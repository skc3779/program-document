# The Microloader

"Microloader"는 Sencha's data-driven을 위한 명칭으로 자바스크립트와 CSS를 위한 다이나믹 로더이다.

http://docs.sencha.com/cmd/5.x/microloader.html

## Manifest

### app.json

이파일은 당신의 애플리케이션에 세부사항을 지정한다. 이설정 파일은  Sencha cmd build process에 의해 처음으로 사용된다.

### Ext.manifest

애플리케이션이 실행 될 때  "Ext.manifest"를 로드하는 app.json 콘텐츠가 처리 된다.
Ext JS 5의 Ext.manifest 프로퍼티를 사용하는 것은 "Compatibility Layer"의 활성화를 지정하는 것이다.

### indexHtmlPath
애플리케이션 HTML 문서의 경로를 설정한다. 만일 당신의 서버가 PHP,JSP 또는 다른 기술을 활용한다면 다른 페이지 값으로 변경하면 된다.

```javascript
"indexHtmlPath": "index.html"
```

### theme

Ext JS 애플리케이션의 테마 페키지 이름을 지정한다.
```javascript
"theme": "ext-theme-crisp"
```

### framework


프레임워크 이름을 설정 "ext", "touch"
```javascript
"framework": "ext"
```

### js

자바스크립트 코드파일을 로드한다.
```javascript
"js": [{
    "path": "app.js",
    "bundle": true
}]
```

### css
CSS는 자바스크립트보다 약간 다르게 핸들링된다. Sencha Cmd는 CSS 를 Sass 소스로 부터 컴파일 하기 때문이다.
```javascript
"css": [{
    "path": "boostrap.css",
    "bootstrap": true
}],
```

### 그외 설정  More

http://docs.sencha.com/cmd/5.x/microloader.html#Ext_manifest

```javascript

```

```javascript

```

```javascript

```

```javascript

```