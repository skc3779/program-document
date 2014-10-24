## Meteor.js

자바스크립트기반 웹플랫폼

Meteor is an ultra-simple environment for building modern websites. What once took weeks, even with the best tools, now takes hours with Meteor.

사이트 : [링크](https://www.meteor.com/)(https://www.meteor.com/)

클라이언트와 서버의 구분없이 모두 자바스크립트 언어를 사용한다는 점이고, 데이터베이스접근 API 까지도  클라이언트에서 동일하게 자바스크립트로 호출해서 사용가능합니다.
클라이언트 코드에서 DB API 호출만으로 DB의 CRUD가 가능하다.

### Meteor의 특징

공식사이트 (meteor.com) 에 나와 있는 9가지 특징입니다.

1. Pure JavaScript.
2. Live page updates.
3. Clean, powerful data synchronization.
4. Latency compensation.
5. Hot Code Pushes.
6. Sensitive code runs in a privileged environment.
7. Fully self-contained application bundles.
8. Interoperability.
9. Smart Packages.

서버와 클아이언트 모두 순수 자바스크립트 언어를 사용하고 서버든 클라이언트든 둘 다 모두 동일한 API를 사용하며, 데이터베이스까지도
자바스크립트 API를 사용할 수 있다.

참고자료(rkJun's Blog) : http://www.slideshare.net/juntai811/meteor-036-preview

### 정리
Meteor 는 간편하고 빠르게 개발 할 수 있는 환경을 제공해주는 웹개발 플랫폼으로, 자바스크립트 기반이며 서버와 클라이언트가 동일구조 (isomorphic) 로 되어 있고, 이는 DB api 역시 마찬가지로 적용됩니다. Node.js 와 HTML템플릿 엔진, MongoDB 를 내장하고 있고 
기본적으로 reactive programming 방식을 지원하며 hot code push 를 통해 모든 수정/변경이 모든 클라이언트에 자동으로 적용되게
하고 있습니다.  
설치, 생성, 배포가 명령어 한번만으로 간단하게 이루어지므로 개발자 입장에서는 환경설정에 시간을 뺏기지 않고 웹 개발에 전념 할 수 있게 
해주지 만 아직까지는 Preview 0.9.X 이므로 안정성이 확보되었다고는 할 수 없으며 발전방향이 흥미로은 웹개발 플랫폼이 아닌까 한다.

### 참고

nodeqa의 강의 : http://nodeqa.com/nodejs_ref/33

