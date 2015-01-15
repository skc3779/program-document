# Yeoman

Yeoman은 당신의 애플리케이션을 제너레이터 해줍니다.

## Yeoman 개발을 위한 프로그램

bower의 경우에는 GIT을 이용해 라이브러리를 설치해 주므로 사전에 [GIT](http://www.git-scm.com/)을 OS에 설치해 두어야 한다.
Bower depends on Node.js and npm. Also make sure that git is installed as some bower packages require it to be fetched and installed.
https://github.com/bower/bower

```cmd
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

```

## generator-angular 설치

```cmd
$> npm install -g generator-angular
```

## 애플리케이션 활용

### 프로젝트 생성
```cmd
$> yo angular [애플리케이션 이름]
```

### controller and view 생성

```cmd
$> yo angular:route [board]

Produces app/scripts/controllers/myroute.js:
angular.module('myMod').controller('MyrouteCtrl', function ($scope) {
  // ...
});

Produces app/views/myroute.html:
<p>This is the myroute view</p>

```



