## [ .bash_profile ]

```txt
export GRADLE_HOME=/Users/seokangchun/gradle-1.12
export PYTHONSTARTUP=$HOME/.pythonstartup.py
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home
export CATALINA_HOME=/Users/seokangchun/tomcat-7.0.47
export JAVA_TOOL_OPTIONS=-Dfile.encoding=UTF-8
export PATH=$PATH:$GRADLE_HOME/bin:$JAVA_HOME:/usr/bin:/usr/local/bin
export PATH="/Users/seokangchun/Libraries/vert.x-2.1.5/bin:$PATH"
```
## [ yeoman을 이용해 angular front end 개발을 위한 설정방법 ]

1) nodejs 설치

    1.1) /usr/local/bin/node 에 노드 설치
    1.2) /usr/local/bin/npm 에  npm 설치
    1.3) .bash_profile 의 $PATH에 경로 등록

2) gradle 버전 2014/11/28일 현재 버전 사용중

```cmd
/Users/seokangchun/gradle-2.2.1
```

3) jdk1.8 설치

jdk1.8
```cmd
/Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home
```

jdk1.7
```cmd
/Library/Java/JavaVirtualMachines/jdk1.7.0_10.jdk/Contents/Home
```


4) webstorm 에서 yeoman, bower, grunt 설치
$ sudo npm install -g yo
$ sudo npm install -g bower
$ sudo npm install -g grunt-cli

$ grunt serve 로 웹서버를 띄우명 아래와 같은 경고가 나오면 
"Warning: You need to have Ruby and Compass installed and in your system PATH for this task to work. More info: https://github.com/gruntjs/grunt-contrib-compass Use --force to continue"

$ sudo gem install compass 를 설치해준다.


$ grunt serve 로 웹서버를 띄우명 아래와 같은 경고가 나오면
"Warning: No provider for "framework:jasmine"! (Resolving: framework:jasmine) Use --force to continue."

framework:jasmine 을 설치해준다.
현재 framework:jasmine은 1.2 버전과 2.0 버전이 존재하면 내 mac에는 1.2을 설치함.

$ sudo npm install karma-jasmine --save-dev      > 1.2 버전 설치
$ sudo npm install karma-jasmine@2_0 --save-dev  > 2.0 버전 설치

위의 지금까지 설치한 모듈들은 /usr/local/lib/node_modules 밑에 설치되어 있다

## [ nodeJS Update 방법 ]

node 버전확인

```console
node -v
```

node 업그레이드

```console
sudo npm cache clean -f
sudo npm install -g n
sudo n stable
```
## [ Mac Ports 설치 ]

https://www.macports.org/install.php

MacPorts is an easy to use system for compiling, installing, and managing open source software.

1. Install [Xcode and the Xcode Command Line Tools](http://guide.macports.org/#installing.xcode)
2. Agree to Xcode license in Terminal: sudo xcodebuild -license
3. Install MacPorts for your version of OS X:
    [OS X 10.10 Yosemite](https://distfiles.macports.org/MacPorts/MacPorts-2.3.3-10.10-Yosemite.pkg)

### Selfupdate

lastly, you need to synchronize your installation with the MacPorts rsync server:

```cmd
$> sudo port -v selfupdate
```

## [ brew를 설치 ]

맥용 패키지를 설치하기 위한 홈브루(Homebrew)를 설치하기

OS X용 패키지 관리자인 Homebrew 설치하기
- 영문 사이트:  http://brew.sh/
- 한글 사이트: http://brew.sh/index_ko.html

설치는 간단하다. 터미널에서 다음을 실행한다.
```console
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
```

다만 설치를 위해서는 Xcode용 Command Line Tools가 설치되어 있어야 한다.

주요 명령어
```
brew install formula // 패키지 설치
brew remove formula // 패키지 삭제
brew info formula // 패키지 정보
brew upgrade [formula] // 설치한 패키지의 최신버전을 설치
brew list 또는 brew ls // 설치한 formula 목록
brew update // Homebrew 업데이트
brew doctor // 시스템에 문제가 있는지 확인
brew outdated // 내가 설치한 formula 목록의 이후 버전이 나왔는지 확인
brew cleanup // fomula 의 모든 과거버전을 제거함
```

### $> brew install nginx

설치가이드 블로그 

```
* http://www.letmecompile.com/nginx-php-fpm-%EB%A7%A5%EC%97%90-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/
* http://kevinworthington.com/nginx-for-mac-os-x-mavericks-in-2-minutes/
```

소개자료
```
http://opentutorials.org/module/384/3462
```

설치정보

```console
설치위치 : /usr/local/Cellar/nginx/1.6.1_1
환경파일 : /usr/local/etc/nginx/nginx.conf
Doc폴더  : /usr/local/var/www
```

환경설정 정보 (자세한 사항을 내용확인 요!!!)
```console
환경폴더 : /usr/local/etc/nginx
기본 환경 파일 : nginx.conf
웹사이트별 파일중 PC-Web 사이트 파일 : fms-public.conf
웹사이트 파일 중 Mobile-Web 사이트 파일 : fms-mobile.conf
```


로그인시 자동실행 되게 하려면 다음과 같이 명령어를 실행한다.<br/>

```
cp /usr/local/Cellar/nginx/1.2.7/homebrew.mxcl.nginx.plist /Library/LaunchAgents/
launchctl load -w /Library/LaunchAgents/homebrew.mxcl.nginx.plist
```

nginx 실행 기본명령어

```
서버 시작 nginx
서버 종료 nginx -s stop
서버 재시작 nginx -s reload
```

nginx 프로세스 실행여부를 확인하기

```
프로세스 확인
$> ps -ef | grep nginx

프로세스 갯수가 몇개나 되는가를 확인
$> ps -ef | grep nginx | wc -l
```

## [ Redis 설치 ]

#### brew를 이용한 설치

설치방법

```console
brew install redis
```

설치위치
```console
/usr/local/etc/redis.conf : confiuration 파일
/usr/local/Cellar/redis/2.8.17  : 설치위치
```

서비실행방법

```console
$> redis-server

[3851] 19 Nov 16:07:39.032 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
[3851] 19 Nov 16:07:39.034 * Increased maximum number of open files to 10032 (it was originally set to 2560).
                _._                                                  
           _.-``__ ''-._                                             
      _.-``    `.  `_.  ''-._           Redis 2.8.17 (00000000/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._                                   
 (    '      ,       .-`  | `,    )     Running in stand alone mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 6379
 |    `-._   `._    /     _.-'    |     PID: 3851
  `-._    `-._  `-./  _.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |           http://redis.io        
  `-._    `-._`-.__.-'_.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |                                  
  `-._    `-._`-.__.-'_.-'    _.-'                                   
      `-._    `-.__.-'    _.-'                                       
          `-._        _.-'                                           
              `-.__.-'                                               

[3851] 19 Nov 16:07:39.035 # Server started, Redis version 2.8.17
[3851] 19 Nov 16:07:39.035 * DB loaded from disk: 0.000 seconds
[3851] 19 Nov 16:07:39.035 * The server is now ready to accept connections on port 6379

```

클라이언트접속방법
```console
$> redis-cli

127.0.0.1:6379> ping
PONG
127.0.0.1:6379> set foo bar
OK
127.0.0.1:6379> get foo
"bar"

```

### [ I/O Docs  설치 ]

사이트 
https://github.com/mashery/iodocs

설치위치
```console
/Users/seokangchun/githubFriends/iodocs
```

PC 설치방법
```console
git clone http://github.com/mashery/iodocs.git
cd iodocs
npm install
```

실행방법
```console
$> redis-server : Run a Redis instance
$> npm start (*nix, Mac OSX) 
$> npm run-script startwin (Windows)
```

참고자료

* 블로그
> I/O Docs를 사용한 API 문서화 http://blog.outsider.ne.kr/990

* Swagger
> 모델에 대한 약간의 코드를 작성하고 이를 기반으로 자동으로 API문서를 만들어 주는 방식이고 스프링 MVC등에서 자동으로 뽑아낼 수 있게 플러그 제공
> http://swagger.io/

### [VertX 설치]

설치위치

```console
$> /Users/seokangchun/Libraries/vert.x-2.1.5/bin
```

.bash_profiles 추가

```txt
# VertX Adapting
export PATH="/Users/seokangchun/Libraries/vert.x-2.1.5/bin:$PATH"
```

```console
$> vertx version
Picked up JAVA_TOOL_OPTIONS: -Dfile.encoding=UTF-8
2.1.5 (built 2014-11-13 15:15:56)

```

소스코드

```
/Users/seokangchun/webstormSample/vertx-books
```

vert 실행

```console
$> vertx run app.js[:자바소스]
```

버텍스 모듈 레지스트리에 있는 모든 모듈을 확인
http://modulereg.vertx.io

### [MogoDB 설치]

OS X: HomeBrew 또는 MacPorts로 설치하기

http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/

MongoDB 바이너리 설치

```console
$> brew install mongodb
```

SSL 지원 MongoDB 바이너리 설치

```console
$> brew install mongodb --with-openssl
```

설치위치

```console
/usr/local/Cellar/mongodb/2.6.5  : 설치위치
/usr/local/etc/mongod.conf :  configuration 파일
```

기본 데이터베이스 위치 : /usr/local/var/mongodb

```console
$> cat mongod.conf
systemLog:
  destination: file
  path: /usr/local/var/log/mongodb/mongo.log
  logAppend: true
storage:
  dbPath: /usr/local/var/mongodb
net:
  bindIp: 127.0.0.1
```

mongodb config 를 이용한 실행

```console
$> mongod -f /usr/local/etc/mongod.conf
```

mongodb 데이터베이스 폴더 직접 지정실행

```console
$> mongod --dbpath <path to data directory>
$> mongod --dbpath /usr/local/var/mongodb

2014-11-24T17:29:19.541+0900 [initandlisten] MongoDB starting : pid=8003 port=27017 dbpath=/usr/local/var/mongodb 64-bit host=seokangchun-ui-iMac.local
2014-11-24T17:29:19.542+0900 [initandlisten] db version v2.6.5
2014-11-24T17:29:19.542+0900 [initandlisten] git version: nogitversion
2014-11-24T17:29:19.542+0900 [initandlisten] build info: Darwin miniyosemite.local 14.0.0 Darwin Kernel Version 14.0.0: Fri Sep 19 00:26:44 PDT 2014; root:xnu-2782.1.97~2/RELEASE_X86_64 x86_64 BOOST_LIB_VERSION=1_49
2014-11-24T17:29:19.542+0900 [initandlisten] allocator: tcmalloc
2014-11-24T17:29:19.542+0900 [initandlisten] options: { storage: { dbPath: "/usr/local/var/mongodb" } }
2014-11-24T17:29:19.589+0900 [initandlisten] journal dir=/usr/local/var/mongodb/journal
2014-11-24T17:29:19.589+0900 [initandlisten] recover : no journal files present, no recovery needed
2014-11-24T17:29:19.642+0900 [initandlisten] waiting for connections on port 27017
```

설치이후 console 를 이용한 사용방법

```console
$> mongo

MongoDB shell version: 2.6.5
connecting to: test
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
	http://docs.mongodb.org/
Questions? Try the support group
	http://groups.google.com/group/mongodb-user
    
```

버텍스 모듈 레지스트리에 있는 모든 모듈을 확인
http://modulereg.vertx.io

검색을 통해 github에 있는 MongoDB Persistor 설치
https://github.com/vert-x/mod-mongo-persistor

2014/11/24일 현재 javascript 모듈버전

```javascript
container.deployModule("io.vertx~mod-mongo-persistor~2.1.0", {
  port: 8000,
  host: "localhost",
  bridge: true,
  inbound_permitted: []
});
```

## Mysql 설치

Yosemite 버전 (10.10) 에서는  최신버전인 `Mac OS X ver.10.9(x86, 65-bit), DMG Archive` 가 정상적으로 설치가 되지 않는다. 해당 문제를 해결하기 위해서는 아래와 같은 절차로 설치 해야 합니다.

그리고 우선 [Mysql](http://dev.mysql.com/downloads/mysql/) 다운로드 해야 합니다.

1) 설치 시 사용자화 인스톨를 통해서 `Startup Item`를 Skip 시킨 상태에서 설치한다. (기본설치는 설치오류 발생)

2) .bash_profile 에 아래의 구문을 추가등록 합니다.

```cmd
# MySql 5.6.21
export PATH="/usr/local/mysql/bin:$PATH"
```
3) Mysql를 수동으로 실행합니다.

> System Preferences ( 시스템 환경설정 ) 에서 Mysql를 실행 하고 아래의 Start MySql Server를 클릭

> Terminal 창에서 아래와 같이 실행

```cmd
$> sudo /usr/local/mysql/support-files/mysql.server start
or
$> sudo mysql.server start
```

4) OS부팅시 자동으로 Mysql를 실행하기 위해서는 아래의 참고를 보시고 추가설정 해주시면 됩니다.

5) Mac의 Mysql Server는 WorkStation이 존재하지 않기 때문에 본이지 자주 사용하는  MySql Client Utility를  다운받아 사용하시기 바랍니다. 나의 경우에는 [Toad Mac Edition](https://itunes.apple.com/us/app/toad/id747961939?ls=1&mt=12&ac=ToadMacEdition)를 AppStore에서 다운받아 사용하고 있습니다.

* 참고

> http://coolestguidesontheplanet.com/get-apache-mysql-php-phpmyadmin-working-osx-10-10-yosemite/

## ImageMagick

http://xpush.github.io/ko/doc/installation/index.html

ImageMagick® is a software suite to create, edit, compose, or convert bitmap images
It can read and write images in a variety of formats (over 100) including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PNG, Postscript, SVG, and TIFF. se ImageMagick to resize, flip, mirror, rotate, distort, shear and transform images, adjust image colors, apply various special effects, or draw text, lines, polygons, ellipses and Bézier curves.

1) Mac OS Install
http://www.imagemagick.org/script/binary-releases.php#macosx

```cmd
$> sudo port install ImageMagick
```

2) Image Magic  사용법

파일포맷변경

```cmd
convert image_org.gif  image_out.jpg
[설명] image_org.gif  이미지를 image_out.jpg로 바꾼다.

convert image_org.png  image_out.jpg
[설명] image_org.png  이미지를 image_out.jpg로 바꾼다.
```

추가참고자료
http://www.albumbang.com/board/board_view.jsp?board_name=free&no=57


## XPush 설치

http://xpush.github.io/ko/doc/installation/index.html

XPush를 위해서 사전에 설치되어야 하는 프로그램

1. nodeJs
1. Redis
2. MongoDb
3. ImageMagick


### Install

npm install 설치

```cmd
$> npm install -g xpush
```
Install Locations `/usr/local/lib/node_modules/xpush`

or

github 에서 직접 다운로드 설치 **`(이방식으로 설치)`**

```cmd
git clone https://github.com/xpush/node-xpush.git
cd node-xpush
npm install
```

Install Locations `~/githubProjects/node-xpush`

### Run xpush

세션 서버를 실행하세요. 자세한 옵션은 [여기](http://xpush.github.io/doc/configuration/#run_config)를 확인하세요.

```cmd
cd $HOME/xpush/node_modules/xpush
bin/xpush --port 8000 --config ./config.sample.json --session
```

채널 서버를 실행하세요. 자세한 옵션은 [여기](http://xpush.github.io/doc/configuration/#run_config)를 확인하세요.
```cmd
cd $HOME/xpush/node_modules/xpush
bin/xpush --port 9000 --config ./config.sample.json

상세실행 방법
$> bin/xpush --port 8000 --config ./config.sample.json --channel --host sample.stalk.io
```

config.sample.json 파일 설정

```json
{
  "zookeeper": {"address":"127.0.0.1:2181"},
  "redis": {"address":"127.0.0.1:6379"},
  "mongodb": {"address":"127.0.0.1:27017"},
  "oauth": {},
  "apps" : []
}
```

## ZooKeeper

분산환경에서 서버들간에 상호 조정이 필요한 다양한 서비스를 제공하는 시스템입니다.

첫째, 하나의 서버에만 서비스가 집중되지 않도록, 서비스를 알맞게 분산하여 동시에 처리하게 해줍니다. 
둘째, 하나의 서버에서 처리한 결과를 다른 서버들과도 동기화하여 데이터의 안정성을 보장해 줍니다. 
셋째, 운영(active)서버가 문제가 발생해서 서비스를 제공할 수 없을 경우, 다른 대기 중인 서버를 운영서버로 바꿔서 서비스가 중지 없지 제공되게 해줍니다. 
넷째, 분산 환경을 구성하는 서버들의 환경설정을 통합적으로 관리해줍니다.

    * Zookeeper Download : http://www.apache.org/dyn/closer.cgi/zookeeper/
    * Zookeeper 문서: http://zookeeper.apache.org/doc/current/
    * Zookeeper 설치 및 가이드 : http://zookeeper.apache.org/doc/current/zookeeperStarted.html

* 서버 구동 :

```cmd
$> cd /usr/local/zookeeper/zookeeper-3.4.6
$> bin/zkServer.sh start
```

*  Zookeeper 접속하기 :

```cmd
$> cd /usr/local/zookeeper/zookeeper-3.4.6
$> bin/zkCli.sh -server 127.0.0.1:2181
```

## Mocha

```cmd
$> npm install -g mocha

```

nodejs test 

http://blog.outsider.ne.kr/770
https://gist.github.com/maxogden
