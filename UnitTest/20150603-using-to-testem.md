# testem

자바스크립트에서 Junit 플러그인과 유사한 기능을 하는 도구로, 특정 테스트 프레임워크에 구애 받지 않고 설정도 간단하여 바로 사용할 수 있는 도구임.

### github
https://github.com/airportyh/testem

### Features

1. Test-framework agnostic. Support for
Jasmine
QUnit
Mocha
Buster.js

2. Two distinct use-cases:
Test-Driven-Development(TDD) — designed to streamline the TDD workflow
Continuous Integration(CI) — designed to work well with popular CI servers like Jenkins or Teamcity

3. Cross-platform support
OS X
Windows
Linux

### Installation

```
npm install testem -g
```

### Configuration File (testem.json)

testem.json 샘플파일

```
{
  "framework": "jasmine",
  "src_files": [
    "hello.js",
    "hello_spec.js"
  ],
  "src_files_ignore": "js/toxic/*.js"
}
```
