---
### 1) mysql> Select * from EMPLOYEE; 

+----------+-------+---------+-----------+------------+--------------------------+-----+----------+-----------+-----+ 

| FNAME    | MINIT | LNAME   | SSN       | BDATE      | ADDRESS                  | SEX | SALARY   | SUPERSSN  | DNO | 

+----------+-------+---------+-----------+------------+--------------------------+-----+----------+-----------+-----+ 

| John     | B     | Smith   | 123456789 | 1965-01-09 | 731 Fondren, Houston, TX | M   | 30000.00 | 333445555 |   5 | 

| Franklin | T     | Wong    | 333445555 | 1955-12-08 | 638 Voss, Houston, TX    | M   | 40000.00 | 888665555 |   5 | 

| Joyce    | A     | English | 453453453 | 1972-07-31 | 5631 Rice, Houston, TX   | F   | 25000.00 | 333445555 |   5 | 

| Ramesh   | K     | Narayan | 666884444 | 1962-09-15 | 975 Fire Oak, Humble, TX | M   | 38000.00 | 333445555 |   5 | 

| James    | E     | Brog    | 888665555 | 1937-11-10 | 450 Stone, Houston, TX   | M   | 55000.00 | NULL      |   1 | 

| Jennifer | S     | Wallace | 987654321 | 1941-06-20 | 291 Berry, Bellaire, TX  | F   | 43000.00 | 888665555 |   4 | 

| Ahmad    | V     | Jabbar  | 987987987 | 1969-03-29 | 980 Dallas, Houston, TX  | M   | 25000.00 | 987654321 |   4 | 

| Alicia   | J     | Zelaya  | 999887777 | 1968-01-19 | 3321 Castle, Spring, TX  | F   | 25000.00 | 987654321 |   4 | 

+----------+-------+---------+-----------+------------+--------------------------+-----+----------+-----------+-----+ 

8 rows in set (0.00 sec) 

 

---
### 2) mysql> SELECT SSN,LNAME,FNAME,ADDRESS FROM EMPLOYEE WHERE DNO=7; 

Empty set (0.04 sec) 

 

---
### 3) mysql> SELECT BDATE,ADDRESS FROM EMPLOYEE WHERE FNAME="Franklin" AND MINIT="T" AND LNAME="Wong" 

    -> ; 

+------------+-----------------------+ 

| BDATE      | ADDRESS               | 

+------------+-----------------------+ 

| 1955-12-08 | 638 Voss, Houston, TX | 

+------------+-----------------------+ 

1 row in set (0.00 sec) 

 

---
### 4) mysql> SELECT FNAME,MINIT,LNAME,SALARY FROM EMPLOYEE; 

+----------+-------+---------+----------+ 

| FNAME    | MINIT | LNAME   | SALARY   | 

+----------+-------+---------+----------+ 

| John     | B     | Smith   | 30000.00 | 

| Franklin | T     | Wong    | 40000.00 | 

| Joyce    | A     | English | 25000.00 | 

| Ramesh   | K     | Narayan | 38000.00 | 

| James    | E     | Brog    | 55000.00 | 

| Jennifer | S     | Wallace | 43000.00 | 

| Ahmad    | V     | Jabbar  | 25000.00 | 

| Alicia   | J     | Zelaya  | 25000.00 | 

+----------+-------+---------+----------+ 

8 rows in set (0.00 sec) 

 

---
### 5) mysql> SELECT DISTINCT SALARY FROM EMPLOYEE; 

+----------+ 

| SALARY   | 

+----------+ 

| 30000.00 | 

| 40000.00 | 

| 25000.00 | 

| 38000.00 | 

| 55000.00 | 

| 43000.00 | 

+----------+ 

6 rows in set (0.04 sec) 

 

---
### 6) mysql> SELECT FNAME,MINIT,LNAME FROM EMPLOYEE WHERE ADDRESS LIKE "%Bellaire%"; 

+----------+-------+---------+ 

| FNAME    | MINIT | LNAME   | 

+----------+-------+---------+ 

| Jennifer | S     | Wallace | 

+----------+-------+---------+ 

1 row in set (0.00 sec) 

 

---
### 7) mysql> SELECT * FROM EMPLOYEE WHERE BDATE BETWEEN "1950-01-01" AND "1959-12-31"; 

+----------+-------+-------+-----------+------------+-----------------------+-----+----------+-----------+-----+ 

| FNAME    | MINIT | LNAME | SSN       | BDATE      | ADDRESS               | SEX | SALARY   | SUPERSSN  | DNO | 

+----------+-------+-------+-----------+------------+-----------------------+-----+----------+-----------+-----+ 

| Franklin | T     | Wong  | 333445555 | 1955-12-08 | 638 Voss, Houston, TX | M   | 40000.00 | 888665555 |   5 | 

+----------+-------+-------+-----------+------------+-----------------------+-----+----------+-----------+-----+ 

1 row in set (0.00 sec) 

 

---
### 8) mysql> SELECT * FROM EMPLOYEE WHERE DNO=5 AND SALARY BETWEEN 50000 AND 60000; 

Empty set (0.00 sec) 

 

---
### 9) mysql> SELECT FNAME,MINIT,LNAME FROM EMPLOYEE WHERE SUPERSSN IS NULL; 

+-------+-------+-------+ 

| FNAME | MINIT | LNAME | 

+-------+-------+-------+ 

| James | E     | Brog  | 

+-------+-------+-------+ 

1 row in set (0.00 sec) 

 

---
### 10) mysql> SELECT SSN,DNAME FROM EMPLOYEE,DEPARTMENT WHERE DNO=DNUMBER; 

+-----------+----------------+ 

| SSN       | DNAME          | 

+-----------+----------------+ 

| 888665555 | Headquarters   | 

| 987654321 | Administration | 

| 987987987 | Administration | 

| 999887777 | Administration | 

| 123456789 | Research       | 

| 333445555 | Research       | 

| 453453453 | Research       | 

| 666884444 | Research       | 

+-----------+----------------+ 

8 rows in set (0.04 sec) 

 

---
### 11) mysql> SELECT FNAME,MINIT,LNAME,ADDRESS FROM EMPLOYEE,DEPARTMENT WHERE DNO=DNUMBER AND DNAME="Research"; 

+----------+-------+---------+--------------------------+ 

| FNAME    | MINIT | LNAME   | ADDRESS                  | 

+----------+-------+---------+--------------------------+ 

| John     | B     | Smith   | 731 Fondren, Houston, TX | 

| Franklin | T     | Wong    | 638 Voss, Houston, TX    | 

| Joyce    | A     | English | 5631 Rice, Houston, TX   | 

| Ramesh   | K     | Narayan | 975 Fire Oak, Humble, TX | 

+----------+-------+---------+--------------------------+ 

4 rows in set (0.00 sec) 

 

---
### 12) mysql> SELECT P.PNUMBER,P.DNUM,E.LNAME,E.ADDRESS,E.BDATE FROM PROJECT P,EMPLOYEE E,DEPARTMENT D WHERE P.PLOCATION="Stafford" AND P.DNUM=D.DNUMBER AND D.MGRSSN=E.SSN; 

+---------+------+---------+-------------------------+------------+ 

| PNUMBER | DNUM | LNAME   | ADDRESS                 | BDATE      | 

+---------+------+---------+-------------------------+------------+ 

|      10 |    4 | Wallace | 291 Berry, Bellaire, TX | 1941-06-20 | 

|      30 |    4 | Wallace | 291 Berry, Bellaire, TX | 1941-06-20 | 

+---------+------+---------+-------------------------+------------+ 

2 rows in set (0.00 sec) 

 

---
### 13) mysql> SELECT R.FNAME,R.MINIT,R.LNAME,R1.FNAME,R1.MINIT,R1.LNAME FROM EMPLOYEE R,EMPLOYEE R1 WHERE R.SUPERSSN=R1.SSN; 

+----------+-------+---------+----------+-------+---------+ 

| FNAME    | MINIT | LNAME   | FNAME    | MINIT | LNAME   | 

+----------+-------+---------+----------+-------+---------+ 

| John     | B     | Smith   | Franklin | T     | Wong    | 

| Franklin | T     | Wong    | James    | E     | Brog    | 

| Joyce    | A     | English | Franklin | T     | Wong    | 

| Ramesh   | K     | Narayan | Franklin | T     | Wong    | 

| Jennifer | S     | Wallace | James    | E     | Brog    | 

| Ahmad    | V     | Jabbar  | Jennifer | S     | Wallace | 

| Alicia   | J     | Zelaya  | Jennifer | S     | Wallace | 

+----------+-------+---------+----------+-------+---------+ 

7 rows in set (0.00 sec) 

 

---
### 14) mysql> SELECT FNAME,MINIT,LNAME,DNAME FROM EMPLOYEE,DEPARTMENT; 

+----------+-------+---------+----------------+ 

| FNAME    | MINIT | LNAME   | DNAME          | 

+----------+-------+---------+----------------+ 

| John     | B     | Smith   | Research       | 

| John     | B     | Smith   | Administration | 

| John     | B     | Smith   | Headquarters   | 

| Franklin | T     | Wong    | Research       | 

| Franklin | T     | Wong    | Administration | 

| Franklin | T     | Wong    | Headquarters   | 

| Joyce    | A     | English | Research       | 

| Joyce    | A     | English | Administration | 

| Joyce    | A     | English | Headquarters   | 

| Ramesh   | K     | Narayan | Research       | 

| Ramesh   | K     | Narayan | Administration | 

| Ramesh   | K     | Narayan | Headquarters   | 

| James    | E     | Brog    | Research       | 

| James    | E     | Brog    | Administration | 

| James    | E     | Brog    | Headquarters   | 

| Jennifer | S     | Wallace | Research       | 

| Jennifer | S     | Wallace | Administration | 

| Jennifer | S     | Wallace | Headquarters   | 

| Ahmad    | V     | Jabbar  | Research       | 

| Ahmad    | V     | Jabbar  | Administration | 

| Ahmad    | V     | Jabbar  | Headquarters   | 

| Alicia   | J     | Zelaya  | Research       | 

| Alicia   | J     | Zelaya  | Administration | 

| Alicia   | J     | Zelaya  | Headquarters   | 

+----------+-------+---------+----------------+ 

24 rows in set (0.00 sec) 

 

---
### 15) mysql> (SELECT W.PNO FROM EMPLOYEE E,WORKS_ON W WHERE W.ESSN=E.SSN AND E.LNAME="Narayan") UNION (SELECT P.PNUMBER FROM PROJECT P,DEPARTMENT D,EMPLOYEE E WHERE P.DNUM=D.DNUMBER AND E.SSN=D.MGRSSN AND E.LNAME="Narayan"); 

+-----+ 

| PNO | 

+-----+ 

|   3 | 

+-----+ 

1 row in set (0.04 sec) 

 

---
### 16) mysql> UPDATE EMPLOYEE E,PROJECT P,WORKS_ON W SET E.SALARY=E.SALARY+(.15*E.SALARY) WHERE W.ESSN=E.SSN AND W.PNO=P.PNUMBER AND P.PNAME="ProductX"; 

Query OK, 2 rows affected (0.05 sec) 

Rows matched: 2  Changed: 2  Warnings: 0 

  

### mysql> SELECT FNAME,MINIT,LNAME,SALARY FROM EMPLOYEE,WORKS_ON,PROJECT WHERE PNAME="ProductX" AND PNO=PNUMBER AND ESSN=SSN; 

+-------+-------+---------+----------+ 

| FNAME | MINIT | LNAME   | SALARY   | 

+-------+-------+---------+----------+ 

| John  | B     | Smith   | 34500.00 | 

| Joyce | A     | English | 28750.00 | 

+-------+-------+---------+----------+ 

2 rows in set (0.00 sec) 

 

## OR 

 

### mysql> SELECT FNAME,MINIT,LNAME,1.15*SALARY AS INCREASED_SALARY FROM EMPLOYEE,WORKS_ON,PROJECT WHERE SSN=ESSN AND PNO=PNUMBER AND PNAME="ProductX"; 

+-------+-------+---------+------------------+ 

| FNAME | MINIT | LNAME   | INCREASED_SALARY | 

+-------+-------+---------+------------------+ 

| John  | B     | Smith   |       34500.0000 | 

| Joyce | A     | English |       28750.0000 | 

+-------+-------+---------+------------------+ 

2 rows in set (0.00 sec) 

 

---
### 17) mysql> SELECT E.FNAME,E.MINIT,E.LNAME,P.PNAME FROM EMPLOYEE E,PROJECT P,WORKS_ON W WHERE E.SSN=W.ESSN AND W.PNO=P.PNUMBER ORDER BY E.DNO,E.FNAME ASC; 

+----------+-------+---------+-----------------+ 

| FNAME    | MINIT | LNAME   | PNAME           | 

+----------+-------+---------+-----------------+ 

| James    | E     | Brog    | Reorganization  | 

| Ahmad    | V     | Jabbar  | Computerization | 

| Ahmad    | V     | Jabbar  | Newbenefits     | 

| Alicia   | J     | Zelaya  | Computerization | 

| Alicia   | J     | Zelaya  | Newbenefits     | 

| Jennifer | S     | Wallace | Reorganization  | 

| Jennifer | S     | Wallace | Newbenefits     | 

| Franklin | T     | Wong    | ProductY        | 

| Franklin | T     | Wong    | ProductZ        | 

| Franklin | T     | Wong    | Computerization | 

| Franklin | T     | Wong    | Reorganization  | 

| John     | B     | Smith   | ProductX        | 

| John     | B     | Smith   | ProductY        | 

| Joyce    | A     | English | ProductX        | 

| Joyce    | A     | English | ProductY        | 

| Ramesh   | K     | Narayan | ProductZ        | 

+----------+-------+---------+-----------------+ 

16 rows in set (0.00 sec) 

 

---
### 18) mysql> SELECT FNAME,MINIT,LNAME FROM EMPLOYEE WHERE SALARY NOT IN (SELECT SALARY FROM EMPLOYEE WHERE DNO=10); 

+----------+-------+---------+ 

| FNAME    | MINIT | LNAME   | 

+----------+-------+---------+ 

| John     | B     | Smith   | 

| Franklin | T     | Wong    | 

| Joyce    | A     | English | 

| Ramesh   | K     | Narayan | 

| James    | E     | Brog    | 

| Jennifer | S     | Wallace | 

| Ahmad    | V     | Jabbar  | 

| Alicia   | J     | Zelaya  | 

+----------+-------+---------+ 

8 rows in set (0.00 sec) 

 

---
### 19) mysql> SELECT E.FNAME,E.MINIT,E.LNAME FROM EMPLOYEE E,DEPENDENT D WHERE E.SSN=D.ESSN AND E.FNAME=D.DEPENDENT_NAME AND E.SEX=D.SEX; 

Empty set (0.00 sec) 

 

---
### 20) mysql> SELECT DISTINCT ESSN AS SSN_OF_EMPLOYEES_WORKING_IN_GIVEN_LOCATIONS FROM WORKS_ON,PROJECT WHERE PNO=PNUMBER AND PLOCATION="Bellaire" OR PLOCATION="Houston" OR PLOCATION="Stafford"; 

+---------------------------------------------+ 

| SSN_OF_EMPLOYEES_WORKING_IN_GIVEN_LOCATIONS | 

+---------------------------------------------+ 

| 123456789                                   | 

| 453453453                                   | 

| 333445555                                   | 

| 666884444                                   | 

| 987987987                                   | 

| 999887777                                   | 

| 888665555                                   | 

| 987654321                                   | 

+---------------------------------------------+ 

8 rows in set (0.00 sec) 

 

---
### 21) mysql> SELECT SUM(SALARY) AS TOTAL_SALARY,MAX(SALARY) AS MAXIMUM_SALARY,MIN(SALARY) AS MINIMUM_SALARY,AVG(SALARY) AS AVERAGE_SALARY FROM EMPLOYEE; 

+--------------+----------------+----------------+----------------+ 

| TOTAL_SALARY | MAXIMUM_SALARY | MINIMUM_SALARY | AVERAGE_SALARY | 

+--------------+----------------+----------------+----------------+ 

|    281000.00 |       55000.00 |       25000.00 |   35125.000000 | 

+--------------+----------------+----------------+----------------+ 

1 row in set (0.00 sec) 

 

---
### 22) mysql> SELECT SUM(SALARY) AS TOTAL_SALARY,COUNT(SSN) AS NUMBER_OF_EMPLOYEES,MAX(SALARY) AS MAXIMUM_SALARY,MIN(SALARY) AS MINIMUM_SALARY,AVG(SALARY) AS AVERAGE_SALARY FROM EMPLOYEE,DEPARTMENT WHERE DNO=DNUMBER AND DNAME="Marketing"; 

+--------------+---------------------+----------------+----------------+----------------+ 

| TOTAL_SALARY | NUMBER_OF_EMPLOYEES | MAXIMUM_SALARY | MINIMUM_SALARY | AVERAGE_SALARY | 

+--------------+---------------------+----------------+----------------+----------------+ 

|         NULL |                   0 |           NULL |           NULL |           NULL | 

+--------------+---------------------+----------------+----------------+----------------+ 

1 row in set (0.00 sec) 

 

--- 
### 23) mysql> SELECT FNAME,MINIT,LNAME FROM EMPLOYEE WHERE SALARY>(SELECT AVG(SALARY) FROM EMPLOYEE WHERE DNO=10); 

Empty set (0.00 sec) 

 

---
### 24) mysql> SELECT DNO,COUNT(SSN),AVG(SALARY) FROM EMPLOYEE GROUP BY DNO; 

+-----+------------+--------------+ 

| DNO | COUNT(SSN) | AVG(SALARY)  | 

+-----+------------+--------------+ 

|   1 |          1 | 55000.000000 | 

|   4 |          3 | 31000.000000 | 

|   5 |          4 | 33250.000000 | 

+-----+------------+--------------+ 

3 rows in set (0.00 sec) 

 

---
### 25) mysql> SELECT PNUMBER,PNAME,COUNT(ESSN) FROM PROJECT,WORKS_ON WHERE PNO=PNUMBER GROUP BY PNUMBER; 

+---------+-----------------+-------------+ 

| PNUMBER | PNAME           | COUNT(ESSN) | 

+---------+-----------------+-------------+ 

|       1 | ProductX        |           2 | 

|       2 | ProductY        |           3 | 

|       3 | ProductZ        |           2 | 

|      10 | Computerization |           3 | 

|      20 | Reorganization  |           3 | 

|      30 | Newbenefits     |           3 | 

+---------+-----------------+-------------+ 

6 rows in set (0.00 sec) 

 

---
### 26) mysql> UPDATE PROJECT SET PLOCATION="Bellaire",DNUM=6 WHERE (SELECT COUNT(ESSN) FROM WORKS_ON WHERE PNO=PNUMBER)>5; 

Query OK, 0 rows affected (0.00 sec) 

Rows matched: 0  Changed: 0  Warnings: 0 

 

---
### 27) mysql> SELECT DNO,NO_OF_EMPLOYEE FROM (SELECT DNO,COUNT(SSN) AS NO_OF_EMPLOYEE FROM EMPLOYEE WHERE SALARY>40000 GROUP BY DNO) E1 HAVING NO_OF_EMPLOYEE>0; 

+-----+----------------+ 

| DNO | NO_OF_EMPLOYEE | 

+-----+----------------+ 

|   1 |              1 | 

|   4 |              1 | 

+-----+----------------+ 

2 rows in set (0.00 sec) 

 

 

---
### 28) mysql> INSERT INTO PROJECT VALUES("TECH",7,"NEW YORK",10); 

ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`company`.`project`, CONSTRAINT `FK_DNO2` FOREIGN KEY (`DNUM`) REFERENCES `department` (`DNUMBER`)) 

 

### mysql> INSERT INTO DEPARTMENT VALUES("TECH",10,"123456789","1996-02-13"); 

Query OK, 1 row affected (0.04 sec) 

 

### mysql> INSERT INTO PROJECT VALUES("TECH",7,"NEW YORK",10); 

Query OK, 1 row affected (0.03 sec) 

 

### mysql> SELECT * FROM PROJECT; 

+-----------------+---------+-----------+------+ 

| PNAME           | PNUMBER | PLOCATION | DNUM | 

+-----------------+---------+-----------+------+ 

| ProductX        |       1 | Bellaire  |    5 | 

| ProductY        |       2 | Sugarland |    5 | 

| ProductZ        |       3 | Houston   |    5 | 

| TECH            |       7 | NEW YORK  |   10 | 

| Computerization |      10 | Stafford  |    4 | 

| Reorganization  |      20 | Houston   |    1 | 

| Newbenefits     |      30 | Stafford  |    4 | 

+-----------------+---------+-----------+------+ 

7 rows in set (0.00 sec) 

  

### mysql> SELECT * FROM DEPARTMENT; 

+----------------+---------+-----------+--------------+ 

| DNAME          | DNUMBER | MGRSSN    | MGRSTARTDATE | 

+----------------+---------+-----------+--------------+ 

| Headquarters   |       1 | 888665555 | 1981-06-19   | 

| Administration |       4 | 987654321 | 1995-01-01   | 

| Research       |       5 | 333445555 | 1988-05-22   | 

| TECH           |      10 | 123456789 | 1996-02-13   | 

+----------------+---------+-----------+--------------+ 

4 rows in set (0.00 sec) 

 

 

---
### 29) mysql> DELETE FROM DEPENDENT WHERE ESSN="123456789"; 

Query OK, 3 rows affected (0.00 sec) 

  

### mysql> SELECT * FROM DEPENDENT; 

+-----------+----------------+-----+------------+--------------+ 

| ESSN      | DEPENDENT_NAME | SEX | BDATE      | RELATIONSHIP | 

+-----------+----------------+-----+------------+--------------+ 

| 333445555 | Alice          | F   | 1986-04-05 | Daughter     | 

| 333445555 | Joy            | F   | 1958-05-03 | Spouse       | 

| 333445555 | Theodore       | M   | 1983-10-25 | Son          | 

| 987654321 | Abner          | M   | 1942-02-28 | Spouse       | 

+-----------+----------------+-----+------------+--------------+ 

4 rows in set (0.00 sec) 

 

---
### 30)  

 

 

---
### 31) mysql> ALTER TABLE EMPLOYEE ADD PNO INT NOT NULL; 

Query OK, 0 rows affected (0.07 sec) 

Records: 0  Duplicates: 0  Warnings: 0 

 

### mysql> UPDATE EMPLOYEE SET PNO=1; 

Query OK, 8 rows affected (0.04 sec) 

Rows matched: 8  Changed: 8  Warnings: 0 

  

### mysql> ALTER TABLE EMPLOYEE ADD CONSTRAINT FK_PN FOREIGN KEY (PNO) REFERENCES PROJECT(PNUMBER); 

Query OK, 8 rows affected (0.17 sec) 

Records: 8  Duplicates: 0  Warnings: 0 

 

### mysql> ALTER TABLE EMPLOYEE DROP FOREIGN KEY FK_PN; 

Query OK, 0 rows affected (0.02 sec) 

Records: 0  Duplicates: 0  Warnings: 0 

 

### mysql> ALTER TABLE EMPLOYEE DROP COLUMN PNO; 

Query OK, 0 rows affected (0.07 sec) 

Records: 0  Duplicates: 0  Warnings: 0 
