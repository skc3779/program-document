# Java Database Replication Master/Slave 분기방법

Java에서 Master/Slave 분기처리를 하는 4 가지 정도의 방법

## 1. DB Proxy 서버를 이용

[MySQL Proxy](http://dev.mysql.com/doc/mysql-proxy/en/)이나 [MaxScale](https://mariadb.com/products/mariadb-maxscale) 같은 프록시 서버를 사용하는 방법이 있다(MySql 외에도 다른 데이터베이스도 Proxy 서버가 있다). 이런 프록시 서버들은 쿼리를 분석하여 select는 slave로 그 외의 업데이트는 master로 자동으로 보내준다. 문제는 select 더라도 master로 보낼 때 인데, 프록시 서버 자체에 스크립트 언어로 분기 처리를 해줌.
보통은 PHP 같은 동적 언어 계통에서 많이 사용하는 방법.

## Java의 특징 이해

Java의 프레임워크인 Spring Framework을 사용하여 트랜잭션을 관리하면 @Transactional(readOnly=true|false)를 통해 현재 트랜잭션의 readOnly 상태를 설정할 수 있으며, 이 Spring의 트랜잭션 설정은 연쇄적으로 커넥션 객체의 setReadOnly메소드를 호출.

이는 Java 애플리케이션에서 외부 Proxy 서버에 의존하지 않고 애플리케이션 코드를 통해 Master/Slave 분기 처리 가능성을 제공.

```java
@Transactional(readOnly = true)
public User findByIdRead(Integer id) {
    return userRepository.findById(id);
}

@Transactional(readOnly = false)
public User findByIdWrite(Integer id) {
    return userRepository.findById(id);
}
```

## 2. MySQL Replication JDBC Driver 사용하기

[MySQL에는 Replication JDBC 드라이버](http://kwonnam.pe.kr/wiki/database/mysql/jdbc#replication_jdbc_driver)가 존재한다. 이를 이용하면 Connection.setReadOnly(true|false) 호출만으로 Master/Slave 분기 처리

## 3. Spring LazyConnectionDataSourceProxy + AbstractRoutingDataSource

Spring에 있는 [AbstractRoutingDataSource](http://kwonnam.pe.kr/wiki/springframework/abstractroutingdatasource) 는 여러개의 데이터소스를 하나로 묶고 자동으로 분기처리를 해주는 Spring 기본 클래스이다. 많은 사람들이 Master/Slave 분기 처리를 할 때 이것을 사용해 스프링의 현재 트랜잭션 속성을 읽어오는 [TransactionSynchronizationManager](http://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/transaction/support/TransactionSynchronizationManager.html)와 조합하여 분기처리 하려고 시도하는데 이건 실패다. (http://stackoverflow.com/에 보면 이거 왜 안되냐는 질문이 좀 있다)

[ReplicationRoutingDataSource.java](https://github.com/kwon37xi/replication-datasource/blob/master/src/test/java/kr/pe/kwonnam/replicationdatasource/routingdatasource/ReplicationRoutingDataSource.java)에 그 구현이 있는데, 너무도 간단하다.
```java
public class ReplicationRoutingDataSource extends AbstractRoutingDataSource {

    @Override
    protected Object determineCurrentLookupKey() {
        String dataSourceType =
            TransactionSynchronizationManager.isCurrentTransactionReadOnly() ? "read" : "write";
        return dataSourceType;
    }
}
```

왜 안되냐면, TransactionSynchronizationManager 가 비록 @Transactional로 선언된 현재 쓰레드의 트랜잭션 상태를 읽어오는게 가능하더라도 동기화(synchronation)시점과 Connection 객체를 가져오는 시점에 문제가 있기 때문이다.

spring은 @Transactional을 만나면 다음 순서로 일을 처리한다.

```
TransactionManager 선별 -> DataSource에서 Connection 획득 -> Transaction 동기화(Synchronization)
```

여기서 보면 트랜잭션 동기화를 마친 뒤에 [ReplicationRoutingDataSource.java](https://github.com/kwon37xi/replication-datasource/blob/master/src/test/java/kr/pe/kwonnam/replicationdatasource/routingdatasource/ReplicationRoutingDataSource.java)에서 커넥션을 획득해야만 이게 올바로 동작하는데 그 순서가 뒤바뀌어 있기 때문이다.

해결방법 ?

> [ReplicationRoutingDataSource.java](https://github.com/kwon37xi/replication-datasource/blob/master/src/test/java/kr/pe/kwonnam/replicationdatasource/routingdatasource/ReplicationRoutingDataSource.java) 를 [LazyConnectionDataSoruceProxy로](http://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/datasource/LazyConnectionDataSourceProxy.html)로 감사준다.

[LazyConnectionDataSoruceProxy](http://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/datasource/LazyConnectionDataSourceProxy.html) ?

> 실질적인 쿼리 실행 여부와 상관없이 트랜잭션이 걸리면 무조건 Connection 객체를 확보하는 Spring의 단점을 보완하여 트랜잭션 시작시에 Connection Proxy 객체를 리턴하고 실제로 쿼리가 발생할 때 데이터소스에서 getConnection()을 호출하는 역할

작동 순서
```
TransactionManager 선별 -> LazyConnectionDataSourceProxy에서 Connection Proxy 객체 획득 -> Transaction 동기화(Synchronization) -> 실제 쿼리 호출시에 ReplicationRoutingDataSource.getConnection()/determineCurrentLookupKey() 호출
```

실제 설정은 다음과 같고, 좀 더 자세한 것은 [WithRoutingDataSourceConfig.java](https://github.com/kwon37xi/replication-datasource/blob/master/src/test/java/kr/pe/kwonnam/replicationdatasource/config/WithRoutingDataSourceConfig.java)를 확인.

```java
@Bean public DataSource writeDataSource() { return 쓰기 DataSource; }

@Bean public DataSource readDataSource() { return 읽기 DataSource; }

@Bean
public DataSource routingDataSource(DataSource writeDataSource, DataSource readDataSource) {
    ReplicationRoutingDataSource routingDataSource = new ReplicationRoutingDataSource();

    Map<Object, Object> dataSourceMap = new HashMap<Object, Object>();
    dataSourceMap.put("write", writeDataSource);
    dataSourceMap.put("read", readDataSource);
    routingDataSource.setTargetDataSources(dataSourceMap);
    routingDataSource.setDefaultTargetDataSource(writeDataSource);

    return routingDataSource;
}

@Bean
public DataSource dataSource(DataSource routingDataSource) {
    return new LazyConnectionDataSourceProxy(routingDataSource);
}
```

## 4. LazyReplicationConnectionDataSourceProxy ( 비 Spring 인 경우 )

Spring의 [LazyConnectionDataSoruceProxy](http://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/datasource/LazyConnectionDataSourceProxy.html)의 코드를 보면서 이 클래스는 하나의 DataSource만 프록시를 하지만 이를 write/read 두개의 데이터소스를 받아서 프록싱 하도록 수정 전체 코드는 [LazyReplicationConnectionDataSourceProxy.java](https://github.com/kwon37xi/replication-datasource/blob/master/src/main/java/kr/pe/kwonnam/replicationdatasource/LazyReplicationConnectionDataSourceProxy.java)


이 클래스는 기본적으로 Spring의 [LazyConnectionDataSoruceProxy](http://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/datasource/LazyConnectionDataSourceProxy.html) 완전히 동일하게 작동하지만 setReadOnly(true|false)로 지정된 값에 따라 두 데이터소스 중에 적합한 곳으로 분기하여 실제 커넥션을 획득하여 리턴한다.
Spring 프로젝트에서의 설정은 다음과 같은 형태가 된다.

```java
@Bean public DataSource writeDataSource() { return 쓰기 DataSource; }

@Bean public DataSource readDataSource() { return 읽기 DataSource; }

@Bean
public DataSource dataSource(DataSource writeDataSource, DataSource readDataSource) {
    return new LazyReplicationConnectionDataSourceProxy(writeDataSource, readDataSource);
}
```

TransactionManager나 영속 계층 프레임워크는 dataSource 이것만 바라보게 해야한다. writeDataSource, readDatasource는 설정 속에만 존재할 뿐 영속 계층 프레임워크들에게는 그 존재를 모르게 해야한다.

앞서 말했듯이 이 코드는 전혀 Spring에 의존적이지 않으면서 Java의 표준 API를 따르고 있다.
따라서 Spring의 @Transactional과 함께 사용해도 되고, 아니면 그냥 일반 Java 코드에서 아래처럼 Connection.setReadOnly(true|false)를 호출하여 사용.

```java
Connection connection = dataSource.getConnection();
connection.setReadOnly(false);
// 쓰기 DB관련 작업
connection.close();

// 절대 앞서 획득한 커넥션을 재사용하지 말 것

Connection connection = dataSource.getConnection();
connection.setReadOnly(true);
// 읽기 DB관련 작업
connection.close();
```


## 결론 과 주의사항

1. Spring을 사용한다면 3번 LazyConnectionDataSourceProxy + AbstractRoutingDataSource 방식을 권장한다.

2. Spring을 사용하지 않는다면 4번 LazyReplicationConnectionDataSourceProxy.java 소스를 복사하여 사용한다. 이는 한가지 예외를 제외하고는 Spring 과도 잘 작동한다.

3. 4번 LazyReplicationConnectionDataSourceProxy.java는 Spring 4.0.x 이하 + JPA 조합으로 사용할 경우 작동하지 않는다. 이유는 일종의 Spring JPA TransactionManager의 의도적 setReadOnly 회피 때문인데 4.1 부터는 JPA에서도 setReadOnly를 올바르게 호출해줘서 괜찮다.

4. 절대로 한번 읽어들인 커넥션을 readOnly 설정을 바꿔서 재활용하면 안된다. 일단 실제 커넥션을 획득하면 중간에 속성을 바꿔도 다른 커넥션을 새로 맺지 않는다. Spring은 propagation이 REQUIRES_NEW일 경우 비록 동일 DataSource에서 커넥션을 가져오더라도 새로운 커넥션을 맺기 때문에 아무 문제 없이 작동한다. 하지만 propagation이 REQUIRED일 경우에는 새로운 트랜잭션을 생성하지도 않고 새로운 설정을 적용하지도 않으므로 주의해야 한다.

5. 이에 관한 모든 소스와 Spring의 Transaction에서의 예제를 모두 만들어서 올려 두었다. replication-datasource 프로젝트를 보면되며 그 중에서도 AbstractReplicationDataSourceIntegrationTest.java가 3, 4번 모두에 대한 Spring Transaction 테스트이다.

일반적으로 Slave는 여러대로 구성한다. 그렇다면 Slave DB 정보를 여러개 받아서 부하 분산 처리하게 수정하고 싶은 욕구를 느낄 듯 한데, 그러지 말길 권한다.
실제 데이터베이스의 물리적 정보를 애플리케이션에 넣게 되면 여러 서버들 중 한 대가 고장났을 경우 애플리케이션이 그대로 죽어버린다. 동종의 물리적 데이터베이스에 대한 Load Balancing 은 애플리케이션에서 하지 말고 중간에 L4, L7, LVS, Proxy Server 등의 계층을 두어서 중앙 집중 조정하게 해야한다. 여기서는 단지 부하 분산만 할 뿐 조건에 따른 분기 처리는 하지 않는다.
사정상 이런 분기 처리가 힘들면 MySQL의 경우에는 JDBC에서 Load Blanace를 지원하니 알아보도록 한다.
그래도 replication-datasource에 다중 Slave의 부하 분산 기능을 넣고 싶다면 일부 서버가 죽었을 때의 처리에 대해 매우 깊이 고민

## 블로그 출처
* by 권남, http://kwon37xi.egloos.com/5364167
* [MySQL JDBC, Replication JDBC Driver, MySQL JDBC Properties, JDBC Driver 버전 정보 확인](http://kwonnam.pe.kr/wiki/database/mysql/jdbc)