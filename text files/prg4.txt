CREATE DATABASE 20cs059_college;

USE 20cs059_college;

CREATE TABLE STUDENT
(
USN VARCHAR(10) PRIMARY KEY,
SNAME VARCHAR(25),
ADDRESS VARCHAR(25),
PHONE VARCHAR(25),
GENDER CHAR(1)
);

CREATE TABLE SEMSEC
(
SSID VARCHAR(5) PRIMARY KEY,
SEM INTEGER(2),
SEC CHAR(1)
);

CREATE TABLE CLASS
(
USN VARCHAR(10),
SSID VARCHAR(5),
PRIMARY KEY(USN, SSID),
FOREIGN KEY(USN) REFERENCES STUDENT(USN),
FOREIGN KEY(SSID) REFERENCES SEMSEC(SSID));

CREATE TABLE SUBJECT
(
SUBCODE VARCHAR(8),
TITLE VARCHAR(20),
SEM INTEGER(2),
CREDITS INTEGER(2),
PRIMARY KEY(SUBCODE));

CREATE TABLE IAMARKS
(
USN VARCHAR(10),
SUBCODE VARCHAR(8),
SSID VARCHAR(5),
TEST1 INT(2),
TEST2 INT(2),
TEST3 INT(2),
FINALIA INT(2),
PRIMARY KEY(USN,SUBCODE,SSID),
FOREIGN KEY(USN) REFERENCES STUDENT(USN),
FOREIGN KEY(SUBCODE) REFERENCES SUBJECT(SUBCODE),
FOREIGN KEY(SSID) REFERENCES SEMSEC(SSID));

DESC STUDENT;
	+---------+-------------+------+-----+---------+-------+
	| Field   | Type        | Null | Key | Default | Extra |
	+---------+-------------+------+-----+---------+-------+
	| USN     | varchar(10) | NO   | PRI | NULL    |       |
	| SNAME   | varchar(25) | YES  |     | NULL    |       |
	| ADDRESS | varchar(25) | YES  |     | NULL    |       |
	| PHONE   | varchar(25) | YES  |     | NULL    |       |
	| GENDER  | char(1)     | YES  |     | NULL    |       |
	+---------+-------------+------+-----+---------+-------+

DESC SEMSEC;
	+-------+------------+------+-----+---------+-------+
	| Field | Type       | Null | Key | Default | Extra |
	+-------+------------+------+-----+---------+-------+
	| SSID  | varchar(5) | NO   | PRI | NULL    |       |
	| SEM   | int        | YES  |     | NULL    |       |
	| SEC   | char(1)    | YES  |     | NULL    |       |
	+-------+------------+------+-----+---------+-------+

DESC CLASS;
	+-------+-------------+------+-----+---------+-------+
	| Field | Type        | Null | Key | Default | Extra |
	+-------+-------------+------+-----+---------+-------+
	| USN   | varchar(10) | NO   | PRI | NULL    |       |
	| SSID  | varchar(5)  | NO   | PRI | NULL    |       |
	+-------+-------------+------+-----+---------+-------+

DESC SUBJECT;
	+---------+-------------+------+-----+---------+-------+
	| Field   | Type        | Null | Key | Default | Extra |
	+---------+-------------+------+-----+---------+-------+
	| SUBCODE | varchar(8)  | NO   | PRI | NULL    |       |
	| TITLE   | varchar(20) | YES  |     | NULL    |       |
	| SEM     | int         | YES  |     | NULL    |       |
	| CREDITS | int         | YES  |     | NULL    |       |
	+---------+-------------+------+-----+---------+-------+

DESC IAMARKS;
	+---------+-------------+------+-----+---------+-------+
	| Field   | Type        | Null | Key | Default | Extra |
	+---------+-------------+------+-----+---------+-------+
	| USN     | varchar(10) | NO   | PRI | NULL    |       |
	| SUBCODE | varchar(8)  | NO   | PRI | NULL    |       |
	| SSID    | varchar(5)  | NO   | PRI | NULL    |       |
	| TEST1   | int         | YES  |     | NULL    |       |
	| TEST2   | int         | YES  |     | NULL    |       |
	| TEST3   | int         | YES  |     | NULL    |       |
	| FINALIA | int         | YES  |     | NULL    |       |
	+---------+-------------+------+-----+---------+-------+


INSERT INTO STUDENT VALUES('1RN13CS020', 'AKSHAY', 'BELAGAVI', 8877881122, 'M');
INSERT INTO STUDENT VALUES('1RN13CS062', 'SANDHYA', 'BENGALURU', 7722829912, 'F');
INSERT INTO STUDENT VALUES('1RN13CS091', 'TEESHA', 'BENGALURU', 7712312312, 'F');
INSERT INTO STUDENT VALUES('1RN13CS066' ,'SUPRIYA' ,'MANGALURU', 8877881122, 'F');
INSERT INTO STUDENT VALUES('1RN14CS010', 'ABHAY', 'BENGALURU', 9900211201, 'M');
INSERT INTO STUDENT VALUES('1RN14CS032', 'BHASKAR', 'BENGALURU', 9923211099, 'M');
INSERT INTO STUDENT VALUES('1RN14CS025', 'ASMI', 'BENGALURU', 7894737377, 'F');
INSERT INTO STUDENT VALUES('1RN15CS011', 'AJAY', 'TUMKUR', 9845091341, 'M');
INSERT INTO STUDENT VALUES('1RN15CS029','CHITRA','DAVANGERE', 7492749274, 'F');
INSERT INTO STUDENT VALUES('1RN15CS045', 'JEEVA', 'BELLARY', 7593740962, 'M');
INSERT INTO STUDENT VALUES('1RN15CS091', 'SANTOSH', 'MANGALURU', 8839473823, 'M');
INSERT INTO STUDENT VALUES('1RN16CS045', 'ISMAIL', 'KALBURGI', 8406840384, 'M');
INSERT INTO STUDENT VALUES('1RN16CS088', 'SAMEERA', 'SHIMOGA', 7985779047, 'F');
INSERT INTO STUDENT VALUES('1RN16CS122', 'VINAYAKA', 'CHIKAMAGALUR', 6743957985, 'M');


INSERT INTO SEMSEC VALUES('CSE8A', 8, 'A');
INSERT INTO SEMSEC VALUES('CSE8B', 8, 'B');
INSERT INTO SEMSEC VALUES('CSE8C', 8, 'C');

INSERT INTO SEMSEC VALUES('CSE7A', 7, 'A');
INSERT INTO SEMSEC VALUES('CSE7B', 7, 'B');
INSERT INTO SEMSEC VALUES('CSE7C', 7, 'C');

INSERT INTO SEMSEC VALUES('CSE6A', 6, 'A');
INSERT INTO SEMSEC VALUES('CSE6B', 6, 'B');
INSERT INTO SEMSEC VALUES('CSE6C', 6, 'C');

INSERT INTO SEMSEC VALUES('CSE5A', 5, 'A');
INSERT INTO SEMSEC VALUES('CSE5B', 5, 'B');
INSERT INTO SEMSEC VALUES('CSE5C', 5, 'C');

INSERT INTO SEMSEC VALUES('CSE4A', 4, 'A');
INSERT INTO SEMSEC VALUES('CSE4B', 4, 'B');
INSERT INTO SEMSEC VALUES('CSE4C', 4, 'C');

INSERT INTO SEMSEC VALUES('CSE3A', 3, 'A');
INSERT INTO SEMSEC VALUES('CSE3B', 3, 'B');
INSERT INTO SEMSEC VALUES('CSE3C', 3, 'C');

INSERT INTO SEMSEC VALUES('CSE2A', 2, 'A');
INSERT INTO SEMSEC VALUES('CSE2B', 2, 'B');
INSERT INTO SEMSEC VALUES('CSE2C', 2, 'C');

INSERT INTO SEMSEC VALUES('CSE1A', 1, 'A');
INSERT INTO SEMSEC VALUES('CSE1B', 1, 'B');
INSERT INTO SEMSEC VALUES('CSE1C', 1, 'C');

INSERT INTO CLASS VALUES('1RN13CS020','CSE8A');
INSERT INTO CLASS VALUES('1RN13CS062','CSE8A');
INSERT INTO CLASS VALUES('1RN13CS066','CSE8B');
INSERT INTO CLASS VALUES('1RN13CS091','CSE8C');

INSERT INTO CLASS VALUES('1RN14CS010','CSE7A');
INSERT INTO CLASS VALUES('1RN14CS025','CSE7A');
INSERT INTO CLASS VALUES('1RN14CS032','CSE7A');

INSERT INTO CLASS VALUES('1RN15CS011','CSE4A');
INSERT INTO CLASS VALUES('1RN15CS029','CSE4A');
INSERT INTO CLASS VALUES('1RN15CS045','CSE4B');
INSERT INTO CLASS VALUES('1RN15CS091','CSE4C');

INSERT INTO CLASS VALUES('1RN16CS045','CSE3A');
INSERT INTO CLASS VALUES('1RN16CS088','CSE3B');
INSERT INTO CLASS VALUES('1RN16CS122','CSE3C');

INSERT INTO SUBJECT VALUES('10CS81','ACA',8,4);
INSERT INTO SUBJECT VALUES('10CS82','SSM',8,4);
INSERT INTO SUBJECT VALUES('10CS83','NM',8,4);
INSERT INTO SUBJECT VALUES('10CS84','CC',8,4);
INSERT INTO SUBJECT VALUES('10CS85','PW',8,4);

INSERT INTO SUBJECT VALUES('10CS71','OOAD',7,4);
INSERT INTO SUBJECT VALUES('10CS72','ECS',7,4);
INSERT INTO SUBJECT VALUES('10CS73','PTW',7,4);
INSERT INTO SUBJECT VALUES('10CS74','DWDM',7,4);
INSERT INTO SUBJECT VALUES('10CS75','JAVA',7,4);
INSERT INTO SUBJECT VALUES('10CS76','SAN',7,4);

INSERT INTO SUBJECT VALUES('10CS51','ME',5,4);
INSERT INTO SUBJECT VALUES('10CS52','CN',5,4);
INSERT INTO SUBJECT VALUES('10CS53','DBMS',5,4);
INSERT INTO SUBJECT VALUES('10CS54','ATC',5,4);
INSERT INTO SUBJECT VALUES('10CS55','JAVA',5,3);
INSERT INTO SUBJECT VALUES('10CS56','AI',5,3);

INSERT INTO SUBJECT VALUES('10CS41','M4',4,4);
INSERT INTO SUBJECT VALUES('10CS42','SE',4,4);
INSERT INTO SUBJECT VALUES('10CS43','DAA',4,4);
INSERT INTO SUBJECT VALUES('10CS44','MPMC',4,4);
INSERT INTO SUBJECT VALUES('10CS45','OOC',4,3);
INSERT INTO SUBJECT VALUES('10CS46','DC',4,3);

INSERT INTO SUBJECT VALUES('10CS31','M3',3,4);
INSERT INTO SUBJECT VALUES('10CS32','ADE',3,4);
INSERT INTO SUBJECT VALUES('10CS33','DSA',3,4);
INSERT INTO SUBJECT VALUES('10CS34','CO',3,4);
INSERT INTO SUBJECT VALUES('10CS35','USP',3,3);
INSERT INTO SUBJECT VALUES('10CS36','DMS',3,3);

INSERT INTO IAMARKS (USN,SUBCODE,SSID,TEST1,TEST2,TEST3)
VALUES('1RN13CS091','10CS81','CSE8C',15,16,18);
INSERT INTO IAMARKS (USN,SUBCODE,SSID,TEST1,TEST2,TEST3)
VALUES('1RN13CS091','10CS82','CSE8C',12,19,14);
INSERT INTO IAMARKS (USN,SUBCODE,SSID,TEST1,TEST2,TEST3)
VALUES('1RN13CS091','10CS83','CSE8C',19,15,20);
INSERT INTO IAMARKS (USN,SUBCODE,SSID,TEST1,TEST2,TEST3)
VALUES('1RN13CS091','10CS84','CSE8C',20,16,19);
INSERT INTO IAMARKS (USN,SUBCODE,SSID,TEST1,TEST2,TEST3)
VALUES('1RN13CS091','10CS85','CSE8C',15,15,12);

SELECT * FROM STUDENT;
	+------------+----------+--------------+------------+--------+
	| USN        | SNAME    | ADDRESS      | PHONE      | GENDER |
	+------------+----------+--------------+------------+--------+
	| 1RN13CS020 | AKSHAY   | BELAGAVI     | 8877881122 | M      |
	| 1RN13CS062 | SANDHYA  | BENGALURU    | 7722829912 | F      |
	| 1RN13CS066 | SUPRIYA  | MANGALURU    | 8877881122 | F      |
	| 1RN13CS091 | TEESHA   | BENGALURU    | 7712312312 | F      |
	| 1RN14CS010 | ABHAY    | BENGALURU    | 9900211201 | M      |
	| 1RN14CS025 | ASMI     | BENGALURU    | 7894737377 | F      |
	| 1RN14CS032 | BHASKAR  | BENGALURU    | 9923211099 | M      |
	| 1RN15CS011 | AJAY     | TUMKUR       | 9845091341 | M      |
	| 1RN15CS029 | CHITRA   | DAVANGERE    | 7492749274 | F      |
	| 1RN15CS045 | JEEVA    | BELLARY      | 7593740962 | M      |
	| 1RN15CS091 | SANTOSH  | MANGALURU    | 8839473823 | M      |
	| 1RN16CS045 | ISMAIL   | KALBURGI     | 8406840384 | M      |
	| 1RN16CS088 | SAMEERA  | SHIMOGA      | 7985779047 | F      |
	| 1RN16CS122 | VINAYAKA | CHIKAMAGALUR | 6743957985 | M      |
	+------------+----------+--------------+------------+--------+


SELECT * FROM SEMSEC;
	+-------+------+------+
	| SSID  | SEM  | SEC  |
	+-------+------+------+
	| CSE1A |    1 | A    |
	| CSE1B |    1 | B    |
	| CSE1C |    1 | C    |
	| CSE2A |    2 | A    |
	| CSE2B |    2 | B    |
	| CSE2C |    2 | C    |
	| CSE3A |    3 | A    |
	| CSE3B |    3 | B    |
	| CSE3C |    3 | C    |
	| CSE4A |    4 | A    |
	| CSE4B |    4 | B    |
	| CSE4C |    4 | C    |
	| CSE5A |    5 | A    |
	| CSE5B |    5 | B    |
	| CSE5C |    5 | C    |
	| CSE6A |    6 | A    |
	| CSE6B |    6 | B    |
	| CSE6C |    6 | C    |
	| CSE7A |    7 | A    |
	| CSE7B |    7 | B    |
	| CSE7C |    7 | C    |
	| CSE8A |    8 | A    |
	| CSE8B |    8 | B    |
	| CSE8C |    8 | C    |
	+-------+------+------+

SELECT * FROM CLASS;
	+------------+-------+
	| USN        | SSID  |
	+------------+-------+
	| 1RN16CS045 | CSE3A |
	| 1RN16CS088 | CSE3B |
	| 1RN16CS122 | CSE3C |
	| 1RN15CS011 | CSE4A |
	| 1RN15CS029 | CSE4A |
	| 1RN15CS045 | CSE4B |
	| 1RN15CS091 | CSE4C |
	| 1RN14CS010 | CSE7A |
	| 1RN14CS025 | CSE7A |
	| 1RN14CS032 | CSE7A |
	| 1RN13CS020 | CSE8A |
	| 1RN13CS062 | CSE8A |
	| 1RN13CS066 | CSE8B |
	| 1RN13CS091 | CSE8C |
	+------------+-------+

SELECT * FROM SUBJECT;
	+---------+-------+------+---------+
	| SUBCODE | TITLE | SEM  | CREDITS |
	+---------+-------+------+---------+
	| 10CS31  | M3    |    3 |       4 |
	| 10CS32  | ADE   |    3 |       4 |
	| 10CS33  | DSA   |    3 |       4 |
	| 10CS34  | CO    |    3 |       4 |
	| 10CS35  | USP   |    3 |       3 |
	| 10CS36  | DMS   |    3 |       3 |
	| 10CS41  | M4    |    4 |       4 |
	| 10CS42  | SE    |    4 |       4 |
	| 10CS43  | DAA   |    4 |       4 |
	| 10CS44  | MPMC  |    4 |       4 |
	| 10CS45  | OOC   |    4 |       3 |
	| 10CS46  | DC    |    4 |       3 |
	| 10CS51  | ME    |    5 |       4 |
	| 10CS52  | CN    |    5 |       4 |
	| 10CS53  | DBMS  |    5 |       4 |
	| 10CS54  | ATC   |    5 |       4 |
	| 10CS55  | JAVA  |    5 |       3 |
	| 10CS56  | AI    |    5 |       3 |
	| 10CS71  | OOAD  |    7 |       4 |
	| 10CS72  | ECS   |    7 |       4 |
	| 10CS73  | PTW   |    7 |       4 |
	| 10CS74  | DWDM  |    7 |       4 |
	| 10CS75  | JAVA  |    7 |       4 |
	| 10CS76  | SAN   |    7 |       4 |
	| 10CS81  | ACA   |    8 |       4 |
	| 10CS82  | SSM   |    8 |       4 |
	| 10CS83  | NM    |    8 |       4 |
	| 10CS84  | CC    |    8 |       4 |
	| 10CS85  | PW    |    8 |       4 |
	+---------+-------+------+---------+


SELECT * FROM IAMARKS;
	+------------+---------+-------+-------+-------+-------+---------+
	| USN        | SUBCODE | SSID  | TEST1 | TEST2 | TEST3 | FINALIA |
	+------------+---------+-------+-------+-------+-------+---------+
	| 1RN13CS091 | 10CS81  | CSE8C |    15 |    16 |    18 |    NULL |
	| 1RN13CS091 | 10CS82  | CSE8C |    12 |    19 |    14 |    NULL |
	| 1RN13CS091 | 10CS83  | CSE8C |    19 |    15 |    20 |    NULL |
	| 1RN13CS091 | 10CS84  | CSE8C |    20 |    16 |    19 |    NULL |
	| 1RN13CS091 | 10CS85  | CSE8C |    15 |    15 |    12 |    NULL |
	+------------+---------+-------+-------+-------+-------+---------+
	
---Queries---
---1.List all the student details in fourth semester 'C' section---

SELECT S.*,SS.SEM,SS.SEC
FROM STUDENT S,SEMSEC SS,CLASS C
WHERE S.USN=C.USN AND SS.SSID=C.SSID AND SS.SEM=4 AND SS.SEC='C';

	+------------+---------+-----------+------------+--------+------+------+
	| USN        | SNAME   | ADDRESS   | PHONE      | GENDER | SEM  | SEC  |
	+------------+---------+-----------+------------+--------+------+------+
	| 1RN15CS091 | SANTOSH | MANGALURU | 8839473823 | M      |    4 | C    |
	+------------+---------+-----------+------------+--------+------+------+

---2.Compute the total number of male and female students in each semester and in each section.---

SELECT SS.SEM,SS.SEC,S.GENDER, COUNT(S.GENDER) AS COUNT
FROM STUDENT S, SEMSEC SS, CLASS C
WHERE S.USN=C.USN AND SS.SSID=C.SSID
GROUP BY SS.SEM,SS.SEC,S.GENDER
ORDER BY SEM;

	+------+------+--------+-------+
	| SEM  | SEC  | GENDER | COUNT |
	+------+------+--------+-------+
	|    3 | A    | M      |     1 |
	|    3 | B    | F      |     1 |
	|    3 | C    | M      |     1 |
	|    4 | A    | F      |     1 |
	|    4 | A    | M      |     1 |
	|    4 | B    | M      |     1 |
	|    4 | C    | M      |     1 |
	|    7 | A    | F      |     1 |
	|    7 | A    | M      |     2 |
	|    8 | A    | F      |     1 |
	|    8 | A    | M      |     1 |
	|    8 | B    | F      |     1 |
	|    8 | C    | F      |     1 |
	+------+------+--------+-------+

---3.Create a view of Test1 marks of student USN '1BI15CS101' in all subjects.---

CREATE VIEW STU_TEST1_MARKS_VIEW AS SELECT TEST1, SUBCODE
FROM IAMARKS WHERE USN='1RN13CS091';

SELECT * FROM STU_TEST1_MARKS_VIEW;

	+-------+---------+
	| TEST1 | SUBCODE |
	+-------+---------+
	|    15 | 10CS81  |
	|    12 | 10CS82  |
	|    19 | 10CS83  |
	|    20 | 10CS84  |
	|    15 | 10CS85  |
	+-------+---------+

---4.Calculate the FinalIA (average of best two test marks) and update the corresponding table for all students.---

DELIMITER //

CREATE PROCEDURE AVGMARKS(	)

BEGIN

DECLARE C_A INTEGER;
DECLARE C_B INTEGER;
DECLARE C_C INTEGER;
DECLARE C_SM INTEGER;
DECLARE C_AV INTEGER;
DECLARE C_USN VARCHAR(10);
DECLARE C_SUBCODE VARCHAR(10);
DECLARE C_SSID VARCHAR(10);

DECLARE C_IAMARKS CURSOR FOR
SELECT GREATEST(TEST1,TEST2) AS A, GREATEST(TEST1,TEST3) AS B,
GREATEST(TEST3,TEST2) AS C, USN, SUBCODE, SSID
FROM IAMARKS
WHERE FINALIA IS NULL
FOR UPDATE;

OPEN C_IAMARKS;
LOOP
FETCH C_IAMARKS INTO C_A,C_B,C_C,C_USN,C_SUBCODE,C_SSID;
IF(C_A!=C_B)THEN
	SET C_SM=C_A+C_B;
ELSE
	SET C_SM=C_A+C_C;
END IF;

SET C_AV=C_SM/2;

UPDATE IAMARKS SET FINALIA=C_AV
WHERE USN=C_USN AND SUBCODE=C_SUBCODE AND SSID=C_SSID;

END LOOP;
CLOSE C_IAMARKS;
END

//


SELECT * FROM IAMARKS;
	+------------+---------+-------+-------+-------+-------+---------+
	| USN        | SUBCODE | SSID  | TEST1 | TEST2 | TEST3 | FINALIA |
	+------------+---------+-------+-------+-------+-------+---------+
	| 1RN13CS091 | 10CS81  | CSE8C |    15 |    16 |    18 |    NULL |
	| 1RN13CS091 | 10CS82  | CSE8C |    12 |    19 |    14 |    NULL |
	| 1RN13CS091 | 10CS83  | CSE8C |    19 |    15 |    20 |    NULL |
	| 1RN13CS091 | 10CS84  | CSE8C |    20 |    16 |    19 |    NULL |
	| 1RN13CS091 | 10CS85  | CSE8C |    15 |    15 |    12 |    NULL |
	+------------+---------+-------+-------+-------+-------+---------+



DELIMITER ;
CALL AVGMARKS();

SELECT * FROM IAMARKS;

	+------------+---------+-------+-------+-------+-------+---------+
	| USN        | SUBCODE | SSID  | TEST1 | TEST2 | TEST3 | FINALIA |
	+------------+---------+-------+-------+-------+-------+---------+
	| 1RN13CS091 | 10CS81  | CSE8C |    15 |    16 |    18 |      17 |
	| 1RN13CS091 | 10CS82  | CSE8C |    12 |    19 |    14 |      17 |
	| 1RN13CS091 | 10CS83  | CSE8C |    19 |    15 |    20 |      20 |
	| 1RN13CS091 | 10CS84  | CSE8C |    20 |    16 |    19 |      20 |
	| 1RN13CS091 | 10CS85  | CSE8C |    15 |    15 |    12 |      15 |
	+------------+---------+-------+-------+-------+-------+---------+


---5.Categorize students based on the following criterion:---

SELECT
S.USN,S.SNAME,S.ADDRESS,S.PHONE,S.GENDER,
(CASE
WHEN IA.FINALIA BETWEEN 17 AND 20 THEN 'OUTSTANDING'
WHEN IA.FINALIA BETWEEN 12 AND 16 THEN 'AVERAGE' ELSE
'WEAK'
END)AS CAT
FROM STUDENT S,SEMSEC SS,IAMARKS IA,SUBJECT SUB
WHERE S.USN=IA.USN AND SS.SSID=IA.SSID AND SUB.SUBCODE=IA.SUBCODE AND SUB.SEM=8;

	+------------+--------+-----------+------------+--------+-------------+
	| USN        | SNAME  | ADDRESS   | PHONE      | GENDER | CAT         |
	+------------+--------+-----------+------------+--------+-------------+
	| 1RN13CS091 | TEESHA | BENGALURU | 7712312312 | F      | OUTSTANDING |
	| 1RN13CS091 | TEESHA | BENGALURU | 7712312312 | F      | OUTSTANDING |
	| 1RN13CS091 | TEESHA | BENGALURU | 7712312312 | F      | OUTSTANDING |
	| 1RN13CS091 | TEESHA | BENGALURU | 7712312312 | F      | OUTSTANDING |
	| 1RN13CS091 | TEESHA | BENGALURU | 7712312312 | F      | AVERAGE     |
	+------------+--------+-----------+------------+--------+-------------+

