# intellij 14 and tomcat 8

## intellij download

https://www.jetbrains.com/idea/

## tomcat 8 download

http://tomcat.apache.org/download-80.cgi

### tomcat 8 startup.sh and shutdown.sh

```cmd

tomcat 설치폴더로 이동 후 bin 폴더에서.

$> ./startup.sh --> 시작
$> ./shutdown.sh --> 종료

```

### tomcat 8 manager access 방법

http://blog.c2b2.co.uk/2014/04/configuring-tomcat-8.html

tomcat 설치 폴더밑에 conf 폴더 안에 tomcat-users.xml 파일에 아래의 내용을 입력한다.

```cmd
Here we will add a new user with the manager-gui role as follows:
  
<role rolename="manager-gui" /> 
<user name="admin" password="admin" roles="manager-gui" />
```

### KendoUI for jsp 다운로드

http://www.kendoui.com

### intellij 설정

1. import project를 이용한 kendoUI for jsp 파일의 pom.xml 파일을 선택한다.

2. menu ->  Run -> Edit Configurations [선택] 한다.

3. Run/Debug Configurations 다이알로그가 나타난다. `+` -> Tomcat Server - >Local [클릭] 한다.

4. Name -> First - Tomcat 7.0 [입력] -> Application Server->Tomcat 7.0 [선택] 한다.

5. Fix -> First:war exploded [선택]->OK [클릭] 한다.

6. File -> Project Structure... -> Project Settings -> Modules -> First [선택]-> Dependencies -> `+` [클릭] -> Library... -> Application Server Libraries -> Tomcat 7.0 [선택] -> Add Selected [클릭] 하여 WAS에 의존적인 라이브러리를 링크한다.


## 참고 사이트

1. Let's ko Project : https://github.com/daejoon/LETS-KO
> 실제 프로젝트 시작전까지 비지니스 로직를 제외한 개발환경 구축 및 간단한 CRUD Sample 



