# MySQL 명령어

### MySql 백업하기

데이터베이스를 백업하기 위해서는 아래와 같은 명령어를 사용하시면 됩니다.
```bash
$> mysqldump -u root -p -h 192.168.13.XXX [[DBName]] > [[DumpFileName]]
```

데이터베이스 백업파일을 Import하기 위해서는 아래와 같은 명령어를 사용하시면 됩니다.
```bash
$> mysql -u root -p [[DBName]] < [[DumpFileName]]
```

### 데이터베이스 생성 및 권한 주기

```sql
CREATE DATABASE [database];
CREATE USER 'testuser'@'%' IDENTIFIED BY 'xxxxxx';
CREATE USER 'testuser'@'localhost' IDENTIFIED BY 'xxxxxx';
GRANT ALL PRIVILEGES on [database].* TO 'testuser'@'%';
GRANT INSERT,UPDATE,INDEX,ALTER ON on [database].* TO 'testuser'@'%';
GRANT INSERT,UPDATE,INDEX,ALTER ON on [database].* TO 'testuser'@'localhost';
FLUSH PRIVILEGES;
```
```sql
GRANT ALL PRIVILEGES ON [database].* TO 'root'@'%' IDENTIFIED BY 'xxxxxx' WITH GRANT OPTION;
```

* `[database].*` 특정 데이터베이스에 권한을 지정합니다. 만일 `*.*` 이렇게 하면 모든 데이터베이스에 권한을 지정하게 됩니다.
* `'testuser'@'%'` 원격접속지원 `'testuser'@'localhost'` 로컬에서만 접속 지원. 
* `GRANT` 문장이 실행될 때 지정된 사용자가 존재하지 않으면 먼저 해당 사용자를 생성하고 권한을 부여합니다. 이경우에는 `IDENTIFIED BY` 절을 이용해 사용자의 비밀번호까지 설정할 수 있습니다. `WITH GRANT OPTION` 권한은 다른 권한과 달리 GRANT 문장의 마지막에 부여합니다.

* `FLUSH PRIVILEGES`으로 권한을 적용합니다.

```sql
DROP DATABASE [database]; -- database 삭제
DROP USER 'testuser'@'localhost'; -- 사용자 삭제
REVOKE ALL ON testdb.* FROM 'testuser'@'localhost'; -- 모든 권한 제거
REVOKE DROP ON testdb.* FROM 'testuser'@'localhost'; -- 특정 명령어에 대한 권한을 제거
```

### MySql 접속하기

```bash
$> mysql --host=localhost --user=myname --password=mypass mydb
$> mysql -h localhost -u myname -p mydb
password:mypass

```

### MySql root 패스워드 변경

/usr/local/mysql/bin에 보시면 mysql데이터베이스를 관리하는 몇가지 유용한 명령어 들이 있습니다.
mysqladmin이라는 명령어는 mysql을 시작, 종료, 재시작등을 할 수 있는 중요한 명령어가 있습니다.

```bash
$> pwd
/usr/local/mysql/bin
$> ./mysqladmin -u root -p password xxxxxx
Enter password
```
mysql의 set이란 명령어로 root 암호로 변경 할 수 있습니다.

```bash
$> ./mysql -u root -p [database name]
Enter password:

$> set password for root=password('xxxxxxxx');
Query OK

```

또 다른 방법

```bash
$> ./mysql -u root -p [database name]
Enter password:

$> update user set password=password('xxxxxxxx') where user = 'root';
Quer Ok, 3 rows affected
$> flush privileges;
Query Ok

```

## MySql 변수

MySql 서버는 기동하면서 설정 파일의 내용을 읽어 메모리나 작동방식을 초기화 하고 접속된 사용자를 제어하기 위해 설정값을 별도로 저장해 두는데  이렇게 저장된 값을 변수(Valiable)라고 한다.

```bash

mysql> show global variables;
```

## MySql 전문검색엔진

MySql에 내장된 전문 검색 엔진이 있다 별도의 추가 설정이나 컴파일 없이 바로 사용할 수 있게 준비돼 있으므로 전문 검색 엔진에 대해 별도로 작업할 사항은 없다.

그러나 띄어쓰기나 문장부호 등과 같은 구분자(StopWord)로 구분된 단어만 검색이 가능하므로 정확히 원하는 바를 검색하기가 어려울 때가 많다. 

일본의 몇몇회사가 합작해 일본어를 포함한 UTF-8 문자집합을 지원하는 전문검색엔진을 개발했는데 이것이 트리톤(=[Tritonn](http//qwik.jp/tritonn)이다. 트리톤은  N-그램(n-gram) 방식의 전문 검색 엔진이라서 띄어쓰기나 문장 부호와 같은 구분자에 대한 정의가 필요치 않으며, 구분자 방식의 전문 검색 엔진보다 훨씬 더 검색 정확도가 높은 편이다. 

### 트리톤 다운로드

다운로드 페이지 : http://qwik.jp/tritonn/download.html

트리톤은 MySql 모든버전에서 사용할 수 있는게 아닙니다. MySql 5.0.87의 커뮤니티 버전만 사용할 수 있다. 만약 5.1 버전 이상에서 사용하려면 트리톤 후속모델로 mGroonga라는 전문검색엔진이 출시되었으며 mGroonga는 독립적으로 실행되는 소프트웨어이다. 그러나 MySqld에 익숙한 사용자를 위해 mGroonga라고 하는 플러그인을 제공하고 있다.

### Mroonga

Mroonga는 Full Text Search를 위한 Groonga기반의 MySql 스토리지 엔진이다.
MySQL 5.1 또는 이후 버전에 설치가능합니다.

* 자세한 설지방법 참고 :  http://mroonga.org/
* Mroonga 소개 : http://mroonga.org/docs/characteristic.html


##### `OSX`에서 Mroonga를 설치하기

```bash
$> brew install https://raw.github.com/mroonga/homebrew/master/mroonga.rb --use-homebrew-mysql
```

### 테이블/컬럼 정보보기

```sql
-- 전체 테이블 정보를 주석까지 포함해서 보여줌.
show table status;

-- 테이블 이름 매칭조건으로 보여줌.
show table status like 'memb%';

-- 테이블의 컬럼 정보를 주석까지 포함해서 보여줌.
show full columns from 테이블명;
```

### 버전정보 확인하기

```sql
show variables like '%version%';
```

### 접속한 커텍션 리스트 

```sql
show full processlist;
```

### 데이터베이스 이동

https://opentutorials.org/module/894/6654

















