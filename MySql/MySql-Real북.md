# Real MySql Books

## 덤프 Database 및 샘플코드

덤프 및 샘플코드 설치 : http://github.com/wikibook/realmysql/archive/master.zip

## 덤프 설치하기

master.zip 압축을 풀게되면, RealMySQL_sample 폴더와 TestDatabase-Employee 폴더 2개가 보인다 이중 TestDatabase-employee 하위로 이동 후 설치된 MySql 엔진이 InnoDB인 경우 employees.sql을 설치하면 됩니다.
* 아래명령어를 실행하기 전에 load_salaries.zip 파일의 압축도 풀어준다.

```cmd

$> pwd
~/TestDatabase-Employee
$> Mysql -u root -p mysql < employees.sql
```

## End.