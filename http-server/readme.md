# Http Server List

## Harp Web Server

Harp Server를 실행하려면 먼저 NodeJS가 [설치](http://www.nodejs.org/)되어 있어야 한다. 

사이트 : http://harpjs.com/

설치방법

```cmd
$> sudo npm install -g harp
$> harp init myproject
$> harp server myproject
```

실행방법

기본 9000번 포트로 실행됨

```cmd
$> harp server
```

포트를 지정하면 특정 포트로 실행가능

```cmd
$> harp server --port 8000
```

## Python Http Server 

실행방법

Python 2+

```cmd
$> python -m SimpleHTTPServer 8888
```

Python 3+

```cmd
$> python -m http.server 8888
```

## Jetty Runner

인스톨과 Jetty 배포 없이 당신의 webapp 실행을 위한 빠르고 쉽운 방법을 제공하니 Jetty Runner를 사용하세요.

사이트 : https://wiki.eclipse.org/Jetty/Howto/Using_Jetty_Runner

다운로드 : 
http://repo2.maven.org/maven2/org/mortbay/jetty/jetty-runner/
http://mvnrepository.com/artifact/org.mortbay.jetty/jetty-runner/

실행방법

```cmd
java -jar jetty-runner-9.3.0.M0.jar  --port 8080
```

도움말

```cmd
java -jar jetty-runner.jar --help
```

## Grunt web Server 

사이트 : https://www.npmjs.org/package/grunt-web-server

설치방법

```cmd
npm install grunt-web-server
```

실행방법

gruntfile에 아래의 내용을 작성

```javascript
grunt.initConfig({
  web_server: {
    options: {
      cors: true,
      port: 8000,
      nevercache: true,
      logRequests: true
    },
    foo: 'bar' // For some reason an extra key with a non-object value is necessary
  },
})
```

실행명령

```cmd
grunt web_server
```

## Sencha web server

Sencha Cmd는 Sencha Application를 개발의 토대가 된다. 신규 프로젝트의 시작부터 최소화하고 당신의 제품을 배포한다.
Senchar Cmd는 당신의 Sencha 프로젝트의 라이프사이클 관리기능의 풀셋을 제공한다.

사이트 : http://www.sencha.com/products/extjs/up-and-running/cmd-getting-started

실행방법

기본포트 : 1841

```cmd
$> sencha web start
$> sencha web start --port 8000  (수정포트)
```

```cmd
$> sencha web stop
```


