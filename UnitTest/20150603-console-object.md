# javascript console log

자바스크립트 개발시 잘 활용하지 못하는 것 중 하나가 console 객체입니다.

### console 로그 패턴

%s 문자, %d,%i 정수, %f 실수, %o 객체, %c 로그스타일

```javascript
console.log('%s은 문자, %o은 객체', 'string', {a:1});

출력 : 'string은 문자, {a:1}은 객체'
```


### 함수명

콘솔 객체는 로그 표현함수, 객체 표현황수, 기타 함수로 구분됩니다. 로그 표현 함수는 로그를 표현할때 단순이 로그만을 사용하면서 나중에 로그가 쌓였을 때 구분이 어려울 수 있기 때문에 좀 편하게 구분해 보기 위해 사용 합니다.

console.error : Errors 탭에 표시되는 log로 에러일 경우 사용함.
console.warn : Warns 탭에 표시되는 log로 경고일 경우 사용함.
console.info : Info 탭에 표시되는 log로 정보일 경우 사용함.
console.debug : Debug Info 탭에 표시되는 log로 디버깅 할 경우 사용함.
console.assert : 첫 번째 인자가 false 일 경우 error탭에 표시되며, 분기를 통해 로그를 남기고 싶은 경우 사용함.

### 객체, 해시, 배열 형태의 데이터

로그를 사용하다가 보면 문자나 숫자만 확인하는 것이 아니라 객체, 해시, 배열, 형태의 데이터를 확인해야 하는 경우 사용함.

console.dir : json 형태의 데이터를 테이블 형식으로 보여주는 함수.
console.dirxml : xml이나 element와 같이 노드를 넣으면 전체 노드를 한눈에 확인 할 수 있는 함수.
console.group : 특정 메서드의 로그를 별도로 표현하고 싶을때 group과 groupEnd를 이용하면 로그를  그룹지어서 볼 수 있음
console.table : 보통 배열 데이터들을 데이블 형식으로 보고 싶을 때 많이 사용함, 칼럼은 정렬이 되는 특징을 가지고 있음.
