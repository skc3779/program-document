# Tomcat

## Tomcat Native Library 설치하기

Linux 나 Mac 에서는 tc-library를 설치하기 위해서는 [APR(Apache Portable Runtime)](http://apr.apache.org/download.cgi)이 필요합니다.

APR Connector의 특징

* Non-blocking I/O for Keep-Alive requests (between requests)
* Uses OpenSSL for TLS/SSL capabilities (if supported by linked APR library)
* FIPS 140-2 support for TLS/SSL (if supported by linked OpenSSL library)

Windows의 경우는 매우 간단하게 설치 할 수 있습니다.

1. 아래의 경로에서 다운로드 binary native library 내려받아서 설치한다.
http://archive.apache.org/dist/tomcat/tomcat-connectors/native/1.1.xxx/binaries/win64/x64/

2. 압축을 해제 하고 %TOMCAT_HOME%/bin 밑에 tcnative-1-ip4.dll를 복사한다.

3. Tomcat를 다시 시작합니다.


Mac의 경우는 brew를 이용해 설치할 수 있습니다. 아래 스크립트를 참고바랍니다.

```
$> brew search apr --> search 를 이용해 apr를 확인한다.
$> brew install apr --> 설치시작함.

설치위치는
/usr/local/opt 밑에존재함.

```
APR를 설치하였다면 이제 tomcat-navtive.tar.gz를 설치해 보자. tomcat-navtive는 tomcat의 bin 폴더밑에 *.gz파일로 존재한다.

먼저 압축을 해제하고, native 폴더로 이동해서 인스톨한다.

```
$> cd $TOMCAT/bin
$> tar xvf tomcat-navtive.tar.gz
$> cd *.src
$> cd jni/native

$> ./configure --prefix=/Users/seokangchun/developers/apache-tomcat-7.0.59 --with-apr=/usr/local/opt/apr/bin/apr-1-config --with-java-home=/Library/Java/JavaVirtualMachines/jdk1.8.0_25.jdk/Contents/Home

$> make
$> make install
```

Tomcat의 catalina.sh 폴더로 이동해서 LD_LIBRARY_PATH 환경변수를 설정한다.

```
$> cd $TOMCAT/bin
$> touch setenv.sh --> setenv.sh 파일을 생성한다.
$> chmod 755 setenv.sh

LINUX의 경우 환경변수 추가
# EXTATION From Kangchun.Seo 2016/05/05
export LD_LIBRARY_PATH=/Users/seokangchun/developers/apache-tomcat-7.0.59/lib

MAC OS의 경우 환경변수 추가
# EXTATION From Kangchun.Seo 2016/05/05
CATALINA_OPTS="$CATALINA_OPTS -Djava.library.path=/Users/seokangchun/developers/apache-tomcat-7.0.59/lib"

```

아래와 같은 에러 발생시 해결방법

SEVERE: Failed to initialize the SSLEngine. org.apache.tomcat.jni.Error: 70023: This function has not been implemented on this platform

```xml
$> cd $TOMCAT/conf/server.xml

server.xml 파일에 SSLEngine="on"으로 되어 있는 경우 에러 off로 변경해준다.
<!--APR library loader. Documentation at /docs/apr.html -->
<Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="off" />
```
