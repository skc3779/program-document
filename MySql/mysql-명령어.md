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
CREATE DATABASE wemebuil;
GRANT ALL ON wemebuil.* TO root@'%' IDENTIFIED BY 'xxxxxx';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'xxxxxx' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

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

또다른 방법

```cmd
$> ./mysql -u root -p [database name]
Enter password:

$> update user set password=password('xxxxxxxx') where user = 'root';
Quer Ok, 3 rows affected
$> flush privileges;
Query Ok

```



