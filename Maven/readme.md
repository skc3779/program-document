## maven


### maven 사용법 베이직

http://javacan.tistory.com/entry/MavenBasic

Maven 라이프사이클(Lifecycle)과 플러그인 실행

본 글의 서두에 Maven은 프로젝트의 라이프사이클 기반 프레임워크를 제공한다고 했다. 앞서 프로젝트를 생성한 뒤 컴파일하고(mvn compile), 테스트 하고(mvn test), 패키징 하는(mvn package) 과정을 정해진 명령어를 이용해서 실행했는데, 이때 compile, test, package는 모두 빌드 라이프사이클에 속하는 단계이다.

Maven은 clean, build (default), site의 세 가지 라이프사이클을 제공하고 있다. 각 라이프사이클은 순서를 갖는 단계(phase)로 구성된다. 또한, 각 단계별로 기본적으로 실행되는 플러그인(plugin) 골(goal)이 정의되어 있어서 각 단계마다 알맞은 작업이 실행된다. 아래 표는 디폴트 라이프사이클을 구성하고 있는 주요 실행 단계를 순서대로 정리한 것이다.

* [표] 디폴트 라이프사이클의 주요 단계(phase)

단계	설명 	단계에 묶인 플러그인 실행
generate-sources	컴파일 과정에 포함될 소스를 생성한다. 예를 들어 DB 테이블과 매핑되는 자바 코드를 생성해주는 작업이 이 단계에서 실행된다.	
process-sources	필터와 같은 작업을 소스 코드에 처리한다.	 
generate-resources	패키지에 포함될 자원을 생성한다. 	 
process-resources	필터와 같은 작업을 자원 파일에 처리하고, 자원 파일을 클래스 출력 디렉토리에 복사한다.	resources:resources 
compile	소스 코드를 컴파일해서 클래스 출력 폴더에 클래스를 생성한다.	compiler:compile
generate-test-sources	테스트 소스 코드를 생성한다. 예를 들어 특정 클래스에서 자동으로 테스트 케이스를 만드는 작업이 이 단계에서 실행된다.	
process-test-sources	필터와 같은 작업을 테스트 소스 코드에 처리한다.	resources:testResources 
generate-test-resources	테스트를 위한 자원 파일을 생성한다. 	 
process-test-resources	필터와 같은 작업을 테스트 자원 파일에 처리하고, 테스트 자원 파일을 테스트 클래스 출력 폴더에 복사한다.	 
test-compile	테스트 소스 코드를 컴파일해서 테스트 클래스 추력 폴더에 클래스를 생성한다.	compiler:testCompile
test	테스트를 실행한다.	surefire:test
package	컴파일 된 코드와 자원 파일들을 jar, war와 같은 배포 형식으로 패키징한다.	패키징에 따라 다름
jar - jar:jar
war - war:war
pom - site:attach-descriptor
ejb - ejb:ejb
install	로컬 리포지토리에 패키지를 복사한다.	install:install
deploy	생성된 패키지 파일을 원격 리포지토리에 등록하여, 다른 프로젝트에서 사용할 수 있도록 한다.	deploy:deploy

* 라이프사이클의 특정 단계를 실행하려면 다음과 같이 mvn [단계이름] 명령어를 실행하면 된다.
```
mvn test
mvn deploy
```

* 디펜던시 트리로 보여주기.
    mvn dependency:tree

* stereotype annotation
    http://therealdanvega.com/blog/2017/03/27/spring-stereotype-annotations

