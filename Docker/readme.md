# Docker

Docker는 2013년 3월 Docker, Inc(구 dotCloud)에서 출시한 오픈 소스 컨테이너 프로젝트이며, 2014년 현재 나온 지 2년도 채 되지 않았지만 급 성장하는 프로젝트 입니다.

Docker는 가상서버 환경에 각종 소프트웨어를 설치하고 설정할 필요 없이 이미지로 생성하여 한번에 배포 할 수 있는 Immutable Infrastructure을 구현한 프로젝트 입니다.

Immutable Infrastructure는 호스트 OS와 서비스 운영 환경(서버 프로그램, 소스 코드, 컴파일된 바이너리)을 분리하고, 한 번 설정한 운영 환경은 변경하지 않는다(Immutable)는 개념입니다. 즉 서비스 운영 환경을 이미지로 생성한 뒤 서버에 배포하여 실행합니다. 이때 서비스가 업데이트되면 운영 환경 자체를 변경하지 않고, 이미지를 새로 생성하여 배포하는 것입니다. 클라우드 플랫폼에서 서버를 쓰고 버리는 것처럼, Immutable Infrastructure도 서비스 운영 환경 이미지를 한번 쓰고 버릴 수 있는 개념입니다.

Immutable Infrastructure는 장점

* 편리한 관리: 서비스 운영 환경을 이미지로 생성했기 때문에 이미지 자체만으로 관리가 가능하며, 버전관리 시스템 활용가능
* 확장: 이미지 하나로 구성되어 있어 동일한 환경의 서버들을 쉽게 생성 할 수 있음. 클라우드 플랫폼과 연계하면 손쉬운 서비스 확장 가능.
* 테스트: 개발PC나 테스트서버에서 이미지를 실행하며 운영환경과 동일한 환경으로 테스트 가능.
* 가볍다: 운영체제와 서비스 운영 환경의 분리가 가능해 Lightweight, Portable 환경을 제공.

## deview 2014

* 김대권의 Docker 발표 [자료](http://www.slideshare.net/deview/1a6docker), [영상](http://serviceapi.rmcnmv.naver.com/flash/outKeyPlayer.nhn?vid=13782279B938A2B6E2B520B7933A170CBA14&outKey=V1221353c4898d58e2284021dc9e8493b2099086b9a0bc09a3a92021dc9e8493b2099&controlBarMovable=true&jsCallable=true)
* 김대권의 [블로그](http://nacyot.com/)

## 책들
* 가장빨리만나는 Docker 책 (pyrasis.com) : [Book](http://pyrasis.com/private/2014/11/30/publish-docker-for-the-really-impatient-book)

## 리눅스 컨테이너

chroot : 파일시스템에서 루트 디렉터리(/)를 변경하는 명령, chroot로 특정 디렉터리를 루트 디렉터리로 설정하면 chroot jail(감옥)이라는 환경을 제공하고 chroot jail에서는 바깥의 파일과 디렉터리에 접근 할 수 없음 그러나,  완벽한 가상 환경이 아니기 때문에 각종 제갸이 많이 존재함.

LXC(Linux Container) : 컴퓨터를 통째로 가상화하여 OS를 실행하는 것이 아닌 리눅스 커널 레벨에서 제공하는 일종의 격리(Isolate)된 가상 공간, LXC는 리눅스 커널의 cgroups와 namespaces기능을 활용하여 가상공간을 제공 그러나, 격리된 공간만 제공할 뿐 개발 및 서버 운영에 필요한 부가 기능이 부족

Docker가 처음 개발될 당시에는 LXC를 기반으로 구현을 하였지만 버전 0.9부터는 LXC를 대신하는 libcontainer를 개발하여 사용



