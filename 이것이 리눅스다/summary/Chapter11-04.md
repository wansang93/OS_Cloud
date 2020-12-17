## 11-04 데이터베이스 서버-데이터베이스 생성과 운영

### [실습3] 쇼핑몰 DB 구축

실습목표
- 쇼핑몰 DB를 MariaDB 서버에 구축
- SQL 구문이 익숙해지도록 연습

cmd 창에서

```powershell
$ cd "\Program Files\MariaDB 10.5\bin"
$ mysql -h 192.168.111.100 -u winuser -p
```

```sql
CREATE DATABASE shopping_db;
USE shopping_db;
DROP DATABASE shopping_db;
CREATE DATABASE shopping_db CHARACTER SET utf8;
USE shopping_db;

CREATE TABLE customer ( id VARCHAR(10) NOT NULL PRIMARY KEY, name VARCHAR(5), age INT, address VARCHAR(5) );

CREATE TABLE purchase ( no INT NOT NULL PRIMARY KEY AUTO_INCREMENT, cust_id VARCHAR(10), date CHAR(8), product VARCHAR(5) );

DESC customer;
DESC purchase;

INSERT INTO customer VALUES ('hong', '홍길동', 22, '경기');
INSERT INTO customer VALUES ('dang', '당탕이', 23, '충북');
INSERT INTO customer VALUES ('ppuni', '이뿌니', 30, '서울');
INSERT INTO customer VALUES ('john', '존벤이', 28, '강원');

INSERT INTO purchase VALUES (null, 'hong', 20161227, 'TV');
INSERT INTO purchase VALUES (null, 'ppuni', 20160305, '냉장고');
INSERT INTO purchase VALUES (null, 'john', 20191217, '세탁기');
INSERT INTO purchase VALUES (null, 'hong', 20201217, '비디오');

SELECT * FROM customer;
SELECT * FROM purchase;
```

![11-04 실습 결과](./assets/11-04실습결과.png)