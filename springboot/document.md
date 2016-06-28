# document 설명

### Spring boot

#### [1.3.3 release](http://docs.spring.io/spring-boot/docs/1.3.3.RELEASE/reference/htmlsingle/#boot-documentation)

### Running as a packaged application

```
$ java -jar target/myproject-0.0.1-SNAPSHOT.jar
```

```
$ java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n \
       -jar target/myproject-0.0.1-SNAPSHOT.jar
```

### Maven 과 Gradle Plugin 사용

#### Maven plugin

실행하기
```
$ mvn spring-boot:run
```

Maven 운영시스템의 환경변수를 사용하기 원하면 아래의 명령을 콘솔에서 실행한다.
```
export MAVEN_OPTS=-Xmx1024m -XX:MaxPermSize=128M -Djava.security.egd=file:/dev/./urandom
```

### Gradle plugin

실행하기
```
$ gradle bootRun
```

Gradle 운영시스템의 환경변수를 사용하기 원하면 아래의 명령을 콘솔에서 실행한다.
```
$ export JAVA_OPTS=-Xmx1024m -XX:MaxPermSize=128M -Djava.security.egd=file:/dev/./urandom
```


































