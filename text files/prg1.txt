-----Creating database-----

SHOW DATABASES;
CREATE DATABASE 20cs059_library;
USE 20cs059_library;


-----Creating tables-----


CREATE TABLE PUBLISHER(
NAME VARCHAR(20) PRIMARY KEY,
PHONE VARCHAR(10),
ADDRESS VARCHAR(20)
);

CREATE TABLE BOOK(
BOOK_ID INTEGER PRIMARY KEY,
TITLE VARCHAR(20),
PUB_YEAR VARCHAR(20),
PUBLISHER_NAME VARCHAR(20),
FOREIGN KEY(PUBLISHER_NAME) REFERENCES PUBLISHER (NAME) ON DELETE CASCADE
);

CREATE TABLE BOOK_AUTHORS(
AUTHOR_NAME VARCHAR(20),
BOOK_ID INTEGER,
FOREIGN KEY (BOOK_ID) REFERENCES BOOK (BOOK_ID) ON DELETE CASCADE,
PRIMARY KEY(BOOK_ID, AUTHOR_NAME)
);

CREATE TABLE LIBRARY_BRANCH(
BRANCH_ID INTEGER PRIMARY KEY,
BRANCH_NAME VARCHAR(50),
ADDRESS VARCHAR(50)
);

CREATE TABLE BOOK_COPIES(
NO_OF_COPIES INTEGER,
BOOK_ID INTEGER,
FOREIGN KEY(BOOK_ID) REFERENCES BOOK (BOOK_ID) ON DELETE CASCADE,
BRANCH_ID INTEGER,
FOREIGN KEY (BRANCH_ID) REFERENCES LIBRARY_BRANCH (BRANCH_ID) ON DELETE CASCADE,
PRIMARY KEY (BOOK_ID, BRANCH_ID)
);

CREATE TABLE CARD(
CARD_NO INTEGER PRIMARY KEY
);

CREATE TABLE BOOK_LENDING(
DATE_OUT DATE,
DUE_DATE DATE,
BOOK_ID INTEGER,
FOREIGN KEY(BOOK_ID) REFERENCES BOOK(BOOK_ID) ON DELETE CASCADE,
BRANCH_ID INTEGER,
FOREIGN KEY (BRANCH_ID) REFERENCES LIBRARY_BRANCH (BRANCH_ID) ON DELETE CASCADE,
CARD_NO INTEGER,
FOREIGN KEY (CARD_NO) REFERENCES CARD (CARD_NO) ON DELETE CASCADE,
PRIMARY KEY (BOOK_ID, BRANCH_ID, CARD_NO)
);

-----Inserting values-----


INSERT INTO PUBLISHER VALUES ('MCGRAW-HILL',9989076587,'BANGALORE');
INSERT INTO PUBLISHER VALUES ('PEARSON',9889076565,'NEW DELHI');
INSERT INTO PUBLISHER VALUES ('RANDOMHOUSE',7455679345,'HYDERABAD');
INSERT INTO PUBLISHER VALUES ('HACHETTE LIVRE',8970862340,'CHANNAI');
INSERT INTO PUBLISHER VALUES ('GRUPO PLANETA',7756120298,'BANGALORE');

INSERT INTO BOOK VALUES (1,'DBMS','JAN-2017','MCGRAW-HILL');
INSERT INTO BOOK VALUES (2,'ADBMS','JUN-2016', 'MCGRAW-HILL');
INSERT INTO BOOK VALUES (3,'CN','SEP-2016','PEARSON');
INSERT INTO BOOK VALUES (4,'CG','SEP-2015','GRUPO PLANETA');
INSERT INTO BOOK VALUES (5,'OS','MAY-2016','PEARSON');


INSERT INTO BOOK_AUTHORS VALUES('NAVATHE',1);
INSERT INTO BOOK_AUTHORS VALUES('NAVATHE',2);
INSERT INTO BOOK_AUTHORS VALUES('TANENBAUM',3);
INSERT INTO BOOK_AUTHORS VALUES('EDWARD ANGEL',4);
INSERT INTO BOOK_AUTHORS VALUES('GALVIN',5);

INSERT INTO LIBRARY_BRANCH VALUES(10,'RR NAGAR','BANGALORE');
INSERT INTO LIBRARY_BRANCH VALUES(11,'RNSIT','BANGALORE');
INSERT INTO LIBRARY_BRANCH VALUES(12,'RAJAJI NAGAR','BANGALORE');
INSERT INTO LIBRARY_BRANCH VALUES(13,'NITTE','MANGALORE');
INSERT INTO LIBRARY_BRANCH VALUES(14,'MANIPAL','UDUPI');

INSERT INTO BOOK_COPIES VALUES(10,1,10);
INSERT INTO BOOK_COPIES VALUES(5,1,11);
INSERT INTO BOOK_COPIES VALUES(2,2,12);
INSERT INTO BOOK_COPIES VALUES(5,2,13);
INSERT INTO BOOK_COPIES VALUES(7,3,14);
INSERT INTO BOOK_COPIES VALUES(1,5,10);
INSERT INTO BOOK_COPIES VALUES(3,4,11);

INSERT INTO CARD VALUES(100);
INSERT INTO CARD VALUES(101);
INSERT INTO CARD VALUES(102);
INSERT INTO CARD VALUES(103);
INSERT INTO CARD VALUES(104);

INSERT INTO BOOK_LENDING VALUES('2017-01-01','2017-06-01',1,10,101);
INSERT INTO BOOK_LENDING VALUES('2011-01-17','2011-03-17',3,14,101);
INSERT INTO BOOK_LENDING VALUES('2021-02-17','2021-04-17',2,13,101);
INSERT INTO BOOK_LENDING VALUES('2015-03-17','2015-07-17',4,11,101);
INSERT INTO BOOK_LENDING VALUES('2012-04-17','2012-05-17',1,11,104);

SELECT * FROM PUBLISHER;
	+----------------+------------+-----------+
	| NAME           | PHONE      | ADDRESS   |
	+----------------+------------+-----------+
	| GRUPO PLANETA  | 7756120298 | BANGALORE |
	| HACHETTE LIVRE | 8970862340 | CHANNAI   |
	| MCGRAW-HILL    | 9989076587 | BANGALORE |
	| PEARSON        | 9889076565 | NEW DELHI |
	| RANDOMHOUSE    | 7455679345 | HYDERABAD |
	+----------------+------------+-----------+


SELECT * FROM BOOK;
	+---------+-------+----------+----------------+
	| BOOK_ID | TITLE | PUB_YEAR | PUBLISHER_NAME |
	+---------+-------+----------+----------------+
	|       1 | DBMS  | JAN-2017 | MCGRAW-HILL    |
	|       2 | ADBMS | JUN-2016 | MCGRAW-HILL    |
	|       3 | CN    | SEP-2016 | PEARSON        |
	|       4 | CG    | SEP-2015 | GRUPO PLANETA  |
	|       5 | OS    | MAY-2016 | PEARSON        |
	+---------+-------+----------+----------------+


SELECT * FROM BOOK_AUTHORS;
	+--------------+---------+
	| AUTHOR_NAME  | BOOK_ID |
	+--------------+---------+
	| NAVATHE      |       1 |
	| NAVATHE      |       2 |
	| TANENBAUM    |       3 |
	| EDWARD ANGEL |       4 |
	| GALVIN       |       5 |
	+--------------+---------+


SELECT * FROM LIBRARY_BRANCH;
	+-----------+--------------+-----------+
	| BRANCH_ID | BRANCH_NAME  | ADDRESS   |
	+-----------+--------------+-----------+
	|        10 | RR NAGAR     | BANGALORE |
	|        11 | RNSIT        | BANGALORE |
	|        12 | RAJAJI NAGAR | BANGALORE |
	|        13 | NITTE        | MANGALORE |
	|        14 | MANIPAL      | UDUPI     |
	+-----------+--------------+-----------+


SELECT * FROM BOOK_COPIES;
	+--------------+---------+-----------+
	| NO_OF_COPIES | BOOK_ID | BRANCH_ID |
	+--------------+---------+-----------+
	|           10 |       1 |        10 |
	|            5 |       1 |        11 |
	|            2 |       2 |        12 |
	|            5 |       2 |        13 |
	|            7 |       3 |        14 |
	|            3 |       4 |        11 |
	|            1 |       5 |        10 |
	+--------------+---------+-----------+


SELECT * FROM CARD;
	+---------+
	| CARD_NO |
	+---------+
	|     100 |
	|     101 |
	|     102 |
	|     103 |
	|     104 |
	+---------+


SELECT * FROM BOOK_LENDING;
	+------------+------------+---------+-----------+---------+
	| DATE_OUT   | DUE_DATE   | BOOK_ID | BRANCH_ID | CARD_NO |
	+------------+------------+---------+-----------+---------+
	| 2017-01-01 | 2017-06-01 |       1 |        10 |     101 |
	| 2012-04-17 | 2012-05-17 |       1 |        11 |     104 |
	| 2021-02-17 | 2021-04-17 |       2 |        13 |     101 |
	| 2011-01-17 | 2011-03-17 |       3 |        14 |     101 |
	| 2015-03-17 | 2015-07-17 |       4 |        11 |     101 |
	+------------+------------+---------+-----------+---------+


-----Retrieve details of all books in the library - id,title,name of publisher, authors, number of copies in each branch-----

SELECT B.BOOK_ID, B.TITLE, B.PUBLISHER_NAME, A.AUTHOR_NAME, C.NO_OF_COPIES, L.BRANCH_ID
FROM BOOK B, BOOK_AUTHORS A, BOOK_COPIES C, LIBRARY_BRANCH L
WHERE B.BOOK_ID = A.BOOK_ID
AND B.BOOK_ID = C.BOOK_ID
AND L.BRANCH_ID = C.BRANCH_ID;

	+---------+-------+----------------+--------------+--------------+-----------+
	| BOOK_ID | TITLE | PUBLISHER_NAME | AUTHOR_NAME  | NO_OF_COPIES | BRANCH_ID |
	+---------+-------+----------------+--------------+--------------+-----------+
	|       1 | DBMS  | MCGRAW-HILL    | NAVATHE      |           10 |        10 |
	|       1 | DBMS  | MCGRAW-HILL    | NAVATHE      |            5 |        11 |
	|       2 | ADBMS | MCGRAW-HILL    | NAVATHE      |            2 |        12 |
	|       2 | ADBMS | MCGRAW-HILL    | NAVATHE      |            5 |        13 |
	|       3 | CN    | PEARSON        | TANENBAUM    |            7 |        14 |
	|       4 | CG    | GRUPO PLANETA  | EDWARD ANGEL |            3 |        11 |
	|       5 | OS    | PEARSON        | GALVIN       |            1 |        10 |
	+---------+-------+----------------+--------------+--------------+-----------+

-----Get the particulars-----

SELECT CARD_NO
FROM BOOK_LENDING
WHERE DATE_OUT BETWEEN '2011-01-01' AND '2025-07-01'
GROUP BY CARD_NO
HAVING COUNT(*)>3;

	+---------+
	| CARD_NO |
	+---------+
	|     101 |
	+---------+


-----Delete a book in BOOK table. Update the contents of other tables to reflect this data manipulation operation-----

DELETE FROM BOOK
WHERE BOOK_ID=3;

SELECT * FROM BOOK;

	+---------+-------+----------+----------------+
	| BOOK_ID | TITLE | PUB_YEAR | PUBLISHER_NAME |
	+---------+-------+----------+----------------+
	|       1 | DBMS  | JAN-2017 | MCGRAW-HILL    |
	|       2 | ADBMS | JUN-2016 | MCGRAW-HILL    |
	|       4 | CG    | SEP-2015 | GRUPO PLANETA  |
	|       5 | OS    | MAY-2016 | PEARSON        |
	+---------+-------+----------+----------------+


-----Partition the BOOK table based on year of publication. Demonstrate its working with a simple query-----

CREATE VIEW V_PUBLICATION AS
SELECT PUB_YEAR
FROM BOOK;

SELECT * FROM V_PUBLICATION;

	+----------+
	| PUB_YEAR |
	+----------+
	| JAN-2017 |
	| JUN-2016 |
	| SEP-2015 |
	| MAY-2016 |
	+----------+


-----Create a view of all books and its number of copies that are currently available in the library

CREATE VIEW V_BOOKS AS
SELECT B.BOOK_ID, B.TITLE, C.NO_OF_COPIES
FROM BOOK B, BOOK_COPIES C, LIBRARY_BRANCH L
WHERE B.BOOK_ID = C.BOOK_ID
AND C.BRANCH_ID = L.BRANCH_ID;

SELECT * FROM V_BOOKS;

	+---------+-------+--------------+
	| BOOK_ID | TITLE | NO_OF_COPIES |
	+---------+-------+--------------+
	|       1 | DBMS  |           10 |
	|       1 | DBMS  |            5 |
	|       2 | ADBMS |            2 |
	|       2 | ADBMS |            5 |
	|       4 | CG    |            3 |
	|       5 | OS    |            1 |
	+---------+-------+--------------+


