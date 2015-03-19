# 유용한 기능

## WebStrom 9 속도향상방법

mac 컴퓨터의 경우 `idea.vmoptions` 파일에 아래의 구문을 추가하고 저장한다.

위치
```cmd
$>cd /Applications/WebStorm.app/Contents/bin/idea.vmoptions
```

추가해야 할 구문
```text
-Dawt.useSystemAAFontSettings=lcd
-Dawt.java2d.opengl=true
```
