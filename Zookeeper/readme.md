## ZooKeeper

분산환경에서 서버들간에 상호 조정이 필요한 다양한 서비스를 제공하는 시스템입니다.

    첫째, 하나의 서버에만 서비스가 집중되지 않도록, 서비스를 알맞게 분산하여 동시에 처리하게 해줍니다. 
    둘째, 하나의 서버에서 처리한 결과를 다른 서버들과도 동기화하여 데이터의 안정성을 보장해 줍니다. 
    셋째, 운영(active)서버가 문제가 발생해서 서비스를 제공할 수 없을 경우, 다른 대기 중인 서버를 운영서버로 바꿔서 서비스가 중지 없지 제공되게 해줍니다. 
    넷째, 분산 환경을 구성하는 서버들의 환경설정을 통합적으로 관리해줍니다.

* Zookeeper Download : http://www.apache.org/dyn/closer.cgi/zookeeper/
* Zookeeper 문서: http://zookeeper.apache.org/doc/current/
* Zookeeper 설치 및 가이드 : http://zookeeper.apache.org/doc/current/zookeeperStarted.html

### 참고블로그

* http://blog.daum.net/caisa/104

### 다운로드

http://www.apache.org/dyn/closer.cgi/zookeeper/

### 설치

```cmd
$> tar zxvf zookeeper-3.4.6.tar.gz

$> cp -Rf zookeeper-3.4.6 /usr/local/zookeeper

$> cd /usr/local/zookeeper
```

### 설치위치

```cmd
/usr/local/zookeeper/zookeeper-3.4.6
```

### zoo.cfg 생성

```cmd
cd /usr/local/zookeeper/zookeeper-3.4.6
cd ./conf
cp zoo_sample.cfg zoo.cfg
```

```cmd
seokangchun-ui-iMac:conf seokangchun$ cat zoo.cfg
# The number of milliseconds of each tick
tickTime=2000
# The number of ticks that the initial 
# synchronization phase can take
initLimit=10
# The number of ticks that can pass between 
# sending a request and getting an acknowledgement
syncLimit=5
# the directory where the snapshot is stored.
# do not use /tmp for storage, /tmp here is just 
# example sakes.
dataDir=/tmp/zookeeper
# the port at which the clients will connect
clientPort=2181
# the maximum number of client connections.
# increase this if you need to handle more clients
#maxClientCnxns=60
#
# Be sure to read the maintenance section of the 
# administrator guide before turning on autopurge.
#
# http://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_maintenance
#
# The number of snapshots to retain in dataDir
#autopurge.snapRetainCount=3
# Purge task interval in hours
# Set to "0" to disable auto purge feature
#autopurge.purgeInterval=1
```

단일 서버 설정은 완료

### 서버 구동 : (start 시작, stop 종료)

```cmd
$> cd /usr/local/zookeeper/zookeeper-3.4.6
$> bin/zkServer.sh start

JMX enabled by default
Using config: /usr/local/zookeeper/zookeeper-3.4.6/bin/../conf/zoo.cfg
```

### Zookeeper 접속하기 :

```cmd
$> cd /usr/local/zookeeper/zookeeper-3.4.6
$> bin/zkCli.sh -server 127.0.0.1:2181
```

help  명령어 사용해 보기

```cmd
WatchedEvent state:SyncConnected type:None path:null
[zk: 127.0.0.1:2181(CONNECTED) 0] help
ZooKeeper -server host:port cmd args
	stat path [watch]
	set path data [version]
	ls path [watch]
	delquota [-n|-b] path
	ls2 path [watch]
	setAcl path acl
	setquota -n|-b val path
	history 
	redo cmdno
	printwatches on|off
	delete path [version]
	sync path
	listquota path
	rmr path
	get path [watch]
	create [-s] [-e] path data acl
	addauth scheme auth
	quit 
	getAcl path
	close 
	connect host:port
```
