# 명령어

## MySql 백업하기

데이터베이스를 백업하기 위해서는 아래와 같은 명령어를 사용하시면 됩니다.
```cmd
$> mysqldump -u root -p -h 192.168.13.XXX [[DBName]] > [[DumpFileName]]
```

데이터베이스 백업파일을 Import하기 위해서는 아래와 같은 명령어를 사용하시면 됩니다.
```cmd
$> mysql -u root -pqwer12#$ [[DBName]] < [[DumpFileName]]
```

## 데이터베이스 생성 및 권한 주기

```cmd
CREATE DATABASE [database];
GRANT ALL PRIVILEGES ON [database].* TO root@'%';
GRANT ALL PRIVILEGES ON [database].* TO 'root'@'%' IDENTIFIED BY 'xxxxxx' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

* `[database].*` 특정 데이터베이스에 권한을 지정합니다. 만일 `*.*` 이렇게 하면 모든 데이터베이스에 권한을 지정하게 됩니다.

* `GRANT` 문장이 실행될 때 지정된 사용자가 존재하지 않으면 먼저 해당 사용자를 생성하고 권한을 부여합니다. 이경우에는 `IDENTIFIED BY` 절을 이용해 사용자의 비밀번호까지 설정할 수 있습니다. `WITH GRANT OPTION` 권한은 다른 권한과 달리 GRANT 문장의 마지막에 부여합니다.

* `FLUSH PRIVILEGES`으로 권한을 적용합니다.

## MySql 접속하기

```cmd
$> mysql --host=localhost --user=myname --password=mypass mydb
$> mysql -h localhost -u myname -p mydb
password:mypass

```

## MySql root 패스워드 변경

/usr/local/mysql/bin에 보시면 mysql데이터베이스를 관리하는 몇가지 유용한 명령어 들이 있습니다.
mysqladmin이라는 명령어는 mysql을 시작, 종료, 재시작등을 할 수 있는 중요한 명령어가 있습니다.

```cmd
$> pwd
/usr/local/mysql/bin
$> ./mysqladmin -u root -p password xxxxxx
Enter password
```
mysql의 set이란 명령어로 root 암호로 변경 할 수 있습니다.

```cmd
$> ./mysql -u root -p [database name]
Enter password:

$> set password for root=password('xxxxxxxx');
Query OK

```

또 다른 방법

```cmd
$> ./mysql -u root -p [database name]
Enter password:

$> update user set password=password('xxxxxxxx') where user = 'root';
Quer Ok, 3 rows affected
$> flush privileges;
Query Ok

```

## MySql 변수

MySql 서버는 기동하면서 설정 파일의 내용을 읽어 메모리나 작동방식을 초기화 하고 접속된 사용자를 제어하기 위해 설정값을 별도로 저장해 두는데  이렇게 저장된 값을 변수(Valiable)라고 한다.

```cmd

mysql> show global variables;
```


