Create EMP Table

CREATE TABLE emp
(
    empid SMALLINT,
    ename VARCHAR(10),
    job VARCHAR(10),
    sal SMALLMONEY,
    hiredate DATE,
    dept VARCHAR(10)
);

Insert Sample Data

INSERT INTO emp
VALUES
(100,'sachin','clerk',6000,'2026-06-11','hr'),
(101,'rahul','manager',9000,'2026-05-10','sales'),
(102,'arvind','analyst',8000,'2019-10-05','it'),
(103,'kumar',NULL,NULL,'2018-02-22','it'),
(104,'nitin','clerk',7000,'2022-04-20','hr');

===============================================================
1. Display employee names and salaries
SELECT ename,sal
FROM emp;

===============================================================
2. Display employee names, jobs and hire dates
SELECT ename,job,hiredate
FROM emp;

===============================================================
3. Display all employee details
SELECT *
FROM emp;

===============================================================
4. Display employee whose id is 103
SELECT *
FROM emp
WHERE empid = 103;

===============================================================
5. Display employee whose name is Nitin
SELECT *
FROM emp
WHERE ename = 'nitin';

===============================================================
6. Display employees earning more than 5000
SELECT *
FROM emp
WHERE sal > 5000;

===============================================================
7. Display employees joined after 2020
SELECT *
FROM emp
WHERE hiredate > '2020-12-31';

===============================================================
8. Display employees joined before 2020
SELECT *
FROM emp
WHERE hiredate < '2020-01-01';

===============================================================
9. Display employees not working in HR
SELECT *
FROM emp
WHERE dept <> 'hr';

===============================================================
10. Display employees working as Clerk or Manager
SELECT *
FROM emp
WHERE job = 'clerk'
OR job = 'manager';

===============================================================
11. Display employees whose ids are 100,103,105
SELECT *
FROM emp
WHERE empid IN (100,103,105);

 ===============================================================
12. Display employees working in HR and earning more than 5000
SELECT *
FROM emp
WHERE dept = 'hr'
AND sal > 5000;

 ===============================================================
13. Display employees earning between 5000 and 10000
SELECT *
FROM emp
WHERE sal > 5000
AND sal < 10000;

 ===============================================================
14. Display employees joined in 2020
SELECT *
FROM emp
WHERE hiredate >= '2020-01-01'
AND hiredate <= '2020-12-31';

 ===============================================================
15. Display Clerks and Managers earning more than 7000
SELECT *
FROM emp
WHERE (job = 'clerk' OR job = 'manager')
AND sal > 7000;

 ===============================================================
16. Display employees working as Clerk or Manager using IN
SELECT *
FROM emp
WHERE job IN ('clerk','manager');

 ===============================================================
17. Display employees not working as Clerk or Manager
SELECT *
FROM emp
WHERE job NOT IN ('clerk','manager');

 ===============================================================
18. Display employees earning between 5000 and 10000
SELECT *
FROM emp
WHERE sal BETWEEN 5000 AND 10000;

 ===============================================================
19. Display employees joined in 2019
SELECT *
FROM emp
WHERE hiredate BETWEEN '2019-01-01'
AND '2019-12-31';

 ===============================================================
20. Display employees not joined in 2019
SELECT *
FROM emp
WHERE hiredate NOT BETWEEN '2019-01-01'
AND '2019-12-31';

 ===============================================================
21. Display employees whose names start with S
SELECT *
FROM emp
WHERE ename LIKE 's%';

 ===============================================================
22. Display employees whose names end with D
SELECT *
FROM emp
WHERE ename LIKE '%d';

 ===============================================================
23. Display employees whose names contain A
SELECT *
FROM emp
WHERE ename LIKE '%a%';

 ===============================================================
24. Display employees where A is the 4th character
SELECT *
FROM emp
WHERE ename LIKE '___a%';

 ===============================================================
25. Display employees where A is 4th character from last
SELECT *
FROM emp
WHERE ename LIKE '%a___';

 ===============================================================
26. Display employees whose names contain exactly 5 characters
SELECT *
FROM emp
WHERE ename LIKE '_____';

 ===============================================================
27. Display employees whose names start with vowels
SELECT *
FROM emp
WHERE ename LIKE '[aeiou]%';

 ===============================================================
28. Display employees whose names start between A and P
SELECT *
FROM emp
WHERE ename LIKE '[a-p]%';

 ===============================================================
29. Display employees joined in October month
SELECT *
FROM emp
WHERE hiredate LIKE '%-10-%';

 ===============================================================
30. Display employees whose job is NULL
SELECT *
FROM emp
WHERE job IS NULL;

 ===============================================================
31. Display employees whose salary is NULL
SELECT *
FROM emp
WHERE sal IS NULL;

 ===============================================================
32. Display employees whose job is NOT NULL
SELECT *
FROM emp
WHERE job IS NOT NULL;

 ===============================================================
33. Display employee names and annual salaries
SELECT ename,
       sal * 12 AS annsal
FROM emp;

 ===============================================================
34. Display employee names and annual salaries with heading
SELECT ename,
       sal * 12 AS [annual salary]
FROM emp;

 ===============================================================
35. Display HRA, DA, TAX and Total Salary
SELECT ename,
       sal,
       sal * 0.2 AS hra,
       sal * 0.3 AS da,
       sal * 0.1 AS tax,
       sal + (sal * 0.2) + (sal * 0.3) - (sal * 0.1) AS totsal
FROM emp;

 ===============================================================
36. Arrange employees name wise ascending
SELECT *
FROM emp
ORDER BY ename ASC;

 ===============================================================
37. Arrange employees salary wise descending
SELECT *
FROM emp
ORDER BY sal DESC;

 ===============================================================
38. Display employee who joined first
SELECT *
FROM emp
ORDER BY hiredate ASC;
39. Arrange employee list department wise and salary wise descending
SELECT empid,
       ename,
       sal,
       dept
FROM emp
ORDER BY dept ASC,
         sal DESC;

 ===============================================================
40. Display Clerks and Managers sorted by salary descending
SELECT *
FROM emp
WHERE job IN ('clerk','manager')
ORDER BY sal DESC;

===============================================================
41. Display employees working as Clerk or Manager and arrange them salary-wise descending
SELECT *
FROM emp
WHERE job IN ('CLERK','MANAGER')
ORDER BY sal DESC;

 ===============================================================
 ===============================================================
42. Display distinct department numbers

SELECT DISTINCT deptno
FROM emp;

===============================================================
43. Display distinct job titles

SELECT DISTINCT job
FROM emp;

===============================================================
44. Display first 5 rows from EMP table

SELECT TOP 5 *
FROM emp;

===============================================================
45. Display top 5 highest paid employees

SELECT TOP 5 *
FROM emp
ORDER BY sal DESC;

===============================================================
46. Display top 5 employees based on experience

SELECT TOP 5 *
FROM emp
ORDER BY hiredate ASC;

===============================================================
47. Display top 5 maximum salaries

SELECT DISTINCT TOP 5 sal
FROM emp
ORDER BY sal DESC;

===============================================================
48. Update commission of all employees to 500

UPDATE emp
SET comm = 500;

===============================================================
49. Update commission to 500 for employees whose commission is NULL

UPDATE emp
SET comm = 500
WHERE comm IS NULL;

===============================================================
50. Update commission to NULL where commission is not NULL

UPDATE emp
SET comm = NULL
WHERE comm IS NOT NULL;

===============================================================
51. Update salary to 2000 and commission to 500 for employee 7369

UPDATE emp
SET sal = 2000,
    comm = 500
WHERE empno = 7369;

===============================================================
52. Increase salary by 20% and commission by 10% for Salesmen joined in 1981

UPDATE emp
SET sal = sal + (sal * 0.2),
    comm = comm + (comm * 0.1)
WHERE job = 'SALESMAN'
AND hiredate LIKE '1981%';

===============================================================
53. Increase price of Samsung, Redmi and Realme mobiles by 10%

UPDATE products
SET price = price + (price * 0.1)
WHERE brand IN ('samsung','redmi','realme')
AND category = 'mobiles';

===============================================================
54. Delete all rows from EMP table

DELETE FROM emp;

===============================================================
55. Delete employees whose employee numbers are 7844 and 7566

DELETE FROM emp
WHERE empno IN (7844,7566);

===============================================================
56. Delete employees who joined in December 1981

DELETE FROM emp
WHERE hiredate LIKE '1981-12-%';

-- OR

DELETE FROM emp
WHERE hiredate BETWEEN '1981-12-01'
AND '1981-12-31';

===============================================================
57. Add Gender column to EMP table

ALTER TABLE emp
ADD gender CHAR(1);

===============================================================
58. Update gender of employee 7369 as M

UPDATE emp
SET gender = 'M'
WHERE empno = 7369;

===============================================================
59. Drop Gender column from EMP table

ALTER TABLE emp
DROP COLUMN gender;

===============================================================
60. Change EMPNO datatype to INT

ALTER TABLE emp
ALTER COLUMN empno INT;

===============================================================
61. Change HIREDATE datatype to DATETIME

ALTER TABLE emp
ALTER COLUMN hiredate DATETIME;

===============================================================
62. Increase ENAME column size to 20

ALTER TABLE emp
ALTER COLUMN ename VARCHAR(20);

===============================================================
63. Drop EMP table

DROP TABLE emp;

===============================================================
64. Remove all rows from STUDENT table but keep structure

TRUNCATE TABLE student;

===============================================================
65. Rename STUDENT table to STUD

SP_RENAME 'student','stud';

===============================================================
66. Rename column M to MATHS in STUD table

SP_RENAME 'STUD.M','MATHS';

===============================================================
67. Create CUSTOMER table with Identity column

CREATE TABLE cust
(
    cid INT IDENTITY(100,1),
    cname VARCHAR(20)
);

===============================================================
68. Insert customer A

INSERT INTO cust(cname)
VALUES('A');

===============================================================
69. Insert customer B

INSERT INTO cust(cname)
VALUES('B');

===============================================================
70. Insert customer C

INSERT INTO cust(cname)
VALUES('C');

===============================================================
71. Display all customer records

SELECT *
FROM cust;

===============================================================
72. Extract current year using DATEPART()

SELECT DATEPART(YY,GETDATE());

===============================================================
73. Extract current month using DATEPART()

SELECT DATEPART(MM,GETDATE());

===============================================================
74. Extract current day using DATEPART()

SELECT DATEPART(DD,GETDATE());

===============================================================
75. Extract current weekday using DATEPART()

SELECT DATEPART(DW,GETDATE());

===============================================================
76. Extract current day of year using DATEPART()

SELECT DATEPART(DY,GETDATE());

===============================================================
77. Extract current hour using DATEPART()

SELECT DATEPART(HH,GETDATE());

===============================================================
78. Extract current minute using DATEPART()

SELECT DATEPART(MI,GETDATE());

===============================================================
79. Extract current second using DATEPART()

SELECT DATEPART(SS,GETDATE());

===============================================================
80. Extract current quarter using DATEPART()

SELECT DATEPART(QQ,GETDATE());

===============================================================