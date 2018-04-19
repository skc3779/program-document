### SpringBoot MySql application.properties 설정

mysql-connector-java 6.xxx.xxx 부터 아래와 같이 URL parameters에 3가지 옵션을 설정한다.

* serverTimezone=UTC 타임존 설정 UTC
* autoReconnect=true 자동 재접속 true
* useSSL=false       SSL 사용 false

```properties
# ===============================
# = DATA SOURCE
# ===============================
spring.datasource.url = jdbc:mysql://110.14.203.48:3306/oauth2_db?serverTimezone=UTC&autoReconnect=true&useSSL=false
spring.datasource.username = root
spring.datasource.password = qwer12#$
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# ===============================
# = JPA / HIBERNATE
# ===============================
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=create-drop
#spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL5Dialect
```