# KHAN Session Manager

OSS World Challenge 2014 금상수상작

Github : https://github.com/opennaru-dev/khan-session

Sample : https://github.com/opennaru-dev/khan-session-sample

JBoss, Tomcat, WebLogic등 WAS의 세션 클러스터링을 위한 모듈로 오픈소스 LGPL 2.1 라이센스를 따르고 있습니다. 지금까지 WAS 에 저장되던 세션 영역을 제거하고 이를 데이터그리드 영역에서 저장/관리하여 웹 시스템의 가용성과 확장성을 높여 줍니다. 이러한 아키텍처를 이용하여 여러 종류 제품의 WAS 인스턴스 간의 세션공유나 서로 다른 웹 애플리케이션의 간의 세션 공유를 지원합니다. 또한 Clustering 기능이 미비한 Tomcat 인스턴스 간의 세션 클러스터링도 지원합니다.

참고 오픈나루 블로그 : http://opennaru.tistory.com/m/post/62

* KHAN Session Manager 사용 이유는?

    1. 웹 애플리케이션에서 사용하는 HTTP 세션 오브젝트 사이즈가 큰 경우
    2. HTTP 세션 오브젝트로 인하여 WAS 의 메모리 제약이 발생하는 경우 (빈번한 GC와 너무 긴 GC Pause time)
    3. 서로 다른 웹 애플리케이션 세션 공유을 통한 단일 로그인 구현
    4. 웹 애플리케이션에서 중복로그인 방지가 필요한 경우
    5. Enterprise 급의 서비스에 있는 Session 클러스터링 기능이 미약한 Tomcat 인스턴스 간에 세션 클러스터링이 필요한 경우 사용하면 좋음.
    6. 서로 다른 WAS 서버 간 세션 공유가 필요한 경우


* 세션 클러스터링 구성방식

    1. Was간의 구성이 가능.
    2. Was간 + 데이터 그리드 구성이 가능.
    3. 세션 데이터 그리드만 구성이 가능.

* 주요기능

    1. 서로다른 웹 애플리케이션간 세션 공유
    2. 중복 로그인 방지
    3. 세션 타임아웃 제어
    4. 다양한 토폴로지 지원
    5. 세션 생성, 소멸, 중복 로그인 수 모니터링
    6. 세션의 메모리 사이즈 모니터링

* 세션스토리지 종류

    1. Infinispan Library Mode
    2. Infinispan HotRod Mode
    3. Redis

* 사용 방법

    Infinispan Library Mode

    ```json
    <dependency>
    <groupId>com.opennaru.khan</groupId>
    <artifactId>khan-session-infinispan</artifactId>
    <version>1.3.0</version>
    </dependency>
    ```
    Filter Class : com.opennaru.khan.session.filter.InfinispanLibSessionFilter

    Infinispan HotRod Mode

    ```json
    <dependency>
    <groupId>com.opennaru.khan</groupId>
    <artifactId>khan-session-hotrod</artifactId>
    <version>1.3.0</version>
    </dependency>
    ```
    Filter Class : com.opennaru.khan.session.filter.InfinispanHotRodSessionFilter

    Redis Mode

    ```json
    <dependency>
    <groupId>com.opennaru.khan</groupId>
    <artifactId>khan-session-redis</artifactId>
    <version>1.3.0</version>
    </dependency>
    ```
    Filter Class : com.opennaru.khan.session.filter.RedisSessionFilter
