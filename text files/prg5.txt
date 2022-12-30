CREATE DATABASE 20cs059_company;

USE 20cs059_company;

CREATE TABLE DEPARTMENT(
DNO VARCHAR(20) PRIMARY KEY,
DNAME VARCHAR(20),
MDRSTARTDATE DATE);

CREATE TABLE EMPLOYEE(
SSN VARCHAR(20) PRIMARY KEY,
FNAME VARCHAR(20),
LNAME VARCHAR(20),
ADDRESS VARCHAR(20),
SEX CHAR(1),
SALARY INTEGER,
SUPERSSN VARCHAR(20),
DNO VARCHAR(20),
FOREIGN KEY(SUPERSSN) REFERENCES EMPLOYEE(SSN),
FOREIGN KEY(DNO) REFERENCES DEPARTMENT(DNO));

ALTER TABLE DEPARTMENT ADD MGRSSN VARCHAR(20);
ALTER TABLE DEPARTMENT ADD FOREIGN KEY(MGRSSN) REFERENCES EMPLOYEE(SSN);

CREATE TABLE DLOCATION(
DLOC VARCHAR(20),
DNO VARCHAR(20),
FOREIGN KEY(DNO) REFERENCES DEPARTMENT(DNO),
PRIMARY KEY(DNO, DLOC));

CREATE TABLE PROJECT(
PNO INTEGER PRIMARY KEY,
PNAME VARCHAR(20),
PLOCATION VARCHAR(20),
DNO VARCHAR(20),
FOREIGN KEY(DNO) REFERENCES DEPARTMENT(DNO));

CREATE TABLE WORKS_ON(
HOURS INTEGER(2),
SSN VARCHAR(20),
FOREIGN KEY(SSN) REFERENCES EMPLOYEE(SSN),
PNO INTEGER,
FOREIGN KEY(PNO) REFERENCES PROJECT(PNO),
PRIMARY KEY(SSN, PNO));

DESC DEPARTMENT;
	+--------------+-------------+------+-----+---------+-------+
	| Field        | Type        | Null | Key | Default | Extra |
	+--------------+-------------+------+-----+---------+-------+
	| DNO          | varchar(20) | NO   | PRI | NULL    |       |
	| DNAME        | varchar(20) | YES  |     | NULL    |       |
	| MDRSTARTDATE | date        | YES  |     | NULL    |       |
	| MGRSSN       | varchar(20) | YES  | MUL | NULL    |       |
	+--------------+-------------+------+-----+---------+-------+


DESC DLOCATION;
	+-------+-------------+------+-----+---------+-------+
	| Field | Type        | Null | Key | Default | Extra |
	+-------+-------------+------+-----+---------+-------+
	| DLOC  | varchar(20) | NO   | PRI | NULL    |       |
	| DNO   | varchar(20) | NO   | PRI | NULL    |       |
	+-------+-------------+------+-----+---------+-------+


DESC EMPLOYEE;
	+----------+-------------+------+-----+---------+-------+
	| Field    | Type        | Null | Key | Default | Extra |
	+----------+-------------+------+-----+---------+-------+
	| SSN      | varchar(20) | NO   | PRI | NULL    |       |
	| FNAME    | varchar(20) | YES  |     | NULL    |       |
	| LNAME    | varchar(20) | YES  |     | NULL    |       |
	| ADDRESS  | varchar(20) | YES  |     | NULL    |       |
	| SEX      | char(1)     | YES  |     | NULL    |       |
	| SALARY   | int         | YES  |     | NULL    |       |
	| SUPERSSN | varchar(20) | YES  | MUL | NULL    |       |
	| DNO      | varchar(20) | YES  | MUL | NULL    |       |
	+----------+-------------+------+-----+---------+-------+


DESC PROJECT;
	+-----------+-------------+------+-----+---------+-------+
	| Field     | Type        | Null | Key | Default | Extra |
	+-----------+-------------+------+-----+---------+-------+
	| PNO       | int         | NO   | PRI | NULL    |       |
	| PNAME     | varchar(20) | YES  |     | NULL    |       |
	| PLOCATION | varchar(20) | YES  |     | NULL    |       |
	| DNO       | varchar(20) | YES  | MUL | NULL    |       |
	+-----------+-------------+------+-----+---------+-------+



DESC WORKS_ON;
	+-------+-------------+------+-----+---------+-------+
	| Field | Type        | Null | Key | Default | Extra |
	+-------+-------------+------+-----+---------+-------+
	| HOURS | int         | YES  |     | NULL    |       |
	| SSN   | varchar(20) | NO   | PRI | NULL    |       |
	| PNO   | int         | NO   | PRI | NULL    |       |
	+-------+-------------+------+-----+---------+-------+


INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSECE01','JOHN','SCOTT','BANAGALORE','M',450000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSCSE01','JAMES','SMITH','BANAGALORE','M',500000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSCSE02','HEARN','BAKER','BANAGALORE','M',700000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSCSE03','EDWARD','SCOTT','MYSORE','M',500000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSCSE04','PAVAN','HEGDE','MANAGALORE','M',650000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSCSE05','GIRISH','MALYA','MYSORE','M',450000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSCSE06','NEHA','SN','BANGALORE','F',800000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSACC01','AHANA','K','MANGALORE','F',350000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSACC02','SANTHOSH','KUMAR','MANGALORE','M',300000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSISE01','VEENA','M','MYSORE','M',600000);

INSERT INTO EMPLOYEE(SSN,FNAME,LNAME,ADDRESS,SEX,SALARY) VALUES('RNSIT01','NAGESH','HR','BANGALORE','M',500000);


INSERT INTO DEPARTMENT VALUES('1','ACCOUNTS','2001-01-01','RNSACC02');
INSERT INTO DEPARTMENT VALUES('2','IT','2016-08-01','RNSIT01');
INSERT INTO DEPARTMENT VALUES('3','ECE','2008-06-01','RNSECE01');
INSERT INTO DEPARTMENT VALUES('4','ISE','2015-08-01','RNSISE01');
INSERT INTO DEPARTMENT VALUES('5','CSE','2002-06-01','RNSCSE05');

UPDATE EMPLOYEE SET
SUPERSSN=NULL, DNO='3'
WHERE SSN='RNSECE01';

UPDATE EMPLOYEE SET
SUPERSSN='RNSCSE02', DNO='5'
WHERE SSN='RNSCSE01';

UPDATE EMPLOYEE SET
SUPERSSN='RNSCSE03', DNO='5'
WHERE SSN='RNSCSE02';

UPDATE EMPLOYEE SET
SUPERSSN='RNSCSE04', DNO='5'
WHERE SSN='RNSCSE03';

UPDATE EMPLOYEE SET
SUPERSSN='RNSCSE05', DNO='5'
WHERE SSN='RNSCSE04';

UPDATE EMPLOYEE SET
SUPERSSN='RNSCSE06', DNO='5'
WHERE SSN='RNSCSE05';

UPDATE EMPLOYEE SET
SUPERSSN=NULL, DNO='5'
WHERE SSN='RNSCSE06';

UPDATE EMPLOYEE SET
SUPERSSN='RNSACC02', DNO='1'
WHERE SSN='RNSACC01';

UPDATE EMPLOYEE SET
SUPERSSN=NULL, DNO='1'
WHERE SSN='RNSACC02';

UPDATE EMPLOYEE SET
SUPERSSN=NULL, DNO='4'
WHERE SSN='RNSISE01';

UPDATE EMPLOYEE SET
SUPERSSN=NULL, DNO='2'
WHERE SSN='RNSIT01';


INSERT INTO DLOCATION VALUES('BANGALORE','1');
INSERT INTO DLOCATION VALUES('BANGALORE','2');
INSERT INTO DLOCATION VALUES('BANGALORE','3');
INSERT INTO DLOCATION VALUES('MANGALORE','4');
INSERT INTO DLOCATION VALUES('MANGALORE','5');

INSERT INTO PROJECT VALUES(100,'IOT','BANGALORE','5');
INSERT INTO PROJECT VALUES(101,'CLOUD','BANGALORE','5');
INSERT INTO PROJECT VALUES(102,'BIGDATA','BANGALORE','5');
INSERT INTO PROJECT VALUES(103,'SENSORS','BANGALORE','3');
INSERT INTO PROJECT VALUES(104,'BANK MANAGEMENT','BANGALORE','1');
INSERT INTO PROJECT VALUES(105,'SALARY MANAGEMENT','BANGALORE','1');
INSERT INTO PROJECT VALUES(106,'OPENSTACK','BANGALORE','4');
INSERT INTO PROJECT VALUES(107,'SMART CITY','BANGALORE','2');

INSERT INTO WORKS_ON VALUES(4,'RNSCSE01',100);
INSERT INTO WORKS_ON VALUES(6,'RNSCSE01',101);
INSERT INTO WORKS_ON VALUES(7,'RNSCSE01',102);
INSERT INTO WORKS_ON VALUES(10,'RNSCSE02',100);
INSERT INTO WORKS_ON VALUES(3,'RNSCSE04',100);
INSERT INTO WORKS_ON VALUES(4,'RNSCSE05',101);
INSERT INTO WORKS_ON VALUES(5,'RNSCSE06',102);
INSERT INTO WORKS_ON VALUES(6,'RNSCSE03',102);
INSERT INTO WORKS_ON VALUES(7,'RNSCSE01',103);
INSERT INTO WORKS_ON VALUES(5,'RNSACC01',104);
INSERT INTO WORKS_ON VALUES(6,'RNSACC02',105);
INSERT INTO WORKS_ON VALUES(4,'RNSISE01',106);
INSERT INTO WORKS_ON VALUES(10,'RNSIT01',107);

SELECT * FROM EMPLOYEE;

	+----------+----------+-------+------------+------+--------+----------+------+
	| SSN      | FNAME    | LNAME | ADDRESS    | SEX  | SALARY | SUPERSSN | DNO  |
	+----------+----------+-------+------------+------+--------+----------+------+
	| RNSACC01 | AHANA    | K     | MANGALORE  | F    | 350000 | RNSACC02 | 1    |
	| RNSACC02 | SANTHOSH | KUMAR | MANGALORE  | M    | 300000 | NULL     | 1    |
	| RNSCSE01 | JAMES    | SMITH | BANAGALORE | M    | 500000 | RNSCSE02 | 5    |
	| RNSCSE02 | HEARN    | BAKER | BANAGALORE | M    | 700000 | RNSCSE03 | 5    |
	| RNSCSE03 | EDWARD   | SCOTT | MYSORE     | M    | 500000 | RNSCSE04 | 5    |
	| RNSCSE04 | PAVAN    | HEGDE | MANAGALORE | M    | 650000 | RNSCSE05 | 5    |
	| RNSCSE05 | GIRISH   | MALYA | MYSORE     | M    | 450000 | RNSCSE06 | 5    |
	| RNSCSE06 | NEHA     | SN    | BANGALORE  | F    | 800000 | NULL     | 5    |
	| RNSECE01 | JOHN     | SCOTT | BANAGALORE | M    | 450000 | NULL     | 3    |
	| RNSISE01 | VEENA    | M     | MYSORE     | M    | 600000 | NULL     | 4    |
	| RNSIT01  | NAGESH   | HR    | BANGALORE  | M    | 500000 | NULL     | 2    |
	+----------+----------+-------+------------+------+--------+----------+------+


SELECT * FROM DEPARTMENT;

	+-----+----------+--------------+----------+
	| DNO | DNAME    | MDRSTARTDATE | MGRSSN   |
	+-----+----------+--------------+----------+
	| 1   | ACCOUNTS | 2001-01-01   | RNSACC02 |
	| 2   | IT       | 2016-08-01   | RNSIT01  |
	| 3   | ECE      | 2008-06-01   | RNSECE01 |
	| 4   | ISE      | 2015-08-01   | RNSISE01 |
	| 5   | CSE      | 2002-06-01   | RNSCSE05 |
	+-----+----------+--------------+----------+

SELECT * FROM DLOCATION;

	+-----------+-----+
	| DLOC      | DNO |
	+-----------+-----+
	| BANGALORE | 1   |
	| BANGALORE | 2   |
	| BANGALORE | 3   |
	| MANGALORE | 4   |
	| MANGALORE | 5   |
	+-----------+-----+

SELECT * FROM PROJECT;

	+-----+-------------------+-----------+------+
	| PNO | PNAME             | PLOCATION | DNO  |
	+-----+-------------------+-----------+------+
	| 100 | IOT               | BANGALORE | 5    |
	| 101 | CLOUD             | BANGALORE | 5    |
	| 102 | BIGDATA           | BANGALORE | 5    |
	| 103 | SENSORS           | BANGALORE | 3    |
	| 104 | BANK MANAGEMENT   | BANGALORE | 1    |
	| 105 | SALARY MANAGEMENT | BANGALORE | 1    |
	| 106 | OPENSTACK         | BANGALORE | 4    |
	| 107 | SMART CITY        | BANGALORE | 2    |
	+-----+-------------------+-----------+------+

SELECT * FROM WORKS_ON;

	+-------+----------+-----+
	| HOURS | SSN      | PNO |
	+-------+----------+-----+
	|     5 | RNSACC01 | 104 |
	|     6 | RNSACC02 | 105 |
	|     4 | RNSCSE01 | 100 |
	|     6 | RNSCSE01 | 101 |
	|     7 | RNSCSE01 | 102 |
	|     7 | RNSCSE01 | 103 |
	|    10 | RNSCSE02 | 100 |
	|     6 | RNSCSE03 | 102 |
	|     3 | RNSCSE04 | 100 |
	|     4 | RNSCSE05 | 101 |
	|     5 | RNSCSE06 | 102 |
	|     4 | RNSISE01 | 106 |
	|    10 | RNSIT01  | 107 |
	+-------+----------+-----+


---Queries---
---1. Make a list of all project numbers for projects that involve an employee whose last name is 'Scott', either as a worker or as a manager of the department that controls the project.---

(SELECT DISTINCT P.PNO
FROM PROJECT P, DEPARTMENT D, EMPLOYEE E
WHERE P.DNO=D.DNO AND D.MGRSSN=E.SSN AND E.LNAME='SCOTT')
UNION
(SELECT DISTINCT P1.PNO
FROM PROJECT P1, WORKS_ON W, EMPLOYEE E1
WHERE P1.PNO=W.PNO AND W.SSN=E1.SSN AND E1.LNAME='SCOTT');

	+-----+
	| PNO |
	+-----+
	| 103 |
	| 102 |
	+-----+

---2.Show the resulting salaries if every employee working on the 'IoT' project is given a 10 percent raise.---

SELECT E.FNAME, E.LNAME, 1.1*E.SALARY AS INCR_SAL
FROM EMPLOYEE E, WORKS_ON W, PROJECT P
WHERE E.SSN=W.SSN
AND W.PNO=P.PNO
AND P.PNAME='IOT';

	+-------+-------+----------+
	| FNAME | LNAME | INCR_SAL |
	+-------+-------+----------+
	| JAMES | SMITH | 550000.0 |
	| HEARN | BAKER | 770000.0 |
	| PAVAN | HEGDE | 715000.0 |
	+-------+-------+----------+

---3.Find the sum of the salaries of all employees of the 'Accounts' department, as well as the maximum salary, the minimum salary, and the average salary in this department.--

SELECT SUM(E.SALARY), MAX(E.SALARY), MIN(E.SALARY), AVG(E.SALARY)
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DNO=D.DNO AND D.DNAME='ACCOUNTS';

	+---------------+---------------+---------------+---------------+
	| SUM(E.SALARY) | MAX(E.SALARY) | MIN(E.SALARY) | AVG(E.SALARY) |
	+---------------+---------------+---------------+---------------+
	|        650000 |        350000 |        300000 |   325000.0000 |
	+---------------+---------------+---------------+---------------+

---4.Retrieve the name of the salaries of all employees who works in all the projects controlled by department number 5.---

SELECT E.FNAME, E.LNAME
FROM EMPLOYEE E
WHERE NOT EXISTS
(SELECT PNO
FROM PROJECT
WHERE DNO='5' AND
PNO NOT IN (SELECT PNO
FROM WORKS_ON
WHERE E.SSN=SSN));

	+-------+-------+
	| FNAME | LNAME |
	+-------+-------+
	| JAMES | SMITH |
	+-------+-------+

---5. For each department that has more than five employees, retreive the department number and the number of its employees who are making more than Rs. 6,00,000.---

SELECT D.DNO, COUNT(*)
FROM DEPARTMENT D, EMPLOYEE E
WHERE D.DNO=E.DNO AND E.SALARY>600000 AND D.DNO IN
(
SELECT E1.DNO
FROM EMPLOYEE E1
GROUP BY E1.DNO
HAVING COUNT(*)>5
)
GROUP BY D.DNO;

	+-----+----------+
	| DNO | COUNT(*) |
	+-----+----------+
	| 5   |        3 |
	+-----+----------+

