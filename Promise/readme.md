# Promise

자바스크립트를 사용하다 보면 비동기 콜백요소들이 많아서 가독성과 디버깅등에 어려움을 격게 됩니다. 이를 회피하는 방법중 하나가 Promise를 사용하는 것입니다.

관련해서 *Matt Greer의 블로그* 글을 참조해 보면 좋습니다. [JavaScript Promises ... In Wicked Detail](http://www.mattgreer.org/articles/promises-in-wicked-detail/)

#### Promise란 무엇일까요 (한빛미디어)?

Promise는 전통적인 콜백 패턴이 가진 단점을 일부 보완하며 비동기 처리 시점을 명확하게 표현해 줍니다. 다시말해 비동기 처리 로직을 추상화한 객체와 그것을 조작하는 방식을 말합닏. 이 개념은 E 언어에서 처음 고안됐으며, 병렬과 병행 프로그램밍을 위한 일종의 디자인 패턴이라 할 수 있습니다. 보통은 자바스크립트에서는 비동기 처리를 위해서 콜백을 사용합니다. "간단한 사용사례" 참고, 그러나 Promise를 지원하는 함수는 비동기 처리 로직을 추상화한 promise 객체를 반환합니다. 그리고 사례에서 볼 수 있듣이 객체를 변수에 대입하고 성공시 동작 할 함수와 실패 시 동작할 함수를 등록해 사용합니다.

```javascript
function asyncFunction() {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            resolve('Async Hello world');
        }, 16);
    });
}

asyncFunction().then(function (value) {
    console.log(value); // => 'Async Hello world'
}).catch(function (error) {
    console.log(error);
});
```
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
