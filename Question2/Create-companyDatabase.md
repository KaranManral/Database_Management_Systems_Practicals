---
### Creating Database and Tables :

 

create database COMPANY; 

CREATE TABLE EMPLOYEE (FNAME VARCHAR(50) NOT NULL,MINIT CHAR(1),LNAME VARCHAR(50) NOT NULL,SSN VARCHAR(50) PRIMARY KEY NOT NULL,BDATE DATE NOT NULL,ADDRESS VARCHAR(100) NOT NULL,SEX CHAR(1) NOT NULL,SALARY DECIMAL(10,2),SUPERSSN VARCHAR(50),DNO INT NOT NULL); 

ALTER TABLE EMPLOYEE ADD CONSTRAINT FK_SUPERSSN FOREIGN KEY (SUPERSSN) REFERENCES EMPLOYEE(SSN); 

CREATE TABLE DEPARTMENT (DNAME VARCHAR(50) NOT NULL,DNUMBER INT PRIMARY KEY NOT NULL,MGRSSN VARCHAR(50) NOT NULL,MGRSTARTDATE DATE NOT NULL); 

ALTER TABLE EMPLOYEE ADD CONSTRAINT FK_DNO FOREIGN KEY (DNO) REFERENCES DEPARTMENT(DNUMBER); 

ALTER TABLE DEPARTMENT ADD CONSTRAINT FK_MGRSSN FOREIGN KEY (MGRSSN) REFERENCES EMPLOYEE(SSN); 

CREATE TABLE DEPT_LOCATIONS (DNUMBER INT NOT NULL,DLOCATION VARCHAR(50) NOT NULL, PRIMARY KEY(DNUMBER,DLOCATION)); 

ALTER TABLE DEPT_LOCATIONS ADD CONSTRAINT FK_DNO1 FOREIGN KEY (DNUMBER) REFERENCES DEPARTMENT(DNUMBER); 

CREATE TABLE PROJECT (PNAME VARCHAR(50) NOT NULL,PNUMBER INT NOT NULL PRIMARY KEY,PLOCATION VARCHAR(50) NOT NULL,DNUM INT NOT NULL); 

ALTER TABLE PROJECT ADD CONSTRAINT FK_DNO2 FOREIGN KEY (DNUM) REFERENCES DEPARTMENT(DNUMBER); 

CREATE TABLE WORKS_ON (ESSN VARCHAR(50) NOT NULL,PNO INT NOT NULL,HOURS DECIMAL(10,2),PRIMARY KEY(ESSN,PNO)); 

ALTER TABLE WORKS_ON ADD CONSTRAINT FK_PNO FOREIGN KEY (PNO) REFERENCES PROJECT(PNUMBER); 

ALTER TABLE WORKS_ON ADD CONSTRAINT FK_ESSN FOREIGN KEY (ESSN) REFERENCES EMPLOYEE(SSN); 

CREATE TABLE DEPENDENT (ESSN VARCHAR(50) NOT NULL,DEPENDENT_NAME VARCHAR(50) NOT NULL,SEX CHAR(1) NOT NULL,BDATE DATE NOT NULL,RELATIONSHIP VARCHAR(50) NOT NULL,PRIMARY KEY(ESSN,DEPENDENT_NAME)); 

ALTER TABLE DEPENDENT ADD CONSTRAINT FK_ESSN1 FOREIGN KEY (ESSN) REFERENCES EMPLOYEE(SSN); 

  
---
### Inserting Data Into Employee Table :

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("John","B","Smith","123456789","1965-01-09","731 Fondren, Houston, TX","M",30000,5); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("Franklin","T","Wong","333445555","1955-12-08","638 Voss, Houston, TX","M",40000,5); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("Alicia","J","Zelaya","999887777","1968-01-19","3321 Castle, Spring, TX","F",25000,4); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("Jennifer","S","Wallace","987654321","1941-06-20","291 Berry, Bellaire, TX","F",43000,4); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("Ramesh","K","Narayan","666884444","1962-09-15","975 Fire Oak, Humble, TX","M",38000,5); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("Joyce","A","English","453453453","1972-07-31","5631 Rice, Houston, TX","F",25000,5); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("Ahmad","V","Jabbar","987987987","1969-03-29","980 Dallas, Houston, TX","M",25000,4); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO EMPLOYEE (FNAME,MINIT,LNAME,SSN,BDATE,ADDRESS,SEX,SALARY,DNO) VALUES ("James","E","Brog","888665555","1937-11-10","450 Stone, Houston, TX","M",55000,1); 

Query OK, 1 row affected (0.04 sec) 

    

mysql> UPDATE EMPLOYEE SET SUPERSSN="333445555" WHERE SSN="123456789"; 

Query OK, 1 row affected (0.01 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

mysql> UPDATE EMPLOYEE SET SUPERSSN="888665555" WHERE SSN="333445555"; 

Query OK, 1 row affected (0.00 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

mysql> UPDATE EMPLOYEE SET SUPERSSN="333445555" WHERE SSN="453453453"; 

Query OK, 1 row affected (0.04 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

mysql> UPDATE EMPLOYEE SET SUPERSSN="333445555" WHERE SSN="666884444"; 

Query OK, 1 row affected (0.00 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

mysql> UPDATE EMPLOYEE SET SUPERSSN="888665555" WHERE SSN="987654321"; 

Query OK, 1 row affected (0.04 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

mysql> UPDATE EMPLOYEE SET SUPERSSN="987654321" WHERE SSN="987987987"; 

Query OK, 1 row affected (0.01 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  

mysql> UPDATE EMPLOYEE SET SUPERSSN="987654321" WHERE SSN="999887777"; 

Query OK, 1 row affected (0.00 sec) 

Rows matched: 1  Changed: 1  Warnings: 0 

  
---
### Inserting Data Into Department Table :

  

mysql> INSERT INTO DEPARTMENT VALUES ("Research",5,"333445555","1988-05-22"); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO DEPARTMENT VALUES ("Administration",4,"987654321","1995-01-01"); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO DEPARTMENT VALUES ("Headquarters",1,"888665555","1981-06-19"); 

Query OK, 1 row affected (0.04 sec) 


  
---
### Inserting Data Into Dept_Locations table :

  

mysql> insert into DEPT_LOCATIONS VALUES (1,"Houston"); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> insert into DEPT_LOCATIONS VALUES (4,"Stafford"); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> insert into DEPT_LOCATIONS VALUES (5,"Bellaire"); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> insert into DEPT_LOCATIONS VALUES (5,"Sugarland"); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> insert into DEPT_LOCATIONS VALUES (5,"Houston"); 

Query OK, 1 row affected (0.00 sec) 

  
  
---
### Inserting Data Into Project table :

  

mysql> INSERT INTO PROJECT VALUES ("ProductX",1,"Bellaire",5); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO PROJECT VALUES ("ProductY",2,"Sugarland",5); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO PROJECT VALUES ("ProductZ",3,"Houston",5); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO PROJECT VALUES ("Computerization",10,"Stafford",4); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO PROJECT VALUES ("Newbenefits",30,"Stafford",4); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO PROJECT VALUES ("Reorganization",20,"Houston",1); 

Query OK, 1 row affected (0.04 sec) 

  
---
### Inserting Data into Works_On table :

  

mysql> INSERT INTO WORKS_ON VALUES("123456789",1,32.5); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("123456789",2,7.5); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("666884444",3,40.0); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("453453453",1,20.0); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("453453453",2,20.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("333445555",2,10.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("333445555",3,10.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("333445555",10,10.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("333445555",20,10.0); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("999887777",30,30.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("999887777",10,10.0); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("987987987",10,35.0); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("987987987",30,5.0); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("987654321",30,20.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("987654321",20,15.0); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO WORKS_ON VALUES("888665555",20,NULL); 

Query OK, 1 row affected (0.00 sec) 

    
---
### Inserting Data into Dependent Table :

  

mysql> INSERT INTO DEPENDENT VALUES("333445555","Alice","F","1986-04-05","Daughter"); 

Query OK, 1 row affected (0.01 sec) 

  

mysql> INSERT INTO DEPENDENT VALUES("333445555","Theodore","M","1983-10-25","Son"); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO DEPENDENT VALUES("333445555","Joy","F","1958-05-03","Spouse"); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO DEPENDENT VALUES("987654321","Abner","M","1942-02-28","Spouse"); 

Query OK, 1 row affected (0.04 sec) 

  

mysql> INSERT INTO DEPENDENT VALUES("123456789","Michael","M","1988-01-04","Son"); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO DEPENDENT VALUES("123456789","Alice","F","1988-12-30","Daughter"); 

Query OK, 1 row affected (0.00 sec) 

  

mysql> INSERT INTO DEPENDENT VALUES("123456789","Elizabeth","F","1967-05-05","Spouse"); 

Query OK, 1 row affected (0.00 sec) 

 
