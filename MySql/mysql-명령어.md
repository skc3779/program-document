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