# MySQL
- Structured Query Language
- Create, Read, Update, Delete
- 데이터베이스 서버(database server) -> 데이터베이스(database, schema)->표(table)
- 위쪽 화살표 입력시 이전 코드 불러와짐
## 데이터베이스 서버
- cd/usr/local/mysql/bin
- ./mysql -uroot -p
## 데이터베이스
- 생성 : CREATE DATABASE opentutorials
- 삭제 : DROP DATABASE opentutorials
- 확인 : SHOW DATABASES;
- 사용/선택 : USE opentutorials;
## 표
- row, record, 행
- column, 열
- CREATE  TABLE 표이름();
- INT 숫자 정수 (숫자를 얼마까지 노출 할 것인가 11), NOT NULL 빈값 거절, AUTO_INCREAMENT 자동 1씩 증가
- PRIMARY KEY(id) : id 가 고유값이라고 지정하는것
```bash
CREATE TABLE topic(
    id INT(11) NOT NULL AUTO_INCREAMENT,
    title VARCHAR(100) NOT NULL,
    description TEXT NOT NULL,
    created DATETIME NOT NULL,
    author VARCHAR(30) NULL,
    profile VARCHAR(100) NULL,
    PRIMARY KEY(id)
);
```
- Query OK 나오면 생성됨
- SET PASSWORD = PASSWORD(''); 비번 재생성 경고 뜰때
### DESC topic : CREATE한 테이블 구조 볼 수 있음
|Field|Type|Null|Key|Default|Extra|
|------|---|---|---|---|---|
|id|int(11)|NO|PRI|NULL|auto_increment|
|title|varchar(100)|NO||NULL||
|description|text|YES||NULL||
|created|datetime|NO||NULL||
|author|varchar(30)|YES||NULL||
|profile|varchar(100)|YES||NULL||

### Create row
- INSERT INTO topic : topic표에 삽입
- ./mysql -uroot -p : 시작
- USE opentutorials : 데이터베이스 선택
- SHOW TABLES : topic 이라는 테이블 확인가능
- DESC topic : CREATE한 테이블 구조 볼 수 있음
- INSERT INTO topic(,,,) VALUE('','',''): 행 추가(id 지정안하면 자동 값 증가 생성됨,NOW()현재시간)
- Query OK
- SELECT * FROM topic: topic에서 모든 데이터를 가져와
- 
```bash
    ./mysql -uroot -p
    USE opentutorials;
    SHOW TABLES;
    DESC table;
    INSERT INTO topic (title,description,created,author,profile) VALUES('MySQL','MySQL is ...',NOW(),'jm','developer');
Query OK, 1row affected(0.02sec)
    SELECT * FROM topic;
```
|id|title|description|created|author|profile|
|------|---|---|---|---|---|
|1|MySQL|MySQL is ...|2024-05-14 17:49:59|jm|developer|  
1 row in set(0.00sec)
#### 행 하나 더 추가
```bash
    INSERT INTO topic (title,description,created,author,profile) VALUES('ORACLE','ORACLE is ...',NOW(),'jm','developer');
Query OK, 1row affected(0.02sec)
    SELECT * FROM topic;
```
|id|title|description|created|author|profile|
|------|---|---|---|---|---|
|1|MySQL|MySQL is ...|2024-05-14 17:49:59|jm|developer|
|2|ORACLE|ORACLE is ...|2024-05-14 17:52:15|jm|developer|  
2 row in set(0.00sec)
