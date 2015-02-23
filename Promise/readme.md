# Promise

자바스크립트를 사용하다 보면 비동기 콜백요소들이 많아서 가독성과 디버깅등에 어려움을 격게 됩니다. 이를 회피하는 방법중 하나가 Promise를 사용하는 것입니다.

관련해서 *Matt Greer의 블로그* 글을 참조해 보면 좋습니다. [JavaScript Promises ... In Wicked Detail](http://www.mattgreer.org/articles/promises-in-wicked-detail/)

#### 그럼 Promise가 왜 필요할 까요?

---
왜 Promise를 자세히 이해하고 있어야 할까요. 그 이유는 자바코드의 가독성을 높이고 개발능력이 향상되고 더 성공적으로 디버깅을 할 수 있기 때문입니다. Promise는 JQuery를 비롯해 공개된 오픈라이브러리 등에 다양하게 사용하고 있습니다. 이를 올바르게 사용하고 자신의 코드의 품질을 한단계 높일 수 있습니다.

#### 간단한 사용사례

---

우리는 아래와 같은 방식을
```javascript
doSomething(function(value) {
  console.log('Got a value:' + value);
});
```
아래와 같이 바꾸어 보고 싶다면

```javascript
doSomething().then(function(value) {
  console.log('Got a value:' + value);
});
```

아래와 같이 작성한 doSomething을
```javascript
function doSomething(callback) {
  var value = 42;
  callback(value);
}
````

아래와 같이 **promise** 기반으로 변경한다.
```javascript
function doSomething() {
  return {
    then: function(callback) {
      var value = 42;
      callback(value);
    }
  };
}
```


## Promise 참고링크

1. [JavaScript Promise](http://www.hanbit.co.kr/ebook/look.html?isbn=9788968487293), AZU지음 / 주우영 옮김 / 한빛미디어에서 무료로 다운로드 받을 수 있습니다.
2. [Bluebird](https://github.com/petkaantonov/bluebird) 는 혁신적인 기능과 성능에 초점을 맞춘 완벽한 기능의  **Promise** 라이브러리 입니다.
