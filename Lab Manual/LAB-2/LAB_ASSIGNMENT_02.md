
# 📚 DBMS LAB ASSIGNMENT 02

> **Date:** 11/February/2026  
> **Database:** saikrishnadb  
> **Server:** MariaDB 10.4.32

---

## 📋 Objective

Perform queries using the **EMPLOYEE** table to retrieve data using various SQL clauses:

1. List all distinct jobs in EMPLOYEE  
2. List all information about employees in Department Number 30  
3. Find all department numbers with department names greater than 20  
4. Find all information about managers and clerks in Department 30  
5. List Employee name, Employee number, and department of all clerks  
6. Find all managers not in Department 30  
7. List information about employees in Department 10 who are not managers or clerks  
8. Find employees and jobs earning between 1200 and 1400  
9. List Name and Department Number of employees who are clerks, analysts, or salesmen  
10. List Name and Department Number of employees whose names begin with M  

---

## 📊 Reference Tables

### DEPARTMENT Table

| DEPTNO | DNAME      |
|--------|------------|
| 10     | RESEARCH   |
| 20     | ACCOUNTING |
| 30     | SALES      |
| 40     | OPERATIONS |

---

### EMPLOYEE Table

| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
|-------|--------|-----------|------|------------|------|------|--------|
| 7369  | SMITH  | CLERK     | 7902 | 1980-12-17 | 800  | NULL | 20     |
| 7499  | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7521  | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 | 300  | 30     |
| 7566  | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7654  | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 | 30     |
| 7698  | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7782  | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL | 20     |
| 7788  | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7839  | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL | 20     |
| 7844  | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7876  | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL | 20     |
| 7900  | JAMES  | CLERK     | 7698 | 1981-12-03 | 950  | NULL | 30     |
| 7902  | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL | 20     |
| 7934  | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL | 10     |

---

## 🔧 Database Connection

```sql
C:\xampp\mysql\bin> mysql -u root
USE saikrishnadb;
````

---

## ✅ Problem Solutions

### Problem 1: List All Distinct Jobs in EMPLOYEE

```sql
SELECT DISTINCT JOB
FROM EMPLOYEE;
```

**Output:**

```
+-----------+
| JOB       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.001 sec)
```

---

### Problem 2: List All Information About Employees in Department 30

```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 30;
```

**Output:**

```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
+-------+--------+-----------+------+------------+------+------+--------+
6 rows in set (0.001 sec)
```

---

### Problem 3: Find All Department Numbers with Department Names Greater Than 20

```sql
SELECT DEPTNO, DNAME
FROM DEPARTMENT
WHERE DEPTNO > 20;
```

**Output:**

```
+--------+------------+
| DEPTNO | DNAME      |
+--------+------------+
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
2 rows in set (0.001 sec)
```

---

### Problem 4: Find All Information About Managers and Clerks in Department 30

```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 30
AND JOB IN ('MANAGER', 'CLERK');
```

**Output:**

```
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
|  7698 | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 |  950 | NULL |     30 |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set (0.001 sec)

---

## 📌 Submitted By

**Saikrishna**
Roll No: **2410030908**
IILM University

