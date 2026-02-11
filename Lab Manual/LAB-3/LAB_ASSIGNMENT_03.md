
````
# 📚 DBMS LAB ASSIGNMENT 03

> **Date:** 11/February/2026  
> **Database:** saikrishnadb  
> **Server:** MariaDB 10.4.32

---

## 📋 Objective

Perform advanced data retrieval queries using **ORDER BY**, **LIKE patterns**, **IN**, **IS NULL**, and **calculated columns**:

1. List all employees and jobs in Department 30 in descending order of salary  
2. List job and department number of employees whose name is five letters long, starts with 'A' and ends with 'N'  
3. Display the names of employees whose name starts with 'S'  
4. Display the names of employees whose name ends with 'S'  
5. Display names of employees working in department 10, 20, or 40 OR working as clerk, salesman, or analyst  
6. Display employee number and names for employees who earn commission  
7. Display employee number and total salary for each employee  
8. Display employee number and annual salary for each employee  
9. Display names of all employees working as clerks and earning more than 3000  
10. Display names of employees working as clerk, salesman, or analyst and earning more than 3000  

---

## 📊 Reference Table: EMPLOYEE

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

### Problem 1: List All Employees and Jobs in Department 30 (Descending Order of Salary)

```sql
SELECT ENAME, JOB, SAL
FROM EMPLOYEE
WHERE DEPTNO = 30
ORDER BY SAL DESC;
```

**Output:**

```
+--------+----------+------+
| ENAME  | JOB      | SAL  |
+--------+----------+------+
| BLAKE  | MANAGER  | 2850 |
| ALLEN  | SALESMAN | 1600 |
| TURNER | SALESMAN | 1500 |
| WARD   | SALESMAN | 1250 |
| MARTIN | SALESMAN | 1250 |
| JAMES  | CLERK    |  950 |
+--------+----------+------+
6 rows in set (0.001 sec)
```

---

### Problem 2: Employees Whose Name is 5 Letters, Starts with 'A' and Ends with 'N'

```sql
SELECT JOB, DEPTNO
FROM EMPLOYEE
WHERE ENAME LIKE 'A___N';
```

**Output:**

```
+----------+--------+
| JOB      | DEPTNO |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+
1 row in set (0.001 sec)
```

---

### Problem 3: Names Starting with 'S'

```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE 'S%';
```

**Output:**

```
SMITH
SCOTT
```

---

### Problem 4: Names Ending with 'S'

```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE '%S';
```

**Output:**

```
JONES
ADAMS
JAMES
```

---

### Problem 5: Dept 10/20/40 OR Clerk/Salesman/Analyst

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO IN (10,20,40)
OR JOB IN ('CLERK','SALESMAN','ANALYST');
```

**Output:**
13 rows returned

---

### Problem 6: Employees Who Earn Commission

```sql
SELECT EMPNO, ENAME
FROM EMPLOYEE
WHERE COMM IS NOT NULL AND COMM > 0;
```

**Output:**
ALLEN, WARD, MARTIN

---

### Problem 7: Total Salary (SAL + COMM)

```sql
SELECT EMPNO, (SAL + IFNULL(COMM,0)) AS TOTAL_SALARY
FROM EMPLOYEE;
```

---

### Problem 8: Annual Salary

```sql
SELECT EMPNO, (SAL * 12) AS ANNUAL_SALARY
FROM EMPLOYEE;
```

---

### Problem 9: Clerks Earning More Than 3000

```sql
SELECT ENAME FROM EMPLOYEE
WHERE JOB='CLERK' AND SAL>3000;
```

**Output:**
Empty set

---

### Problem 10: Clerk/Salesman/Analyst Earning More Than 3000

```sql
SELECT ENAME FROM EMPLOYEE
WHERE JOB IN ('CLERK','SALESMAN','ANALYST')
AND SAL>3000;
```

**Output:**
Empty set

---

## 📝 Summary

All ORDER BY, LIKE, IN, NULL handling, and calculated column queries were executed successfully.

---

> **Submitted By:** Saikrishna
> **Roll No:** 2410030908
> **Course:** DBMS Lab

