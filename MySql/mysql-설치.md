# Mysql 설치

Yosemite 버전 (10.10) 에서는  최신버전인 `Mac OS X ver.10.9(x86, 65-bit), DMG Archive` 가 정상적으로 설치가 되지 않는다. 해당 문제를 해결하기 위해서는 아래와 같은 절차로 설치 해야 합니다.

그리고 우선 [Mysql](http://dev.mysql.com/downloads/mysql/) 다운로드 해야 합니다.

1) 설치 시 사용자화 인스톨를 통해서 `Startup Item`를 Skip 시킨 상태에서 설치한다. (기본설치는 설치오류 발생)

2) .bash_profile 에 아래의 구문을 추가등록 합니다.

```cmd
# MySql 5.6.21
export PATH="/usr/local/mysql/bin:$PATH"
```
3) Mysql를 수동으로 실행합니다.

> System Preferences ( 시스템 환경설정 ) 에서 Mysql를 실행 하고 아래의 Start MySql Server를 클릭

> Terminal 창에서 아래와 같이 실행

```cmd
$> sudo /usr/local/mysql/support-files/mysql.server start
or
$> sudo mysql.server start
```

4) OS부팅시 자동으로 Mysql를 실행하기 위해서는 아래의 참고를 보시고 추가설정 해주시면 됩니다.

5) Mac의 Mysql Server는 WorkStation이 존재하지 않기 때문에 본이지 자주 사용하는  MySql Client Utility를  다운받아 사용하시기 바랍니다. 나의 경우에는 [Toad Mac Edition](https://itunes.apple.com/us/app/toad/id747961939?ls=1&mt=12&ac=ToadMacEdition)를 AppStore에서 다운받아 사용하고 있습니다.

* 참고

> http://coolestguidesontheplanet.com/get-apache-mysql-php-phpmyadmin-working-osx-10-10-yosemite/