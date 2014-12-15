# XPush

http://xpush.github.io/ko/service/

2014년 공개SW 개발자대회 대상 수상

웹에서 실시간 데이터 통신을 구현하기 위해 구현된 XPUSH 는 여러분이 직접 설치해서 사용할 수 있는 실시간 메시지 통신 기능과 메시지 저장 및 사용자와 장치를 관리하는 기능 그리고 Mobile Push 기능을 제공하는 서버 플랫폼 입니다.

* 특징

    1. Real-time Web Communication Platform
    2. Works Everywhere
    3. Scalable Web Architecture

* 제공되는 소스

    1. node-xpush : XPUSH 서버 플랫폼 소스
    2.  node-xpush-client : XPUSH 서버 Node.js Client 모듈 소스
    3. lib-xpush-web : XPUSH API Javascript 라이브러리 소스
    4. lib-xpush-java : XPUSH API JAVA 라이브러리 소스
    5. dockerfile : XPUSH 서버 플랫폼 Docker 설치 이미지 파일 (Docker Hub에 등록)
    6. messengerX : XPUSH 기반의 메신저 솔루션 소스 (messengerx)
    7. chrome.messengerX : messengerX 의 Chrome Extension 설치 파일 소스
    8. stalk.io : XPUSH 기반의 웹 체팅 위젯 소스 (stalk.io)
    9. chrome.stalk.io : stalk.io 의 Chrome Extension 설치 파일 소스
    10. xpush.github.io : XPUSH 소개 홈페이지 소스

* 참고자료

    > 오픈소스(OSS)를 활용한 분산아키텍처 구현기술<br/>http://www.slideshare.net/deview/232-deview2013-oss?ref=http://xpush.github.io/ko/blog/
    
## Application Configuration 

### oauth 

http://borisunde.blogspot.kr/2012/04/blog-post.html

1) Facebook (seokangchun_xpush)
```javascript
<script>
  window.fbAsyncInit = function() {
    FB.init({
      appId      : '1508517359428736',
      xfbml      : true,
      version    : 'v2.2'
    });
  };

  (function(d, s, id){
     var js, fjs = d.getElementsByTagName(s)[0];
     if (d.getElementById(id)) {return;}
     js = d.createElement(s); js.id = id;
     js.src = "//connect.facebook.net/en_US/sdk.js";
     fjs.parentNode.insertBefore(js, fjs);
   }(document, 'script', 'facebook-jssdk'));
</script>
```

## Xpush 실행하기

1. xpush는 zookeeper, redis, mongodb를 활용하고 있습니다. 관련 애플리케이션을 실행시켜 두어야 합니다.
2. xpush는 서버는 세션서버와 채널서버로 구성되어 있는데 서비스를 위해서는 모두 실행시켜 두어야 합니다.

* zookeepr 실행

```cmd
$> cd /usr/local/zookeeper/zookeeper-3.4.6
$> bin/zkServer.sh start

```

* redis 실행

```cmd
$> redis-server
```

* mongodb 실행

```cmd
$> mongod --dbpath /usr/local/var/mongodb
```

* 세선서버 실행

```cmd
$> cd $소스폴더$/xpush
$> bin/xpush --port 8000 --config ./config.json --session
```

* 채널서버 실행

```cmd
$> cd $소스폴더$/xpush
$> bin/xpush --port 9000 --config ./config.json 
```

## MessagerX 설치하기

MessagerX를 설치하기 위해서는 [ionic](http://ionicframework.com/), [cordova](http://cordova.apache.org/), [gulp](http://gulpjs.com/)가 먼저 설치되어 있어야 합니다.

```cmd
$> sudo npm install -g cordova ionic gulp
```
