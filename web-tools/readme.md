# ㅁ Web Developer Tools

## 1. Yeoman 

#### YO - 작업 흐름 관리 도구

#### Grunt - 빌디/테스팅 등의 태스크 러너(실행도구)

#### Bower - 컴포넌트 배포 및 의존성 관리 툴

## 2. Polymer

#### 웹 컴포넌트를 위한 Polyfill 라이브러리 프로젝트

## 3. Bricks

#### x-Tag 기반의 웹 컴포넌트 Polyfill 라이브러리

# ㅁ 웹 컴포넌트에 대한 질문!

* "자주 사용되거나 구조적 분리가 필요한 요소를 다른 요소들과 충돌하지 않는 재활용 가능한 방법이 필요하다."
* "특히 분리되어 있는 HTML, CSS, JS를 하나로 묶어 쉽게 불러들일 수 있으면..."

# ㅁ 웹 컴포넌트를 지탱하는 4가지 규격

#### 1. Shadow DOM
* 컴포넌트를 구성하는 DOM, CSS, JS 캠슐화 및 외부로부터의 간섭을 제어할 수 있도록 스코프 분리
* 하나의 페이지는 하나의 문서로 작성

	> * 브라우저가 하나의 문서로 통합하여 제어

	> * 개발시 다른 요소들과의 구조적인 이슈들이 발생 방지

#### 2. Custom Elements
* 정의된 마크업을 비활성화된 상태로 로딩 및 런타임에서 사용
* 무서을 할 수 있을까.

	> * 새로운 엘리먼트의 등록

	> * 기존 엘리먼트를 상속한 새로운 엘리먼트 확장

	> * Tag에 대한 사용자 기능 지정 및 추가

	> * 기존 엘리먼트의 메소드 및 이벤트 확장
	
#### 3. HTML Templates
* 웹 문서에서 사용할 엘리먼트의 동적인 등록 및 확장
* HTML Template 기능

	> * Text Templating

	> * Script Overloading `<script type="text/template> 구문 </script>`

	> * Offline Dom ( 보이지 않는 Dom )

* 템플릿의 선언
```html
<template id="id">
	<img scr="" alt="image"/>
</template>
```

* 주요특징
	> * 비활성화 기능으로 렌더링되지 않고 스크립트는 실행되지 않으며 리소스는 로딩되지 않고 문서내에서 정상적인 방법으로는 액세스 되지 않음 

	> 

	> * 모든 위치의 태크에서 활용 가능

#### 4. HTML Imports
* 외부로부터 웹 문서내에 문서의 일부/전체를 포함하기 위한 방법 제공
* import
```html
<iframe/>
Ajax
Script hack!
```
* link 
```html
<link rel="import" href="/path/import.html">
```
* Import 이벤트 핸들링
* Script Html Import


# Polymer Web Component 등장.

PPT 참고 : http://www.slideshare.net/cwdoh/polymer-web-components-web-animations?related=1


### Custom Element 
* 선언적이고 가독성이 뛰어나다.
* 직관적인 HTML 코딩이 가능하다.
* 확장 방법의 일반화로 재상용성이 높다.

```html
<paper-tabs selected="0">
  <paper-tab>TAB 1</paper-tab>
  <paper-tab>TAB 2</paper-tab>
  <paper-tab>TAB 3</paper-tab>
</paper-tabs>
```

### 작성중...



