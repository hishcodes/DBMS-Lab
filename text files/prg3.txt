CREATE DATABASE 20cs059_movie;


---Creating tables---
CREATE TABLE ACTOR(
ACT_ID INTEGER(3),
ACT_NAME VARCHAR(20),
ACT_GENDER CHAR(1),
PRIMARY KEY (ACT_ID));

CREATE TABLE DIRECTOR(
DIR_ID INTEGER(3),
DIR_NAME VARCHAR(20),
DIR_PHONE VARCHAR(10),
PRIMARY KEY (DIR_ID));

CREATE TABLE MOVIES(
MOV_ID INTEGER(4),
MOV_TITLE VARCHAR(25),
MOV_YEAR INTEGER(4),
MOV_LANG VARCHAR(12),
DIR_ID INTEGER(3),
PRIMARY KEY (MOV_ID),
FOREIGN KEY (DIR_ID) REFERENCES DIRECTOR(DIR_ID));

CREATE TABLE MOVIE_CAST(
ACT_ID INTEGER(3),
MOV_ID INTEGER(4),
ROLE VARCHAR(10),
PRIMARY KEY(ACT_ID, MOV_ID),
FOREIGN KEY (ACT_ID) REFERENCES ACTOR(ACT_ID),
FOREIGN KEY (MOV_ID) REFERENCES MOVIES (MOV_ID));

CREATE TABLE RATING(
MOV_ID INTEGER(4),
REV_STARS VARCHAR(25),
PRIMARY KEY(MOV_ID),
FOREIGN KEY(MOV_ID) REFERENCES MOVIES(MOV_ID));

---Describing tables---
DESC ACTOR;
	+------------+-------------+------+-----+---------+-------+
	| Field      | Type        | Null | Key | Default | Extra |
	+------------+-------------+------+-----+---------+-------+
	| ACT_ID     | int         | NO   | PRI | NULL    |       |
	| ACT_NAME   | varchar(20) | YES  |     | NULL    |       |
	| ACT_GENDER | char(1)     | YES  |     | NULL    |       |
	+------------+-------------+------+-----+---------+-------+

DESC DIRECTOR;
	+-----------+-------------+------+-----+---------+-------+
	| Field     | Type        | Null | Key | Default | Extra |
	+-----------+-------------+------+-----+---------+-------+
	| DIR_ID    | int         | NO   | PRI | NULL    |       |
	| DIR_NAME  | varchar(20) | YES  |     | NULL    |       |
	| DIR_PHONE | varchar(10) | YES  |     | NULL    |       |
	+-----------+-------------+------+-----+---------+-------+
	
DESC MOVIES;
	+-----------+-------------+------+-----+---------+-------+
	| Field     | Type        | Null | Key | Default | Extra |
	+-----------+-------------+------+-----+---------+-------+
	| MOV_ID    | int         | NO   | PRI | NULL    |       |
	| MOV_TITLE | varchar(25) | YES  |     | NULL    |       |
	| MOV_YEAR  | int         | YES  |     | NULL    |       |
	| MOV_LANG  | varchar(12) | YES  |     | NULL    |       |
	| DIR_ID    | int         | YES  | MUL | NULL    |       |
	+-----------+-------------+------+-----+---------+-------+

DESC MOVIE_CAST;
	+--------+-------------+------+-----+---------+-------+
	| Field  | Type        | Null | Key | Default | Extra |
	+--------+-------------+------+-----+---------+-------+
	| ACT_ID | int         | NO   | PRI | NULL    |       |
	| MOV_ID | int         | NO   | PRI | NULL    |       |
	| ROLE   | varchar(10) | YES  |     | NULL    |       |
	+--------+-------------+------+-----+---------+-------+

DESC RATING;
	+-----------+-------------+------+-----+---------+-------+
	| Field     | Type        | Null | Key | Default | Extra |
	+-----------+-------------+------+-----+---------+-------+
	| MOV_ID    | int         | NO   | PRI | NULL    |       |
	| REV_STARS | varchar(25) | YES  |     | NULL    |       |
	+-----------+-------------+------+-----+---------+-------+

INSERT INTO ACTOR VALUES(301,'ANUSHKA','F');
INSERT INTO ACTOR VALUES(302,'PRABHAS','M');
INSERT INTO ACTOR VALUES(303,'PUNITH','M');
INSERT INTO ACTOR VALUES(304,'JERMY','M');

INSERT INTO DIRECTOR VALUES(60,'RAJAMOULI',8751611001);
INSERT INTO DIRECTOR VALUES(61,'HITCHCOCK',7766138911);
INSERT INTO DIRECTOR VALUES(62,'FARAN',9986776531);
INSERT INTO DIRECTOR VALUES(63,'STEVEN SPIELBERG',8989776530);

INSERT INTO MOVIES VALUES(1001,'BAHUBALI-2',2017,'TELUGU',60);
INSERT INTO MOVIES VALUES(1002,'BAHUBALI-1',2015,'TELUGU',60);
INSERT INTO MOVIES VALUES(1003,'AKASH',2008,'KANNADA',61);
INSERT INTO MOVIES VALUES(1004,'WAR HORSE',2011,'ENGLISH',63);

INSERT INTO MOVIE_CAST VALUES(301,1002,'HEROINE');
INSERT INTO MOVIE_CAST VALUES(301,1001,'HEROINE');
INSERT INTO MOVIE_CAST VALUES(303,1003,'HERO');
INSERT INTO MOVIE_CAST VALUES(303,1002,'GUEST');
INSERT INTO MOVIE_CAST VALUES(304,1004,'HERO');

INSERT INTO RATING VALUES(1001,4);
INSERT INTO RATING VALUES(1002,2);
INSERT INTO RATING VALUES(1003,5);
INSERT INTO RATING VALUES(1004,4);

SELECT * FROM ACTOR;
	+--------+----------+------------+
	| ACT_ID | ACT_NAME | ACT_GENDER |
	+--------+----------+------------+
	|    301 | ANUSHKA  | F          |
	|    302 | PRABHAS  | M          |
	|    303 | PUNITH   | M          |
	|    304 | JERMY    | M          |
	+--------+----------+------------+

SELECT * FROM DIRECTOR;
	+--------+------------------+------------+
	| DIR_ID | DIR_NAME         | DIR_PHONE  |
	+--------+------------------+------------+
	|     60 | RAJAMOULI        | 8751611001 |
	|     61 | HITCHCOCK        | 7766138911 |
	|     62 | FARAN            | 9986776531 |
	|     63 | STEVEN SPIELBERG | 8989776530 |
	+--------+------------------+------------+

SELECT * FROM MOVIES;
	+--------+------------+----------+----------+--------+
	| MOV_ID | MOV_TITLE  | MOV_YEAR | MOV_LANG | DIR_ID |
	+--------+------------+----------+----------+--------+
	|   1001 | BAHUBALI-2 |     2017 | TELUGU   |     60 |
	|   1002 | BAHUBALI-1 |     2015 | TELUGU   |     60 |
	|   1003 | AKASH      |     2008 | KANNADA  |     61 |
	|   1004 | WAR HORSE  |     2011 | ENGLISH  |     63 |
	+--------+------------+----------+----------+--------+

SELECT * FROM MOVIE_CAST;
	+--------+--------+---------+
	| ACT_ID | MOV_ID | ROLE    |
	+--------+--------+---------+
	|    301 |   1001 | HEROINE |
	|    301 |   1002 | HEROINE |
	|    303 |   1002 | GUEST   |
	|    303 |   1003 | HERO    |
	|    304 |   1004 | HERO    |
	+--------+--------+---------+

SELECT * FROM RATING;
	+--------+-----------+
	| MOV_ID | REV_STARS |
	+--------+-----------+
	|   1001 | 4         |
	|   1002 | 2         |
	|   1003 | 5         |
	|   1004 | 4         |
	+--------+-----------+

---1. List the titles of all movies directed by 'Hitchcock'---

SELECT MOV_TITLE
FROM MOVIES
WHERE DIR_ID IN (SELECT DIR_ID
FROM DIRECTOR
WHERE DIR_NAME = 'HITCHCOCK');

	+-----------+
	| MOV_TITLE |
	+-----------+
	| AKASH     |
	+-----------+

---2.Find the movie names where one or more actors acted in two or more minutes---

SELECT MOV_TITLE
FROM MOVIES M,MOVIE_CAST MV
WHERE M.MOV_ID=MV.MOV_ID AND ACT_ID IN (SELECT ACT_ID
FROM MOVIE_CAST GROUP BY ACT_ID
HAVING COUNT(ACT_ID)>1)
GROUP BY MOV_TITLE
HAVING COUNT(*)>1;

	+------------+
	| MOV_TITLE  |
	+------------+
	| BAHUBALI-1 |
	+------------+

---3.List all actors who acted in a movie before 2000 and also in a movie after 2015---

SELECT A.ACT_NAME, A.ACT_NAME, C.MOV_TITLE, C.MOV_YEAR
FROM ACTOR A,MOVIE_CAST B,MOVIES C
WHERE A.ACT_ID=B.ACT_ID
AND B.MOV_ID=C.MOV_ID
AND C.MOV_YEAR NOT BETWEEN 2000 AND 2015;

	+----------+----------+------------+----------+
	| ACT_NAME | ACT_NAME | MOV_TITLE  | MOV_YEAR |
	+----------+----------+------------+----------+
	| ANUSHKA  | ANUSHKA  | BAHUBALI-2 |     2017 |
	+----------+----------+------------+----------+

---4.Find the title of movies and number of stars for each movie that has at least one rating and find the highest number of stars that movie received. Sort the result by movie title---

SELECT MOV_TITLE,MAX(REV_STARS)
FROM MOVIES
INNER JOIN RATING USING (MOV_ID)
GROUP BY MOV_TITLE
HAVING MAX(REV_STARS)>0
ORDER BY MOV_TITLE;

	+------------+----------------+
	| MOV_TITLE  | MAX(REV_STARS) |
	+------------+----------------+
	| AKASH      | 5              |
	| BAHUBALI-1 | 2              |
	| BAHUBALI-2 | 4              |
	| WAR HORSE  | 4              |
	+------------+----------------+
	
---5. ---

UPDATE RATING
SET REV_STARS=5
WHERE MOV_ID IN (SELECT MOV_ID FROM MOVIES
WHERE DIR_ID IN (SELECT DIR_ID
FROM DIRECTOR
WHERE DIR_NAME = 'STEVEN SPIELBERG'));

SELECT * FROM RATING;

	+--------+-----------+
	| MOV_ID | REV_STARS |
	+--------+-----------+
	|   1001 | 4         |
	|   1002 | 2         |
	|   1003 | 5         |
	|   1004 | 5         |
	+--------+-----------+


