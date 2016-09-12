### 엔티티 매핑

* 객체와 테이블 매핑 : @Entity, @Table
* 기본 키 매핑 : @Id
* 필드와 컬럼 매핑 : @Column
* 연관관계 매핑 : @ManyToOne, @JoinColumn


#### 이름매핑 방법

자바에서는 주로 카멜(Calmel) 표기법을 주로 사용하고 데이터베이스는 관례상 언더스코어(_)를 주로 사용한다.

```java
@Column(name = "role_type")
private RoleType roleType;
```

```xml
<property name="hibernate.ejb.naming_strategy" value="org.hibernate.cfg.ImprovedNamingStrategy" />
```

### 엔티티 매핑 예제

이제부터 아래의 예제 코드를 기준으로 JPA 엔티티 어노테이션을 이해해 봅시다.

```java
@Entity
@Table(name="MEMBER", uniqueConstraints = {@UniqueConstraint( //추가
        name = "ID_NAME_AGE_UNIQUE",
        columnNames = {"ID", "NAME", "AGE"} )})
//@SequenceGenerator(name="MEMBER_ID_GENERATOR",
//        sequenceName="MEMBER_ID",
//        initialValue = 1, allocationSize = 1)
@TableGenerator(name="MEMBER_ID_GENERATOR",
    table="MY_SEQUENCES",
    pkColumnName = "SEQUENCE_NAME",
    pkColumnValue = "MEMBER_ID",
    allocationSize = 1)

// lombok 사용
@Data
public class Member {
    @Id
    @Column(name = "ID")
    @GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "MEMBER_ID_GENERATOR")
    private Long id;

    @Column(name = "NAME", nullable = false, length = 10) //추가 //**
    private String username;

    private Integer age;

    @Enumerated(EnumType.STRING)
    @Column(name = "role_type")
    private RoleType roleType;

    @Temporal(TemporalType.TIMESTAMP)
    private Date createdDate;

    @Temporal(TemporalType.TIMESTAMP)
    private Date lastModifiedDate;

    @Lob
    private String description;

    @Transient
    private String temp;

	}
```

```<property name="hibernate.hbm2ddl.auto" value="create" />``` 코드에 의해 
아래의 테이블, 시퀀스 테이블, 인텍스가 자동생성됨.

```sql
create table member (
    id bigint not null,
    age integer,
    created_date timestamp,
    description clob,
    last_modified_date timestamp,
    role_type varchar(255),
    name varchar(10) not null,
    primary key (id)
)
create table my_sequences (
    sequence_name varchar(255) not null,
    next_val bigint,
    primary key (sequence_name)
)
alter table member 
    add constraint ID_NAME_AGE_UNIQUE  unique (id, name, age)
```


#### 기본키 매핑 전략


##### IDENTITY 전략

IDENTITY 기본키는  SQL Server, DB2, Mysql, PostgreSQL에서 사용한다.
MySql AUTO_INCREMENT 기능을 제공 ID 컬럼을 비워두면 데이터베이스가 순서대로 값을 채워준다.

```sql
create table member (
    id bigint not null auto_increment primary key,
    age integer
    ...
    )
```

```java

@Entity
public class Member {
    @Id
    @Column(name = "ID")
    @GeneratedValue(strategy = GenerationType.INDENTITY)
    private Long id;
}
```

엔티티 영속 상태가 되려면 식별자가 반드시 필요하다. 그런데 IDENTITY 식별자 생성 전략은 엔티티를 데이터베이스에 저아해야 식별자를 구할 수 있으며로  em.persist()를 호출하는 즉시 INSERT SQLㅇㅇ이 데이터베이스에 전달된다. 이전략은 쓰기지연이 동작하지 않는다.


##### SEQUENCE 전략

SEQUENCE 전략은 오라클, PostreSQL, DB2, H2 테이터베이스에 사용할 수 있다.


```SQL
create table member (
    id bigint not null primary key,
    age integer
    ...
    )

// 시퀀스 생성
create sequence member_seq start with 1 increment by 1;
```

```java
@SequenceGenerator(name="member_seq_generator",
        sequenceName="member_seq",
        initialValue = 1, allocationSize = 1)
@Entity
public class Member {
    @Id
    @Column(name = "ID")
    @GeneratedValue(strategy = GenerationType.SEQUENCE,
    				generator  = "member_seq_generator")
    private Long id;
}
```

##### allocationSize 할당

JPA는 시퀀스에 접근하는 횟수를 줄이기 위해 @SequenceGenerator.allocationSize를 사용하다. 간단히 설명하자면 여기에 설정한 값만큼 한 번에 시퀀스 값을 증가시키고 나서 그만큼 메모리에 시쿼스 값을 할당한다. 예를 들면 allocationSize 값을 100이면 시퀀스를 한번에 100증가 시킨 다음에 1~100까지는 메모리에서 식별자를 할당한다.

이 최적화 방법은 시쿼스 값을 선점하므로 여러 JVM이 동시에 동작해도 기본 키 값이 충돌하지 않는 장점이 있다.

##### TABLE 전략

데이터베이스 테이블을 이용해 시쿼스를 흉내내는 전략이다.


```sql
create table my_sequences (
    sequence_name varchar(255) not null,
    next_val bigint,
    primary key (sequence_name)
)
```

```java
@TableGenerator(name="MEMBER_ID_GENERATOR",
    table="MY_SEQUENCES",           // 기본값 "HIBERNATE_SEQUENCES"
    pkColumnName = "SEQUENCE_NAME", // 기본값 "SEQUENCE_NAME"
    valueColumnName = "NEXT_VAL",   // 기본값 "NEXT_VAL"
    pkColumnValue = "MEMBER_ID",
    allocationSize = 1)
@Entity
public class Member {
    @Id
    @Column(name = "ID")
    @GeneratedValue(strategy = GenerationType.TABLE,
    				generator  = "MEMBER_ID_GENERATOR")
    private Long id;
}
```

### 필드와 컬럼 매핑

@Column     컬럼을 매핑
@Enumerated 자바의 enum 타입을 매핑한다.
@Temporal   날짜 타입을 매핑한다.
@Lob        BLOB, CLOB 타입을 매핑한다.
@Transient  특정 필드를 데이터베이스에 매핑하지 않는다.
@Access     JPA가 엔티티에 접근하는 방식을 지정한다.


주요 컬럼매핑 필드 몇가지만 설명해 본다.

#### @Enumerated

자바의 enum 타입을 매핑에 해당된다.

```java
enum RoleType {
	ADMIN, USER
}
```

```java
@Enumerated(EnumType.STRING)
@Column(name = "role_type")
private RoleType roleType;
```

EnumType.ORDINAL는 enum에 정의된 순서대로 ADMIN은 0, USER 1 값이 데이터베이스에 저장된다.
EnumType.STRING은 enum 이름 그대로 ADMIN은 'ADMIN', USER는 'USER'라는 문자로 데이터베이스에 저장된다.

권장은 EnumType.STRING 이다. ORDINAL 의 경우 중간에 열거값을 추가 시 데이터베이스의 값이 밀리게 되는 문제가 발생 하게된다.

#### @Temporal

날짜 타입(java.util.Date, java.util.Calendar)을 매핑할 때 사용한다.

```java
// 날짜
@Temporal (TemporalType.DATE)
private Date date;

// 시간
@Temporal (TemporalType.TIME)
private Date time;

// 날짜와 시간
@Temporal (TemporalType.TIMESTAMP)
private Date timestamp;
```

#### @Lob

데이터베이스 BLOB, CLOB 타입과 매핑한다.

```java

// CLOB 문자열 데이터
@Lob
private String lobSgtring;

// BLOB 바이트 데이터
@Lob
private byte[] lobByte;
```


#### @Transient

이 어노테이션을 사용 시 필드는 매핑하지 않는다. 데이터베이스에 저장하지 않고 조회하지도 않는 어떤 값을 보관하고 싶을 때 사용한다.

```java

@Transient
private String temp;
```


#### @Access

JPA가 엔티티 데이터에 접근하는 방식을 지정한다.

**@Access(AccessType.FIELD)**
> @Id, @Column 등이 필드에 매핑하는 방식

```java
@Entity
@Access(AccessType.FIELD)
public class Member {
	@Id
    private String Id;
    
    @Column
    private String userName;
}
```

**@Access(AccessType.PROPERY)**
> @Id, @Column 등이 프로퍼티에 매핑하는 방식

```java
@Entity
@Access(AccessType.PROPERY)
public class Member {
    private String Id;    
    private String userName;
    
    @Id
    public String getId() {
    	return this.id;
    }
    
    @Column
    public String getUserName() {
    	return this.userName;
    }
}

```










































