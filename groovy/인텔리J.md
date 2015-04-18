### Mac IOX에 Groovy 설치하기

brew를 이용해서 groovy 2.4를 설치해 봅니다.

```
$> brew install groovy
```

위 명령어를 통해 설치한 후에 `bash_profile` 에 아래의 스크립트를 등록한다.

```ini
# groovy
export GROOVY_HOME="/usr/local/opt/groovy/libexec"
# path
export PATH="$PATH:$GROOVY_HOME"
```

console (iTerm)에서 아래의 내용을 사용해 볼시다.

```
# 버전을 확인
$> groovy --version
# groovy 스크립트 실행을 위한 콘솔
$> groovyConsole

```

## intellij에서 Groovy 실행하기

### Intellij Document
https://confluence.jetbrains.com/display/IntelliJIDEA/Groovy

위는 인텔리J에서 groovy 설치하는 방법이 잘 설명되어 있는 Intellij Document 사이트입니다.


