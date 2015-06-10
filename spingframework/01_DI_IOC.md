# DI & IOC

## IOC

* IOC (INVERSION OF CONTROL) 제어의 역전, 역제어

    제어의 역전이란 간단하게 말해보면 프로그램의 제어 흐름구조가 바뀌었다는 것이다.
    일반적으로 main()같은 프로그램이 시작되는 지점에서 다음에 사용할 오브젝트(객체)를 결정, 또는 생성하고 만들어진 오브젝트 내의 메소드를 호출하는 작업을 반복하게 된다. 이런 구조에서 각 오브젝트는 프로그램을 흐름을 결정하거나 사용 할 오프벡트를 구성하는 작업에 능동적으로 참여하게 된다. 이는 다시말해 사용하는 쪽에서 모든 종류의 작업을 제어하는 구조로 이루어 진다는 것이다.

    그러나 IoC는 제어 흐름의 개념을 거꾸로 뒤집는다. 오브젝트 자신이 사용할 오브젝트를 스스로 생성하거나 선택하지 않는다. 그리고 자신이 어떻게 만들어 지고 어디서 사용되는지 알 수 없다. 모든 제어 권한을 자신이 아닌 다른 대상에게 위임하는 것이다. 프로그램의 시작을 담당하는 main() 같은 엔트리 포인트를 제외하면 모든 오브젝트는 이런 방식으로 위임받은 제어 권한을 갖는 특별한 오브젝트에 의해 결정되고 만들어 지는 것이다.

* IoC를 요약해 보면

    1. 작업을 수행하는 쪽에서 Object를 생성하는 제어 흐름의 개념을 반대로 뒤집는다.
    2. IoC에서는 Object가 자신의 사용할 Object를 생성하거나 선택하지 않는다.
    3. Object는 자신이 어떻게 생성되고 어떻게 사용되는지 알 수 없다.
    4. 모든 Object는 제어 권한을 위임받는 특별한 Object에 의해서 만들어 지고 사용된다.


### IoC 구현방법

* **DL (Dependency Lookup)  - 의존성 검색**

	저장소에 저장되어 있는 빈(Bean)에 접근하기 위하여 개발자들이 컨테이너에서 제공하는 API 를 이용하여사용하고자 하는 빈(Bean) 을 Lookup 하는 것

* **DI (Dependency Injection) - 의존성 주입**
        
	각 계층 사이, 각 클래스 사이에 필요로 하는 의존 관계를 컨테이너가 자동으로 연결해주는것 각 클래스 사이의 의존 관계를 빈 설정(Bean Definition) 정보를 바탕으로 컨테이너가 자동으로 연결해 주는 것 DL 사용 시 컨테이너 종속성이 증가하여, 이를 줄이기 위하여 DI를 사용

	- **Setter Injection**

        1. 인자가 없는 생성자나 인자가 없는 static factory 메소드가 bean을 인스턴스화 하기 위하여 호출된 후 bean의 setter 메소드를 호출하여 실체화하는 방법    
        2. 객체를 생성 후 의존성 삽입 방식이기에 구현시에 좀더 유연하게 사용할 수 있다.
        3. 세터를 통하여 필요한 값이 할당되기 전까지 객체를 사용할 수 없다.
        4. Spring 프레임워크의 빈 설정 파일에서 property 사용

	- **Constructor Injection**

        1. 생성자를 이용하여 클래스 사이의 의존 관계를 연결
        2. 생성자에 파라미터를 지정함으로 생성하고자하는 객체가 필요로 하는 것을 명확하게 알 수 있다.
        3. Setter메소드를 제공하지 않음으로 간단하게 필드를 불변 값으로 지정이 가능하다.
        4. 생성자의 파라미터가 많을 경우 코드가 복잡해 보일 수 있다.
        5. 조립기 입장에서는 생성의 순서를 지켜야 하기에 상당히 불편하다.
        6. Spring 프레임워크의 빈 설정 파일에서 constructor-arg 사용

	- **Method Injection**
	
 		Singleton 인스턴스와 Non Singleton 인스턴스의 의존 관계를 연결 시킬 필요가 있을 경우 사용하지만, 많이 사용하지는 않는다.

* **Setter Injection 예제**

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <property name="beanOne"><ref bean="anotherExampleBean"/></property>
    <!-- setter injection using the neater 'ref' attribute -->
    <property name="beanTwo" ref="yetAnotherBean"/>
    <property name="integerProperty" value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

```java
public class ExampleBean {
    private AnotherBean beanOne;
    private YetAnotherBean beanTwo;
    private int i;

    public void setBeanOne(AnotherBean beanOne)
        this.beanOne = beanOne;

    public void setBeanTwo(YetAnotherBean beanTwo)
        this.beanTwo = beanTwo;

    public void setIntegerProperty(int i)
        this.i = i;
}
```

* **Constructor Injection의 예제**

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <constructor-arg><ref bean="anotherExampleBean"/></constructor-arg>
    <constructor-arg ref="yetAnotherBean"/>    
           // <constructor-arg><ref bean="yetAnotherBean"/></constructor-arg> 위와 동일
    <constructor-arg type="int" value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

```java
public class ExampleBean {
    private AnotherBean beanOne;
    private YetAnotherBean beanTwo;
    private int i;
    
    public ExampleBean(
        AnotherBean anotherBean, YetAnotherBean yetAnotherBean, int i) {
        this.beanOne = anotherBean;
        this.beanTwo = yetAnotherBean;
        this.i = i;
    }
}
```

### IoC 용어 정리

**bean** - 스프링에서 제어권을 가지고 직접 만들고 관계를 부여하는 오브젝트
자바빈, EJB의 빈과 비슷한 오브젝트 단위의 애플리케이션 컴포넌트를 말한다. 하지만 스프링을 사용하는 애플리케이션에서 만들어지는 모든 오브젝트가 빈은아니다. 스프링의 빈은 스프링 컨테이너가 생성과 관계설정, 사용등을 제어해주는 오브젝트를 가리킨다.

**bean factory** - 스프링의 IoC를 담당하는 핵심 컨테이너
빈을 등록/생성/조회/반환/관리한다. 보통은 bean factory 를 바로 사용하지 않고 이를 확장한 application context 를 이용한다. BeanFactory 는 bean factory 가 구현하는 interface 이다. (getBean()등의 메소드가 정의되어 있음)
 
**application context** - bean factory를 확장한 IoC 컨테이너
빈의 등록/생성/조회/반환/관리의 기능은 bean factory 와 같지만, 여기에 spring의 각종 부가 서비스를 추가로 제공한다. ApplicationContext는 application context가 구현해야 하는 interface이여, BeanFactory 를 상속한다.
 
**configuration metadata** (설정정보/설정 메타정보)
application context 혹은 bean factory 가 IoC를 적용하기 위해 사용하는 메타정보
스프링의 설정정보는 컨테이너에 어떤 기능을 세팅하거나 조정하는 경우에도 사용하지만 주로 bean 을 생성/구성하는 용도로 사용된다.
 
**container (IoC container)**
IoC 방식으로 bean을 관리한다는 의미에서 bean factory 나 application context 를 가리킨다. 
(spring container = application context) application context는 그 자체로 ApplicationContext 인터페이스를 구현한 오브젝트를 가리키기도 하는데, 하나의 애플리케이션에 보통 여러개의 ApplicationContext Object가 만들어진다. 이를 통칭해서 strping container라고 부를 수 있다.
간단하게, 객체를 관리하는 컨테이너이다, 컨테이너에 객체를 담아 두고, 필요할 때에 컨테이너로부터 객체를 가져와 사용할 수 있도록 하고 있다.
 
**spring framework** - IoC container, application context 를 포함해서 spring이 제공하는 모든 기능을 통칭한다.


## 클래스 호출방식

**일반적인 클래스 호출**
클래스내에 선언과 구현이 한몸이기때문에 다양한 형태로 변화가 불가능하다.

```java
public class ConnectionMaker {
	public Connection makeNewConnection() throws ClassNotFoundException, SqlException {
    	Connection c = //  로직
       return c;
    }
}
public class UserDao {
	private ConnectionMaker connectionMaker;
    public UserDao() {
    	connectionMaker = new ConnectinMaker();
    }
    
    public void add(User user) throws ClassNotFoundException, SqlException {
    	Connection c = connectionMaker.makeNewConnection();
    }
    
    public void get(User user) throws ClassNotFoundException, SqlException {
    	Connection c = connectionMaker.makeNewConnection();
    }
    
}
```

**인터페이스를 이용한 클래스 호출**
클래스를 인터페이스와 구현클래스로 분리를 하였다.구현클래스 교체가 용이하여 다양한 형태로 변화가 가능하지만 구현클래스 교체시 호출 클래스의 소스를 수정해야한다.

```java
public interface ConnectionMaker {
	public Connection makeNewConnection() throws ClassNotFoundException, SqlException
}
public class DConnectionMaker implements ConnectionMaker {
	public Connection makeNewConnection() throws ClassNotFoundException, SqlException {
    	Connection c = //  로직
       return c;
    }
}
public class UserDao {
	private ConnectionMaker connectionMaker;
    
    public UserDao() {
    	connectionMaker = new DConnectinMaker();
    }
    
    public void add(User user) throws ClassNotFoundException, SqlException {
    	Connection c = connectionMaker.makeNewConnection();
    }
    
    public void get(User user) throws ClassNotFoundException, SqlException {
    	Connection c = connectionMaker.makeNewConnection();
    }
    
}
```

**팩토리패턴을 이용한 클래스 호춟방식**
팩토리방식은 팩토리가 구현클래스를 생성하므로 클래스는 팩토리를 호출하는 코드로 충분하다. 구현클래스 변경시 호출클래스에는 영향을 미치지 않고, 팩토리만 수정하면 된다. 하지만 클래스에 팩토리를 호출하는 소스가 들어가야한다. 그것 자체가 팩토리에 의존함을 의미한다
```java
public interface ConnectionMaker {
	public Connection makeNewConnection() throws ClassNotFoundException, SqlException
}
public class DConnectionMaker implements ConnectionMaker {
	public Connection makeNewConnection() throws ClassNotFoundException, SqlException {
    	Connection c = //  로직
       return c;
    }
}
public class DaoFactory {
	publics UserDao userDao() {
    	return new UserDao()
    }
    
    public AccountDao accountDao() {
    	return new AccountDao(connectionMaker());
    }
    
    public MessageDao messageDao() {
    	return new MessageDao(connectionMaker());
    }
    
    public ConnectionMaker connectionMaker() {
    	return new DConnectionMaker();
    }
}
```
**IoC를 이용한 클래스 호출방식**
팩토리패턴의 장점을 더하여 어떠한것에도 의존하지 않는 형태로 구성이 가능하다. 실행 시점에 클래스간의 관계가 형성이 된다. 
즉 의존성이 삽입된다는 의미로 IoC를 DI(Dependency Injection) 라는 표현으로 사용한다.

```java

@Configuration
public class DaoFactory {
	@Bean
    public UserDao userDao() {
    	return new UserDao(connectionMaker());
    }
    @Bean
    public ConnectionMaker connectionMaker() {
    	return new DConnectionMaker();
    }
}

@Configuration : 애플리케이션 컨텍스트 또는 빈 팩토리가 사용할 설정정보라는 표시임.
@Bean : 오브젝트 생성을 담당하는 Ioc용 메소드라는 표시임.
```

애플리케이션 컨텍스트를 적용한 UserDaoTest
```java
public class UserDaoTest {
	public stati void main(tring[] args) throws ClassNotFoundException, SQLException {
		ApplicationContext context = new AnnotationConfigApplicationContext(DaoFactory.class);
        UserDao dao = context.getBean("userDao", UserDao.class);
        // 이후로직 처리
        
    }
}
```