# NGINX

Nginx 는 러시아의 개발자이자 서버관리자인 이고르 시셰프(Igor Sysoev)에 의해 2002년부터
개발되기 시작했다고 하며.2004년 첫 릴리즈 이래, 2013년 전세계적으로 약 14% 이상의
점유율을 기록하고 있다 한다.현재 Apache에 있어 가장 위협이 되고 있는 존재로 급부상 중이다.

nginx는 웹 서버 소프트웨어로, 가벼움과 높은 성능을 목표로 하고, 적은 수의 쓰레드로도 많은 클라이언트를 처리할수 있다.

아파치와 대표적으로 다른점은 쓰레드 기반이 아닌 이벤트 기반이라는것이다.
여기서 말하는 이벤트 기반이란 Event Driven Architecture(EDA)라고 하는데 아파치같은경우는 하나의 쓰레드에 하나의 클라이언트를 처리한다면 정보를 읽거나 쓴후 가공해서 클라이언트에 전달할때까지 쓰레드의 대기시간이 많고 클라이언트개수만큼 스레드가 생성되어야 한다.

하지만 EDA방식에서는 Event(요청이나 응답결과를 다생성했을때)가 발생되었을 때 
이벤트를 처리하게 해서 더작은 쓰레드로 CPU가 놀지 않고 일하게 할 수 있다 라는것이다.

## Nginx Conf 구조

```javascript
http {

	server {
    	
        location {
        	
        }
        
    }

}
```

* HTTP 블럭 : http 란 웹서버와 웹클라이언트가 서로 정보를 주고 받기 위한 약속(protocol)이다. 즉 요청은 어떻게 해야하고,응답은 어떻게 해야하는지에 대한 규칙을 미리 정해둔 것이다.

* Server 블럭 : server 블럭은 Virtual Host 로 볼 수 있다. Virtual Host 는 한대의 컴퓨터에서 여러 도메인 주소를 예를들어(http://www.naver.com ,http://www.naver2.com) 운영,관리 하려할때 사용하는 기능이다.각각 도메인으로 접속하였을때 둘다 1.222.80.50 이라는 ip를 가르킨다 하자. 그러나 해당하는 호스트는 각각의 도메인에 따라서 
서로다른 페이지를 서비스 하게 할 수있다. 여러 사이트들이 같은 서버에서 돌고있다는 사실을 웹사용자는 눈치채지 못한다.

* location 블럭 :  server 블럭 안에 위치하며 .특정 URL을 처리하는 방법을 정의한다.

## 설치

```cmd
$> brew install nginx
```

설치된 nginx의 관련 파일의 위치를 확인해 보려면 아래의 명령을 실행한다.

```cmd
seokangchun-ui-iMac:~ seokangchun$ brew list nginx
/usr/local/Cellar/nginx/1.6.1_1/bin/nginx
/usr/local/Cellar/nginx/1.6.1_1/homebrew.mxcl.nginx.plist
/usr/local/Cellar/nginx/1.6.1_1/html
/usr/local/Cellar/nginx/1.6.1_1/share/man/man8/nginx.8
```

## 자동시작 (Setup auto start)

```cmd
$> sudo cp -v /usr/local/opt/nginx/*.plist /Library/LaunchDaemons/
$> sudo chown root:wheel /Library/LaunchDaemons/homebrew.mxcl.nginx.plist
```

## 시작/종료/재시작

```cmd
서버시작
$> nginx

서버종료
$> nginx -s stop

서버재시작
$> nginx -s reload
```

## 참고자료

nginx 모듈생성방식, http://helloworld.naver.com/helloworld/textyle/192785