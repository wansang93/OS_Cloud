## 11-01 데이터베이스 서버-DBMS 개념과 SQL문

### DBMS 개념

- Data: 자료
- Table: 데이터를 표 형식으로 표현
- Database: 테이블의 집합, 테이블을 저장하는 저장 공간
- DBMS: DataBase Management System
- RDBMS: Relational DBMS
- Record or Row: 행
- Field or Column: 열
- Data Type: 각 필드에 입력할 값의 타입(정수, 문자, 날짜 등)
- Field name: 각 필드(열)의 이름
- SQL(Structured Query Language): 구조화된 질의 언어

### 필수 SQL 구문

1. DB 관련
   - DB 이름 조회: `SHOW DATABASES;`
   - 사용할 DB: `USE db_name;`
   - DB 생성: `CREATE DATABASE db_name`
   - DB 삭제: `DROP DATABASE db_name`
2. 테이블 관련
   - 테이블 이름 조회: `SHOW TABLES`
   - 테이블 구조 조회: `EXPLAIN table_name`, `DESC table_name`
   - 테이블 생성: `CREATE TABLE table_name (field_name1, field_type1, ...)`
   - 테이블 삭제: `DROP TABLE table_name`
   - 테이블 수정: `ALTER TABLE table_name <option>`
     - `MODIFY name CHAR(20)`: 필드 타입 바꾸기
     - `CHANGE name fullname CHAR(10)`: 필드 바꾸기
     - `ADD phone VARCHAR(20) AFTER name;`: 필드 추가
     - `DROP age`: 필드 삭제 
3. 레코드 관련
   - `INSERT INTO table_name VALUES (값1, 값2, ...);`: 레코드 삽입
   - `DELETE FROM table_name WHERE 조건;`: 레코드 삭제
   - `UPDATE table_name SET 필드이름1=수정할값1, ... WHERE 조건;`: 레코드 수정
4. 테이블 조회
   - `SELECT 필드이름1, 필드이름2, ... FROM 테이블이름 WHERE 조건;`
