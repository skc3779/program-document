# Web Sql

HTML5 Web SQL Database

Web SQL Database API는 실제로는 HTML5 규격의 일부가 아닙니다. 그러나 SQL을 사용하는 클라이언트 측 데이터베이스를 조작하는 APIs 집합으로 소개된 별도의 규격입니다.

Web SQL Database는 Safari, Chrome and Opera에서 사용 할 수 있습니다.

### Core Methods

|메소드|설명|
|---|---|
|openDatabase|This method creates the database object either using existing database or creating new one.|
|transaction|This method give us the ability to control a transaction and performing either commit or rollback based on the situation.|
|executeSql|This method is used to execute actual SQL query.|

### Web SQL Tutorial

http://www.tutorialspoint.com/html5/html5_web_sql.htm
http://www.tutorialspoint.com/sql/index.htm


### DataBase 오픈

데이터베이스를 오픈하기 위해서는 5개의 파라메터를 작성해 주어야 합니다.

1. database name 작성
2. version number 작성
3. text description 설명 기술
4. database 크기설정
5. Callback 함수 (이 파라메터의 경우 데이터베이스가 생성되면 기능없는 Callback을 호출한다.)

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
```

### query 실행

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {  
   tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
});
```

### Insert 조작
```javasscript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {
   tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (1, "foobar")');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (2, "logmsg")');
});
```

### read 조작

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {
   tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (1, "foobar")');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (2, "logmsg")');
});
db.transaction(function (tx) {
   tx.executeSql('SELECT * FROM LOGS', [], function (tx, results) {
   var len = results.rows.length, i;
   msg = "<p>Found rows: " + len + "</p>";
   document.querySelector('#status').innerHTML +=  msg;
   for (i = 0; i < len; i++){
      alert(results.rows.item(i).log );
   }
 }, null);
});
```

### 샘플

```javascript

<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
var msg;
db.transaction(function (tx) {
  tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
  tx.executeSql('INSERT INTO LOGS (id, log) VALUES (1, "foobar")');
  tx.executeSql('INSERT INTO LOGS (id, log) VALUES (2, "logmsg")');
  msg = '<p>Log message created and row inserted.</p>';
  document.querySelector('#status').innerHTML =  msg;
});

db.transaction(function (tx) {
  tx.executeSql('SELECT * FROM LOGS', [], function (tx, results) {
   var len = results.rows.length, i;
   msg = "<p>Found rows: " + len + "</p>";
   document.querySelector('#status').innerHTML +=  msg;
   for (i = 0; i < len; i++){
     msg = "<p><b>" + results.rows.item(i).log + "</b></p>";
     document.querySelector('#status').innerHTML +=  msg;
   }
 }, null);
});
</script>
</head>
<body>
<div id="status" name="status">Status Message</div>
</body>
</html>
```
