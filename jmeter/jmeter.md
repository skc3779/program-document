# JMeter 사용방법

### JMeter Plugin설정

	http://jmeter-plugins.org/wiki/PluginInstall/
    
JMETER-INSTALL-DIR/bin/jmeter.properties 폴더에서 아래의 프로퍼티 값을 true 설정한다.

```java
	#jmeter.save.saveservice.thread_counts=false
```

```java
	jmeter.save.saveservice.thread_counts=true
```

### 분산테스트 환경 설정하기

참고 : http://odysseymoon.tistory.com/51

#### jmeter-controller : 설정하기

jmeter.properties

```

# Remote Hosts - comma delimited
remote_hosts={Server1_DNS}:1099,{Server2_DNS}:1099,{Server3_DNS}:1099

#### Parameter that controls the RMI port used by the RemoteSampleListenerImpl
# Default value is 0 which means port is randomly assigned
client.rmi.localport=40001

```

#### jmeter-server : 설정하기

```

# RMI port to be used by the server (must start rmiregistry with same port)
server_port=1099

# To use a specific port for the JMeter server engine, define
# the following property before starting the server:
server.rmi.localport=40000

```

#### 공통설치

다음은 DNS Cache를 사용하지 않도록 {apache_jmeter_dir}\bin
디렉토리의  system.properties 파일에 다음 항목을 추가

jmeter (Linux), jmeter.bat (Windows) 파일의 JVM 옵션 수정

```
#Disable DNS Cache
networkaddress.cache.ttl=0
sun.net.inetaddr.ttl=0
```
(SUN JDK가 아니면 sun.net.inetaddr.ttl=0 은 제외합니다.


```
HEAP=-Xms512m -Xmx1024m
```