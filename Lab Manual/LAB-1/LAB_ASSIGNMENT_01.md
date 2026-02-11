
# 📚 DBMS LAB ASSIGNMENT 01

> **Date:** 11/February/2026  
> **Database:** saikrishnadb  
> **Server:** MariaDB 10.4.32  

---

## 📋 Objective

Create two tables (`DEPARTMENT` and `EMPLOYEE`) and perform the following operations:

1. Create `EMPLOYEE_MASTER` table with data from `EMPLOYEE` table  
2. Delete all records from `EMPLOYEE_MASTER` where `DEPTNO = 10`  
3. Update salary by 10% increase for `DEPTNO = 20` in `EMPLOYEE_MASTER`  
4. Alter `SAL` column to `DECIMAL(10,2)` in `EMPLOYEE_MASTER`  
5. Drop `EMPLOYEE_MASTER` table  

---

## 📊 Table Structures

### Table 1: DEPARTMENT

| Field  | Type        | Null | Key | Default | Extra |
|------|-------------|------|-----|---------|-------|
| DEPTNO | INT(2) | NO | PRI | NULL | |
| DNAME | VARCHAR(15) | NO | | NULL | |

---

### Table 2: EMPLOYEE

| Field | Type | Null | Key | Default | Extra |
|------|------|------|-----|---------|-------|
| EMPNO | INT(4) | NO | PRI | NULL | |
| ENAME | VARCHAR(20) | NO | | NULL | |
| JOB | VARCHAR(20) | YES | | NULL | |
| MGR | INT(4) | YES | | NULL | |
| HIREDATE | DATE | YES | | NULL | |
| SAL | INT(10) | YES | | NULL | |
| COMM | INT(7) | YES | | NULL | |
| DEPTNO | INT(2) | YES | MUL | NULL | Foreign Key |

---

## 📁 Sample Data

### DEPARTMENT Table

| DEPTNO | DNAME |
|------|------------|
| 10 | RESEARCH |
| 20 | ACCOUNTING |
| 30 | SALES |
| 40 | OPERATIONS |

---

### EMPLOYEE Table

| EMPNO | ENAME | JOB | MGR | HIREDATE | SAL | COMM | DEPTNO |
|------|-------|-----------|------|------------|------|------|--------|
| 7369 | SMITH | CLERK | 7902 | 1980-12-17 | 800 | NULL | 20 |
| 7499 | ALLEN | SALESMAN | 7698 | 1981-02-20 | 1600 | 300 | 30 |
| 7521 | WARD | SALESMAN | 7698 | 1981-02-22 | 1250 | 300 | 30 |
| 7566 | JONES | MANAGER | 7839 | 1981-04-02 | 2975 | NULL | 20 |
| 7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 | 30 |
| 7698 | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850 | NULL | 30 |
| 7782 | CLARK | MANAGER | 7839 | 1981-06-09 | 2450 | NULL | 20 |
| 7788 | SCOTT | ANALYST | 7566 | 1982-12-09 | 3000 | NULL | 40 |
| 7839 | KING | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL | 20 |
| 7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0 | 30 |
| 7876 | ADAMS | CLERK | 7788 | 1983-01-12 | 1100 | NULL | 20 |
| 7900 | JAMES | CLERK | 7698 | 1981-12-03 | 950 | NULL | 30 |
| 7902 | FORD | ANALYST | 7566 | 1981-12-03 | 3000 | NULL | 20 |
| 7934 | MILLER | CLERK | 7782 | 1982-01-23 | 1300 | NULL | 10 |

---

## 🔧 SQL Queries & Solutions

### Step 1: Create Tables

```sql
CREATE TABLE DEPARTMENT (
  DEPTNO INT(2) PRIMARY KEY,
  DNAME VARCHAR(15) NOT NULL
);

CREATE TABLE EMPLOYEE (
  EMPNO INT(4) PRIMARY KEY,
  ENAME VARCHAR(20),
  JOB VARCHAR(20),
  MGR INT(4),
  HIREDATE DATE,
  SAL INT(10),
  COMM INT(7),
  DEPTNO INT(2),
  FOREIGN KEY (DEPTNO) REFERENCES DEPARTMENT(DEPTNO)
);
````

**Output:**

```
Query OK, 0 rows affected
```

---

### Step 2: Insert Data

```sql
INSERT INTO DEPARTMENT VALUES
(10,'RESEARCH'),
(20,'ACCOUNTING'),
(30,'SALES'),
(40,'OPERATIONS');
```

```sql
INSERT INTO EMPLOYEE VALUES
(7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20),
(7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30),
(7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
```

**Output:**

```
Query OK, rows affected
```

---

## ✅ Problem Solutions

### Problem 1: Create EMPLOYEE_MASTER

```sql
CREATE TABLE EMPLOYEE_MASTER AS
SELECT * FROM EMPLOYEE;
```

**Output:**

```
Query OK, 14 rows affected
```

---

### Problem 2: Delete where DEPTNO = 10

```sql
DELETE FROM EMPLOYEE_MASTER WHERE DEPTNO = 10;
```

**Output:**

```
Query OK, 1 row affected
```

---

### Problem 3: Update salary by 10%

```sql
UPDATE EMPLOYEE_MASTER
SET SAL = SAL * 1.10
WHERE DEPTNO = 20;
```

**Output:**

```
Query OK, rows affected
```

---

### Problem 4: Alter SAL column

```sql
ALTER TABLE EMPLOYEE_MASTER
MODIFY SAL DECIMAL(10,2);
```

**Output:**

```
Query OK, table altered
```

---

### Problem 5: Drop EMPLOYEE_MASTER

```sql
DROP TABLE EMPLOYEE_MASTER;
```

**Output:**

```
Query OK, table dropped
```

## 📌 Submitted By

**Saikrishna**
Roll No: **2410030908**
IILM University
