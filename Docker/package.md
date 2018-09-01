### PostgreSQL 설치 및 서버 실행

docker run -p 5432:5432 -e POSTGRES_PASSWORD=qwer12#$ -e POSTGRES_USER=kang -e POSTGRES_DB=springdata --name postgres_boot -d postgres

 docker exec -i -t postgres_boot bash

 su - postrgres

 psql springdata

데이터베이스 조회
 \list

테이블 조회
\dt

 
 