## 리눅스 커널

#### OS 확인

```
$> uname -a
$> uname -r
$> cat /proc/version
```

#### 프로세스 정보 확인

```
$> dmidecode -t processor
$> lscpu
```

#### 메모리 정보 확인

```
$> dmidecode -t memory | grep -i size:
```

* ubuntu

```
cat /proc/meminfo | grep MemTotal
```

#### 디스크 정보 확인하기

```
$> df -h
```

#### 파일관련 명령어  

* 리눅스 cat, more, less, head, tail - 파일내용 확인

> http://webdir.tistory.com/142

* tail

```
마지막 부분의 20개행까지 출력
tail -n 20 test

마지막에서 200byte 까지를 출력
tail -c 200 test  

로그파일을 실시간 모니터링, 종료는 Ctrl-c
tail -f /var/log/messages
```

* more

more 명령어는 특정파일의 내용을 확인하는 그 페이지에서 바로 vi 로 파일을 열어서 편집을 할 수도 있으며 텍스트 파일의 내용을 한 페이지씩 차례대로 확인할 수 있다.

```
사용법 : more 파일명
more test

많은 양의 파일리스트를 확인할때 파이프를 이용해 연결
ls -l /etc | more
특정 파일의 내용을 확인하고 있는 상태에서 사용할 수 있는 키

h : more 명령어상태에서 사용할 수 있는 키 도움말 확인
Space Bar : 한 화면씩 뒤로 이동하기 (f와 동일)
Enter : 현재행에서 한 행씩 뒤로 이동하기
q : more 명령어 종료하기
f : 한 페이지씩 뒤로 이동하기(Space Bar 와 동일)
b : 한 페이지씩 앞으로 이동하기
= : 현재 위치의 행번호 표시하기
/문자열 : 지정한 문자열을 검색하기
n : /문자열로 검색한 문자열을 차례대로 계속해서 찾기
!쉘명령어 : more 명령어상태에서 쉘명령어를 실행하기
v : more 명령어로 열려있는 파일의 현재위치에서 vi를 실행하기
```

### 패스워드 변경

root 계정을 이용해서
```
$> sudo passwd <계정명>
new password
```