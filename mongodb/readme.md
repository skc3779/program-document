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

```console
$> brew install mongodb
```

SSL 지원 MongoDB 바이너리 설치

```console
$> brew install mongodb --with-openssl
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

## MongoDB 사용법

`mongo`명령어를 이용해 접속

```cmd

$> mongo

Last login: Fri Nov 28 08:31:11 on ttys000
seokangchun-ui-iMac:node-xpush-client seokangchun$ mongo
MongoDB shell version: 2.6.5
connecting to: test

```

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

## 참고문서

nodejs mongodb api
http://mongodb.github.io/node-mongodb-native/2.0/api-docs/

mongodb manual
http://docs.mongodb.org/manual/tutorial/generate-test-data/

