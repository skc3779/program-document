## [ .bash_profile ]

export GRADLE_HOME=/Users/seokangchun/gradle-1.12
export PYTHONSTARTUP=$HOME/.pythonstartup.py
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home
export CATALINA_HOME=/Users/seokangchun/tomcat-7.0.47
export JAVA_TOOL_OPTIONS=-Dfile.encoding=UTF-8

export PATH=$PATH:$GRADLE_HOME/bin:$JAVA_HOME:/usr/bin:/usr/local/bin


## [ yeoman을 이용해 angular front end 개발을 위한 설정방법 ]

1) nodejs 설치
1.1) /usr/local/bin/node 에 노드 설치
1.2) /usr/local/bin/npm 에  npm 설치
1.3) .bash_profile 의 $PATH에 경로 등록

2) gradle 버전 2014/05/15일 현재 1.12버전 사용중
2.1) 설치위치 /Users/seokangchun/gradle-1.12

3) jdk1.8 설치
3.1) 설치위치 /Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home

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

## [ brew를 설치 ]

맥용 패키지를 설치하기 위한 홈브루(Homebrew)를 설치하기

OS X용 패키지 관리자인 Homebrew 설치하기
- 영문 사이트:  http://brew.sh/
- 한글 사이트: http://brew.sh/index_ko.html

설치는 간단하다. 터미널에서 다음을 실행한다.
```
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

```
설치위치 : /usr/local/Cellar/nginx/1.6.1_1
환경파일 : /usr/local/etc/nginx/nginx.conf
Doc폴더  : /usr/local/var/www
```

환경설정 정보 (자세한 사항을 내용확인 요!!!)
```
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

