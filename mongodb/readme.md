# Mongodb

* MongoDB(from humongous)는 전통적인 RDBMS의 대안인 NOSQL Family의 일부로 오픈 소스 *Document-Oriented Database* 을 지향 합니다.
* Data는 JSON과 같은 Dynamic Schema 형태의 Document(문자열로 구성된 단위라고 생각하면 됩니다.) 구조로 저장 되는데 MongoDB에서는 이를 BSON 합니다.
* MongoDB가 다른 문서 데이터베이스와 구별되는 한 가지 기능은 SQL문을 MongoDB 쿼리 함수 호출로 매우 간단하게 변환하는 기능있어 기존 RDBMS를 쉽게 마이그레이션이 가능합니다.

## MongoDB 설정

* 설정 파일 : /usr/local/etc/mongod.conf
* 실행 파일: /usr/local/Cellar/mongodb/2.6.5
* 데이터베이스 위치: /usr/local/var/mongodb
* 로그 위치: /usr/local/var/log/mongodb/mongo.log

```console
$> cat mongod.conf
systemLog:
  destination: file
  path: /usr/local/var/log/mongodb/mongo.log
  logAppend: true
storage:
  dbPath: /usr/local/var/mongodb
net:
  bindIp: 127.0.0.1
```

## MongoDB 설치

### MacOS에 설치하기
```console
$> brew install mongodb
```

SSL 지원 MongoDB 바이너리 설치

```console
$> brew install mongodb --with-openssl
```

### Windows에 설치하기

* 공식홈페이지
https://www.mongodb.com/download-center?jmp=homepage#community

* 다운로드후 설치
* 실행파일 "mongod.cmd"
```
CD C:\Tools\MongoDB\Server\3.4\bin
mongod --dbpath "C:\Tools\MongoDB\DB" --config "C:\Tools\MongoDB\conf\mongod.conf"
```

* 환경파일 "mongod.conf", [메뉴얼참고](https://docs.mongodb.com/manual/reference/configuration-options/#file-format)
```
systemLog:
   destination: file
   path: "C:/Tools/MongoDB/logs/mongod.log"
   logAppend: true
storage:
   journal:
      enabled: true
net:
   bindIp: 0.0.0.0
   port: 27017
```

## MongoDB 실행

mongodb config 를 이용한 실행

```console
$> mongod -f /usr/local/etc/mongod.conf
```

mongodb 데이터베이스 폴더 직접 지정실행

```console
$> mongod --dbpath <path to data directory>
$> mongod --dbpath /usr/local/var/mongodb

2014-11-24T17:29:19.541+0900 [initandlisten] MongoDB starting : pid=8003 port=27017 dbpath=/usr/local/var/mongodb 64-bit host=seokangchun-ui-iMac.local
2014-11-24T17:29:19.542+0900 [initandlisten] db version v2.6.5
2014-11-24T17:29:19.542+0900 [initandlisten] git version: nogitversion
2014-11-24T17:29:19.542+0900 [initandlisten] build info: Darwin miniyosemite.local 14.0.0 Darwin Kernel Version 14.0.0: Fri Sep 19 00:26:44 PDT 2014; root:xnu-2782.1.97~2/RELEASE_X86_64 x86_64 BOOST_LIB_VERSION=1_49
2014-11-24T17:29:19.542+0900 [initandlisten] allocator: tcmalloc
2014-11-24T17:29:19.542+0900 [initandlisten] options: { storage: { dbPath: "/usr/local/var/mongodb" } }
2014-11-24T17:29:19.589+0900 [initandlisten] journal dir=/usr/local/var/mongodb/journal
2014-11-24T17:29:19.589+0900 [initandlisten] recover : no journal files present, no recovery needed
2014-11-24T17:29:19.642+0900 [initandlisten] waiting for connections on port 27017
```

## MongoDB Data Import
* Import data into the collection.
* [메뉴얼참고](https://docs.mongodb.com/getting-started/shell/import-data/)
* [샘플 콜랙션](https://raw.githubusercontent.com/mongodb/docs-assets/primer-dataset/primer-dataset.json)
```
CD "C:\Tools\MongoDB\Server\3.4\bin"
mongoimport --db mongodb_tutorial --collection restaurants --drop --file "C:\Tools\MongoDB\data\primer-dataset.json"
```


## MongoDB 사용법

`mongo`명령어를 이용해 접속

```cmd

$> mongo

Last login: Fri Nov 28 08:31:11 on ttys000
seokangchun-ui-iMac:node-xpush-client seokangchun$ mongo
MongoDB shell version: 2.6.5
connecting to: test

```

### Tutorial 사용법
https://docs.mongodb.com/getting-started/shell/

###  명령어

| 명령어 | 설명 |
|---|---|
|db |현재 접속한 DB 확인|
|show dbs | 모든 DB 확인|
|use mydb | 사용할 DB 지정, 없는 경우 자동 생성된다.|
|help | 도움말 보기|
|db.help() | DB 메소드 도움말 보기|
|show collections | 현재 DB에 Collection을 확인한다.|
|db.things.find() | things에 포함된 Document을 조회 한다, "_id”는 MongoDB가 collection에 입력되는 순간 자동으로 부여하며, mogoDB내에서 유니크 하다.|
|db.things.findOne()|첫번째 Document만 출력한다.|
|it | 더 있는 경우 ‘it'|

#### insert()
Insert a document into a collection named inventory
```javascript
db.inventory.insert(
   {
     item: "ABC1",
     details: {
        model: "14Q3",
        manufacturer: "XYZ Company"
     },
     stock: [ { size: "S", qty: 25 }, { size: "M", qty: 50 } ],
     category: "clothing"
   }
)
```

Insert 성공 시 'WriteResult' 리턴 객체를 반환한다.
```javascript
WriteResult({ "nInserted" : 1 })
```

#### update()
Modifies an existing document or documents in a collection

```javascript
db.collection.update(query, update, options)

db.collection.update(
   <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>
   }
)

database scheme
{ "_id" : ObjectId("548a9e9e66d8aa73287a9ed9"), "A" : "messengerx", "U" : "user02", "PW" : "dkMfrIoYckGvjz83FW3rlHMvUvtF6wfsT0YgUb2C8YM=", "DT" : { "I" : "http://sample.stalk.io:8100/img/default_image.jpg" }, "DS" : { "ionic" : { "N" : null, "TK" : "FW3dGvsJVl" } }, "CD" : ISODate("2014-12-12T07:51:58.602Z"), "GR" : [ "user01", "xodhks_0113", "user03" ], "__v" : 0 }

example update
db.users.update({"A" : "messengerx"}, { $set : {"DT" : { "I":"http://sample.stalk.io:8100/img/default_image.jpg" }}}, {multi:true} );
```

#### remove()
Removes documents from a collection. [Link](http://docs.mongodb.org/manual/reference/method/db.collection.remove/#db.collection.remove)
```javascript
db.collection.remove(
   <query>,
   <justOne>
)

example remove
db.users.remove({"_id" : ObjectId("548a9e9666d8aa73287a9ed8")});
```

## 참고문서

nodejs mongodb api
http://mongodb.github.io/node-mongodb-native/2.0/api-docs/

mongodb manual
http://docs.mongodb.org/manual/tutorial/generate-test-data/

velopert.log
https://velopert.com/457