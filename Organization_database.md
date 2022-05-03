---
### 1) mysql> SELECT eno,ename,job_type,hire_date FROM EMPLOYEE; 

+-----+--------+--------------------+------------+ 

| eno | ename  | job_type           | hire_date  | 

+-----+--------+--------------------+------------+ 

| 1   | Karan  | CEO                | 2019-01-16 | 

| 26  | Aditya | Software Testing   | 2020-11-28 | 

| 5   | Kundan | Manager            | 2019-02-27 | 

| 58  | Harsh  | HR                 | 2022-01-16 | 

| 59  | Kapil  | Software Developer | 2019-12-26 | 

+-----+--------+--------------------+------------+ 

5 rows in set (0.00 sec) 

---
### 2) mysql> SELECT DISTINCT job_type FROM EMPLOYEE; 

+--------------------+ 

| job_type           | 

+--------------------+ 

| CEO                | 

| Software Testing   | 

| Manager            | 

| HR                 | 

| Software Developer | 

+--------------------+ 

5 rows in set (0.00 sec) 

---
### 3) mysql> SELECT CONCAT(ename,",",job_type) AS EMPLOYEE_JOB FROM EMPLOYEE; 

+--------------------------+ 

| EMPLOYEE_JOB             | 

+--------------------------+ 

| Karan,CEO                | 

| Aditya,Software Testing  | 

| Kundan,Manager           | 

| Harsh,HR                 | 

| Kapil,Software Developer | 

+--------------------------+ 

5 rows in set (0.00 sec) 

---
### 4) mysql> SELECT CONCAT(eno,",",ename,",",job_type,",",COALESCE(manager,"NULL"),",",hire_date,",",dno,",",commission,",",salary) AS THE_OUTPUT FROM EMPLOYEE; 

+------------------------------------------------------------------+ 

| THE_OUTPUT                                                       | 

+------------------------------------------------------------------+ 

| 1,Karan,CEO,NULL,2019-01-16,56,800000.00,99999.90                | 

| 26,Aditya,Software Testing,NULL,2020-11-28,29,120000.00,80000.00 | 

| 5,Kundan,Manager,1,2019-02-27,56,500000.00,90000.00              | 

| 58,Harsh,HR,26,2022-01-16,48,80000.00,70000.00                   | 

| 59,Kapil,Software Developer,26,2019-12-26,29,100000.00,78000.00  | 

+------------------------------------------------------------------+ 

5 rows in set (0.00 sec) 

 

---
### 5) mysql> SELECT ename,salary FROM EMPLOYEE WHERE salary>2850; 

+--------+----------+ 

| ename  | salary   | 

+--------+----------+ 

| Karan  | 99999.90 | 

| Aditya | 80000.00 | 

| Kundan | 90000.00 | 

| Harsh  | 70000.00 | 

| Kapil  | 78000.00 | 

+--------+----------+ 

5 rows in set (0.00 sec) 

 

---
### 6) mysql> SELECT ename,dno FROM EMPLOYEE WHERE eno="79"; 

+--------+------+ 

| ename  | dno  | 

+--------+------+ 

| Shreya |   29 | 

+--------+------+ 

1 row in set (0.00 sec) 

 

---
### 7) mysql> SELECT ename,salary FROM EMPLOYEE WHERE salary NOT BETWEEN 1500 AND 2850; 

+--------+----------+ 

| ename  | salary   | 

+--------+----------+ 

| Karan  | 99999.90 | 

| Aditya | 80000.00 | 

| Kundan | 90000.00 | 

| Harsh  | 70000.00 | 

| Kapil  | 78000.00 | 

| Shreya | 58000.00 | 

+--------+----------+ 

6 rows in set (0.00 sec) 

---
### 8) mysql> SELECT ename,dno FROM EMPLOYEE WHERE dno=10 OR dno=30 ORDER BY ename ASC; 

Empty set (0.00 sec) 

---
### 9) mysql> INSERT INTO EMPLOYEE VALUES ("3","RISHAB","Supervisor","1981-10-28","5",56,100000,90000); 

Query OK, 1 row affected (0.40 sec) 

  

### mysql> SELECT ename,hire_date FROM EMPLOYEE WHERE YEAR(hire_date)="1981"; 

+--------+------------+ 

| ename  | hire_date  | 

+--------+------------+ 

| RISHAB | 1981-10-28 | 

+--------+------------+ 

1 row in set (0.02 sec) 

---
### 10) mysql> SELECT ename,job_type FROM EMPLOYEE WHERE manager IS NULL; 

+--------+------------------+ 

| ename  | job_type         | 

+--------+------------------+ 

| Karan  | CEO              | 

| Aditya | Software Testing | 

+--------+------------------+ 

2 rows in set (0.00 sec) 

 

 

---
### 11) mysql> UPDATE EMPLOYEE SET commission=0 WHERE eno="79" OR eno="58"; 

Query OK, 2 rows affected (0.12 sec) 

Rows matched: 2  Changed: 2  Warnings: 0 

  

### mysql> SELECT ename,salary,commission FROM EMPLOYEE WHERE commission>0; 

+--------+----------+------------+ 

| ename  | salary   | commission | 

+--------+----------+------------+ 

| Karan  | 99999.90 |  800000.00 | 

| Aditya | 80000.00 |  120000.00 | 

| RISHAB | 90000.00 |  100000.00 | 

| Kundan | 90000.00 |  500000.00 | 

| Kapil  | 78000.00 |  100000.00 | 

+--------+----------+------------+ 

5 rows in set (0.00 sec) 

--- 
### 12) mysql> SELECT * FROM EMPLOYEE ORDER BY SALARY DESC,COMMISSION DESC; 

+-----+--------+--------------------+------------+---------+------+------------+----------+ 

| eno | ename  | job_type           | hire_date  | manager | dno  | commission | salary   | 

+-----+--------+--------------------+------------+---------+------+------------+----------+ 

| 1   | Karan  | CEO                | 2019-01-16 | 1       |   56 |  800000.00 | 99999.90 | 

| 5   | Kundan | Manager            | 2019-02-27 | 1       |   56 |  500000.00 | 90000.00 | 

| 3   | RISHAB | Supervisor         | 1981-10-28 | 5       |   56 |  100000.00 | 90000.00 | 

| 26  | Aditya | Software Testing   | 2020-11-28 | 3       |   29 |  120000.00 | 80000.00 | 

| 59  | Kapil  | Software Developer | 2019-12-26 | 26      |   29 |  100000.00 | 78000.00 | 

| 58  | Harsh  | HR                 | 2022-01-16 | 26      |   48 |       0.00 | 70000.00 | 

| 79  | Shreya | UI Designer        | 2020-12-05 | 59      |   29 |       0.00 | 58000.00 | 

+-----+--------+--------------------+------------+---------+------+------------+----------+ 

7 rows in set (0.00 sec) 

 

---
### 13) mysql> SELECT ename FROM EMPLOYEE WHERE ename like "__a%"; 

Empty set (0.01 sec) 

---
### 14) mysql> SELECT ename FROM EMPLOYEE WHERE ename LIKE "%r%r%" OR ename LIKE "%a%a%" AND dno=30 AND manager="7788"; 

Empty set (0.00 sec) 

---
### 15) mysql> SELECT ename,salary,commission FROM EMPLOYEE WHERE commission>(salary+salary*0.05); 

+--------+----------+------------+ 

| ename  | salary   | commission | 

+--------+----------+------------+ 

| Karan  | 99999.90 |  800000.00 | 

| Aditya | 80000.00 |  120000.00 | 

| RISHAB | 90000.00 |  100000.00 | 

| Kundan | 90000.00 |  500000.00 | 

| Kapil  | 78000.00 |  100000.00 | 

+--------+----------+------------+ 

5 rows in set (0.00 sec) 

---
### 16) mysql> SELECT CURDATE() AS DATE,DAYNAME(CURDATE()) AS DAY; 

+------------+--------+ 

| DATE       | DAY    | 

+------------+--------+ 

| 2022-01-23 | Sunday | 

+------------+--------+ 

1 row in set (0.00 sec) 

---
### 17) mysql> SELECT ENAME,HIRE_DATE,DATE_ADD(DATE_ADD(HIRE_DATE,INTERVAL 6 MONTH),INTERVAL 9-DAYOFWEEK(DATE_ADD(HIRE_DATE,INTERVAL 6 MONTH)) DAY) AS SALARY_REVIEW_DATE FROM EMPLOYEE; 

+--------+------------+--------------------+ 

| ENAME  | HIRE_DATE  | SALARY_REVIEW_DATE | 

+--------+------------+--------------------+ 

| Karan  | 2019-01-16 | 2019-07-22         | 

| Aditya | 2020-11-28 | 2021-05-31         | 

| RISHAB | 1981-10-28 | 1982-05-03         | 

| Kundan | 2019-02-27 | 2019-09-02         | 

| Harsh  | 2022-01-16 | 2022-07-18         | 

| Kapil  | 2019-12-26 | 2020-06-29         | 

| Shreya | 2020-12-05 | 2021-06-07         | 

+--------+------------+--------------------+ 

7 rows in set (0.00 sec) 

---
### 18) mysql> SELECT E.ENAME,TIMESTAMPDIFF(MONTH,E.HIRE_DATE,CURDATE()) FROM EMPLOYEE E,DEPARTMENT D WHERE E.DNO=D.DNO AND D.DNAME="Purchase"; 

+--------+--------------------------------------------+ 

| ENAME  | TIMESTAMPDIFF(MONTH,E.HIRE_DATE,CURDATE()) | 

+--------+--------------------------------------------+ 

| Karan  |                                         38 | 

| RISHAB |                                        485 | 

| Kundan |                                         37 | 

+--------+--------------------------------------------+ 

3 rows in set (0.00 sec) 

---
### 19)mysql> select concat(ename,' earns ',salary, ' monthly but wants ', (3*salary)) as Dream_Salary from EMPLOYEE; 

+---------------------------------------------------+ 

| Dream_Salary                                      | 

+---------------------------------------------------+ 

| Karan earns 99999.90 monthly but wants 299999.70  | 

| Aditya earns 80000.00 monthly but wants 240000.00 | 

| RISHAB earns 90000.00 monthly but wants 270000.00 | 

| Kundan earns 90000.00 monthly but wants 270000.00 | 

| Harsh earns 70000.00 monthly but wants 210000.00  | 

| Kapil earns 78000.00 monthly but wants 234000.00  | 

| Shreya earns 58000.00 monthly but wants 174000.00 | 

+---------------------------------------------------+ 

7 rows in set (0.51 sec) 

---
### 20)mysql> select concat(UPPER(substring(ename,1,1)),Lower(substring(ename,2))) from EMPLOYEE where ename like 'J%' or ename like 'A%'or ename like 'M%';  

+---------------------------------------------------------------+ 

| concat(UPPER(substring(ename,1,1)),Lower(substring(ename,2))) | 

+---------------------------------------------------------------+ 

| Aditya                                                        | 

+---------------------------------------------------------------+ 

1 row in set (0.11 sec) 

---
### 21)mysql> select hire_date,ename, dayname(hire_date) from EMPLOYEE; 

+------------+--------+--------------------+ 

| hire_date  | ename  | dayname(hire_date) | 

+------------+--------+--------------------+ 

| 2019-01-16 | Karan  | Wednesday          | 

| 2020-11-28 | Aditya | Saturday           | 

| 1981-10-28 | RISHAB | Wednesday          | 

| 2019-02-27 | Kundan | Wednesday          | 

| 2022-01-16 | Harsh  | Sunday             | 

| 2019-12-26 | Kapil  | Thursday           | 

| 2020-12-05 | Shreya | Saturday           | 

+------------+--------+--------------------+ 

7 rows in set (0.13 sec) 

---
### 22)mysql>  select EMPLOYEE.ename,DEPARTMENT.DNAME,EMPLOYEE.dno from EMPLOYEE,DEPARTMENT where EMPLOYEE.dno=DEPARTMENT.DNO; 

+--------+-----------------+------+ 

| ename  | DNAME           | dno  | 

+--------+-----------------+------+ 

| Aditya | TECHNOLOGY      |   29 | 

| Kapil  | TECHNOLOGY      |   29 | 

| Shreya | TECHNOLOGY      |   29 | 

| Harsh  | HUMAN RESOURCES |   48 | 

| Karan  | Accounts        |   56 | 

| RISHAB | Accounts        |   56 | 

| Kundan | Accounts        |   56 | 

+--------+-----------------+------+ 

7 rows in set (0.00 sec) 

---
### 23)mysql> select distinct job_type from EMPLOYEE where dno='30';  

Empty set (0.24 sec) 

---
### 24)mysql> select ename, DNAME from EMPLOYEE,DEPARTMENT where EMPLOYEE.dno=DEPARTMENT.DNO and ename like '%a%'; 

+--------+-----------------+ 

| ename  | DNAME           | 

+--------+-----------------+ 

| Karan  | Accounts        | 

| Aditya | TECHNOLOGY      | 

| RISHAB | Accounts        | 

| Kundan | Accounts        | 

| Harsh  | HUMAN RESOURCES | 

| Kapil  | TECHNOLOGY      | 

| Shreya | TECHNOLOGY      | 

+--------+-----------------+ 

7 rows in set (0.10 sec) 

---
### 25)mysql> select EMPLOYEE.ename, EMPLOYEE.job_type, DEPARTMENT.DNO, DEPARTMENT.DNAME from EMPLOYEE, DEPARTMENT where EMPLOYEE.dno=DEPARTMENT.DNO and LOCATION='Dallas'; 

Empty set (0.00 sec) 

---
### 26) mysql> SELECT R1.ENAME AS EMPLOYEE_NAME,R1.ENO AS EMPLOYEE_NUMBER,R2.ENAME AS SUPERVISOR_NAME,R2.ENO AS SUPERVISOR_NUMBER FROM EMPLOYEE R1,EMPLOYEE R2 WHERE R1.MANAGER=R2.ENO; 

+---------------+-----------------+-----------------+-------------------+ 

| EMPLOYEE_NAME | EMPLOYEE_NUMBER | SUPERVISOR_NAME | SUPERVISOR_NUMBER | 

+---------------+-----------------+-----------------+-------------------+ 

| Karan         | 1               | Karan           | 1                 | 

| Aditya        | 26              | RISHAB          | 3                 | 

| RISHAB        | 3               | Kundan          | 5                 | 

| Kundan        | 5               | Karan           | 1                 | 

| Harsh         | 58              | RISHAB          | 3                 | 

| Kapil         | 59              | Aditya          | 26                | 

| Shreya        | 79              | Kapil           | 59                | 

+---------------+-----------------+-----------------+-------------------+ 

7 rows in set (0.00 sec) 

---
### 27) mysql> SELECT R.ENAME,R.DNO,R.SALARY FROM EMPLOYEE R,EMPLOYEE R1 WHERE R.SALARY=R1.SALARY AND R.DNO=R1.DNO AND R.ENO!=R1.ENO; 

+--------+------+----------+ 

| ENAME  | DNO  | SALARY   | 

+--------+------+----------+ 

| Kundan |   56 | 90000.00 | 

| RISHAB |   56 | 90000.00 | 

+--------+------+----------+ 

2 rows in set (0.00 sec) 

---
### 28)mysql> SELECT ename,REPEAT ('*',(salary/100)) AS SALARY_IN_STAR FROM EMPLOYEE; 

---
### 29)mysql> select Max(salary),Min(salary),Sum(salary),Avg(salary) FROM EMPLOYEE; 

+-------------+-------------+-------------+--------------+ 

| Max(salary) | Min(salary) | Sum(salary) | Avg(salary)  | 

+-------------+-------------+-------------+--------------+ 

|    99999.90 |    58000.00 |   565999.90 | 80857.128571 | 

+-------------+-------------+-------------+--------------+ 

1 row in set (0.08 sec) 

---
### 30)mysql> select job_type,COUNT(*)FROM EMPLOYEE GROUP BY job_type;  

+--------------------+----------+ 

| job_type           | COUNT(*) | 

+--------------------+----------+ 

| CEO                |        1 | 

| Software Testing   |        1 | 

| Supervisor         |        1 | 

| Manager            |        1 | 

| HR                 |        1 | 

| Software Developer |        1 | 

| UI Designer        |        1 | 

+--------------------+----------+ 

7 rows in set (0.02 sec) 

---
### 31)mysql> select COUNT(DISTINCT manager) FROM EMPLOYEE; 

+-------------------------+ 

| COUNT(DISTINCT manager) | 

+-------------------------+ 

|                       5 | 

+-------------------------+ 

1 row in set (0.00 sec) 

---
### 32) mysql> SELECT DNAME,LOCATION,COUNT(ENO) AS NUMBER_OF_EMPLOYEES,AVG(SALARY) AS AVERAGE_SALARY FROM DEPARTMENT,EMPLOYEE WHERE EMPLOYEE.DNO=DEPARTMENT.DNO GROUP BY DEPARTMENT.DNO; 

+-----------------+-----------+---------------------+----------------+ 

| DNAME           | LOCATION  | NUMBER_OF_EMPLOYEES | AVERAGE_SALARY | 

+-----------------+-----------+---------------------+----------------+ 

| Purchase        | Lucknow   |                   3 |   93333.300000 | 

| TECHNOLOGY      | Banglore  |                   3 |   72000.000000 | 

| HUMAN RESOURCES | New Delhi |                   1 |   70000.000000 | 

+-----------------+-----------+---------------------+----------------+ 

3 rows in set (0.00 sec) 

---
### 33)mysql> select ename, hire_date FROM EMPLOYEE WHERE dno=(SELECT dno FROM EMPLOYEE WHERE ename = 'Blake'); 

Empty set (0.01 sec) 

---
### 34)mysql> select eno,ename FROM EMPLOYEE WHERE salary>(Select AVG(salary) FROM EMPLOYEE); 

+-----+--------+ 

| eno | ename  | 

+-----+--------+ 

| 1   | Karan  | 

| 3   | RISHAB | 

| 5   | Kundan | 

+-----+--------+ 

3 rows in set (0.00 sec) 

---
### 35)mysql> select e.eno,e.ename FROM EMPLOYEE AS e,EMPLOYEE as d WHERE e.dno=d.dno AND d.ename LIKE '%T%'; 

+-----+--------+ 

| eno | ename  | 

+-----+--------+ 

| 26  | Aditya | 

| 59  | Kapil  | 

| 79  | Shreya | 

+-----+--------+ 

3 rows in set (0.00 sec) 

--- 
### 36)mysql> select ename, salary FROM EMPLOYEE WHERE manager = (select eno FROM EMPLOYEE WHERE ename = 'King'); 

Empty set (0.00 sec) 

---
### 37)mysql> select e.dno,e.ename,e.job_type FROM EMPLOYEE AS e,DEPARTMENT as d WHERE d.DNO=e.dno AND d.DNAME='Sales';  

Empty set (0.00 sec) 

---
### 38) mysql> SELECT ENAME,DNAME FROM EMPLOYEE,DEPARTMENT WHERE EMPLOYEE.DNO=DEPARTMENT.DNO AND TIMESTAMPDIFF(YEAR,EMPLOYEE.HIRE_DATE,CURDATE())>20; 

+--------+----------+ 

| ENAME  | DNAME    | 

+--------+----------+ 

| RISHAB | Purchase | 

+--------+----------+ 

1 row in set (0.00 sec) 

 

---
### 39) mysql> UPDATE DEPARTMENT SET LOCATION="New Delhi" WHERE DNO=56; 

Query OK, 1 row affected (0.00 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

### mysql> SELECT COUNT(DNO) AS TOTAL_NUMBER_OF_DEPARTMENT,LOCATION FROM DEPARTMENT GROUP BY LOCATION; 

+----------------------------+-----------+ 

| TOTAL_NUMBER_OF_DEPARTMENT | LOCATION  | 

+----------------------------+-----------+ 

|                          1 | Banglore  | 

|                          2 | New Delhi | 

+----------------------------+-----------+ 

2 rows in set (0.00 sec) 

 

---
### 40) mysql> SELECT DNAME FROM DEPARTMENT,EMPLOYEE WHERE EMPLOYEE.DNO=DEPARTMENT.DNO GROUP BY DEPARTMENT.DNO HAVING COUNT(ENO)>=20; 

Empty set (0.00 sec) 

 

---
### 41) mysql> SELECT E1.ENAME AS EMPLOYEE_NAME FROM EMPLOYEE E1 WHERE E1.ENO NOT IN (SELECT MANAGER FROM EMPLOYEE); 

+---------------+ 

| EMPLOYEE_NAME | 

+---------------+ 

| Harsh         | 

| Shreya        | 

+---------------+ 

2 rows in set (0.00 sec) 

  

### mysql> SELECT ENAME AS SUPERVISOR_NAME FROM EMPLOYEE WHERE ENO IN (SELECT MANAGER FROM EMPLOYEE GROUP BY MANAGER HAVING COUNT(ENO)>5); 

Empty set (0.00 sec) 

 

---
### 42)  
