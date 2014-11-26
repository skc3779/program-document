# D3 Guide

D3.js는 데이터 기반으로 문서수정을 하기 위한 Javascript 라이브러리다. D3는 HTML, SVG 그리고 CSS를 사용해 데이터에 활기를 부어준다. 웹표준에서 D3's의 강점은 강력한 시각화 구성요소를 결합한 자체 프레임워크에 자신을 얽매이지 않아도 모던 브라우저의 호환성을 보장하는 것이다. 그리고 DOM 조작의 데이터 관점에서 접근한다.

## Browser / Platform Support

D3 "모던" 브라우저를 지원한다. 일반적으로 IE8과 이전을 제외한다. D3는  Firefox, Chrome, Safari, Opera, IE9+, Android and iOS를 대상으로 테스트 되었다. 

D3는 또한 Node.js에서 실행된다. 사용법은 `npm install d3`로 설치, 그리고 `require("d3")`로 로드한다. Node는 제한된 DOM지원을 [JSDOM](https://github.com/tmpvar/jsdom)으로 제공한다.

### Installing

Download the lastest

https://github.com/mbostock/d3/releases

또는 이 조각을 복사해서 직접링크 하자.

```javascript
<script src="http://d3js.org/d3.v3.min.js" charset="utf-8"></script>
```

### Using

로컬 웹서버를 활용해라.

Python 2+ 

```cmd
python -m SimpleHTTPServer 8888
```

Python 3+

```cmd
python -m http.server 8888
```

jetty-runner

```cmd
java -jar jetty-runner-9.3.0.M0.jar  --port 8080 
```

D3는 비동기지원 모듈 정의(AMD) API 지원

```javascript
require.config({paths: {d3: "http://d3js.org/d3.v3.min"}});

require(["d3"], function(d3) {
  console.log(d3.version);
});
```

###  Reference

* D3 github source
https://github.com/mbostock/d3

* D3 API Reference
http://github.com/mbostock/d3/wiki/API-Reference

* D3 Wiki
http://github.com/mbostock/d3/wiki

* D3 gallery sample
https://github.com/mbostock/d3/wiki/Gallery

* D3 Stack Overflow
http://stackoverflow.com/questions/tagged/d3.js

* 한국어 api document
https://github.com/zziuni/d3/wiki/3.0

* D3 Workshop ppt
http://www.slideshare.net/antonkatunin/d3-workshop?ref=http://mobicon.tistory.com/275
