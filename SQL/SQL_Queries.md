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
===============================================================
81. Display employees joined in years 1980, 1983 and 1985

SELECT *
FROM emp
WHERE DATEPART(YY,hiredate) IN (1980,1983,1985);

===============================================================
82. Display employees who joined in a leap year

SELECT *
FROM emp
WHERE DATEPART(YY,hiredate) % 4 = 0;

===============================================================
83. Display employees who joined in January, April and December

SELECT *
FROM emp
WHERE DATEPART(MM,hiredate) IN (1,4,12);

===============================================================
84. Display employees who joined in 2nd quarter of 1981

SELECT *
FROM emp
WHERE DATEPART(QQ,hiredate) = 2
AND DATEPART(YY,hiredate) = 1981;

===============================================================
85. Display employee name and year of joining

SELECT ename,
       DATEPART(YY,hiredate) AS year_of_join
FROM emp;

===============================================================
86. Display employee name and joining day

SELECT ename,
       DATENAME(DW,hiredate) AS day
FROM emp;

===============================================================
87. Display employees who joined on Sunday

SELECT *
FROM emp
WHERE DATENAME(DW,hiredate) = 'Sunday';

===============================================================
88. Display employees who joined on Sunday using DATEPART

SELECT *
FROM emp
WHERE DATEPART(DW,hiredate) = 1;

===============================================================
89. Display on which day India got Independence

SELECT DATENAME(DW,'1947-08-15');

===============================================================
90. Display current date in DD-MM-YYYY format

SELECT FORMAT(GETDATE(),'dd-MM-yyyy');

===============================================================
91. Display current time

SELECT FORMAT(GETDATE(),'hh:mm:ss');

===============================================================
92. Display current date with short day name

SELECT FORMAT(GETDATE(),'dd-MM-yyyy ddd');

===============================================================
93. Display current date with full day name

SELECT FORMAT(GETDATE(),'dd-MM-yyyy dddd');

===============================================================
94. Display current date in DD-MMM-YYYY format

SELECT FORMAT(GETDATE(),'dd-MMM-yyyy');

===============================================================
95. Display current date in DD-MMMM-YYYY format

SELECT FORMAT(GETDATE(),'dd-MMMM-yyyy');

===============================================================
96. Display employee name and hire date in MM/DD/YYYY format

SELECT ename,
       FORMAT(hiredate,'MM/dd/yyyy') AS hiredate
FROM emp;

===============================================================
97. Display employees who joined today

SELECT *
FROM emp
WHERE hiredate = FORMAT(GETDATE(),'yyyy-MM-dd');

===============================================================
98. Display date after 10 days from today

SELECT DATEADD(DD,10,GETDATE());

===============================================================
99. Display date before 10 days from today

SELECT DATEADD(DD,-10,GETDATE());

===============================================================
100. Display date after 2 months from today

SELECT DATEADD(MM,2,GETDATE());

===============================================================
101. Display employees who joined in last 6 months

SELECT *
FROM emp
WHERE hiredate BETWEEN DATEADD(MM,-6,GETDATE())
AND GETDATE();

===============================================================
102. Display employees who joined in last 5 years

SELECT *
FROM emp
WHERE hiredate >= DATEADD(YY,-5,GETDATE());

===============================================================
103. Display difference in years between 18-Jun-2025 and today

SELECT DATEDIFF(YY,'2025-06-18',GETDATE());

===============================================================
104. Display difference in months between 18-Jun-2025 and today

SELECT DATEDIFF(MM,'2025-06-18',GETDATE());

===============================================================
105. Display difference in days between 18-Jun-2025 and today

SELECT DATEDIFF(DD,'2025-06-18',GETDATE());

===============================================================
106. Display employee name and experience in years

SELECT ename,
       DATEDIFF(YY,hiredate,GETDATE()) AS experience
FROM emp;

===============================================================
107. Display employees having experience greater than 45 years

SELECT *
FROM emp
WHERE DATEDIFF(YY,hiredate,GETDATE()) > 45;

===============================================================
108. Display employee experience in years and months

SELECT ename,
       DATEDIFF(MM,hiredate,GETDATE())/12 AS years,
       DATEDIFF(MM,hiredate,GETDATE())%12 AS months
FROM emp;

===============================================================
109. Display last day of current month

SELECT EOMONTH(GETDATE());

===============================================================
110. Display last day of next month

SELECT EOMONTH(GETDATE(),1);

===============================================================
111. Display last day of previous month

SELECT EOMONTH(GETDATE(),-1);

===============================================================
112. Display first day of next month

SELECT DATEADD(DD,1,EOMONTH(GETDATE()));

===============================================================
113. Display first day of current month

SELECT DATEADD(DD,1,EOMONTH(GETDATE(),-1));

===============================================================
114. Convert string to uppercase

SELECT UPPER('hello');

===============================================================
115. Convert string to lowercase

SELECT LOWER('HELLO');

===============================================================
116. Display employee names in lowercase with salary

SELECT LOWER(ename) AS ename,
       sal
FROM emp;

===============================================================
117. Convert all employee names to lowercase in table

UPDATE emp
SET ename = LOWER(ename);

===============================================================
118. Display length of string 'hello welcome'

SELECT LEN('hello welcome');

===============================================================
119. Display employees whose names contain exactly 4 characters

SELECT *
FROM emp
WHERE LEN(ename) = 4;

===============================================================
120. Display employee name and length where name length is greater than 4

SELECT ename,
       LEN(ename) AS length
FROM emp
WHERE LEN(ename) > 4
ORDER BY LEN(ename) ASC;

===============================================================
121. Display first 5 characters of the string 'hello welcome'

SELECT LEFT('hello welcome',5);

===============================================================
122. Display last 7 characters of the string 'hello welcome'

SELECT RIGHT('hello welcome',7);

===============================================================
123. Display employees whose names start with 'S'

SELECT *
FROM emp
WHERE LEFT(ename,1) = 's';

===============================================================
124. Display employees whose names end with 'S'

SELECT *
FROM emp
WHERE RIGHT(ename,1) = 's';

===============================================================
125. Display employees whose names start and end with the same character

SELECT *
FROM emp
WHERE LEFT(ename,1) = RIGHT(ename,1);

===============================================================
126. Generate employee email IDs

SELECT empno,
       ename,
       LEFT(ename,3) + LEFT(CAST(empno AS VARCHAR),3) + '@tcs.com' AS emailid
FROM emp;

===============================================================
127. Add EmailID column to EMP table

ALTER TABLE emp
ADD emailid VARCHAR(20);

===============================================================
128. Update EmailID column for all employees

UPDATE emp
SET emailid = LEFT(ename,3) + LEFT(CAST(empno AS VARCHAR),3) + '@tcs.com';

===============================================================
129. Display 5 characters starting from 7th position

SELECT SUBSTRING('hello welcome',7,5);

===============================================================
130. Display string from 7th position till end

SELECT SUBSTRING('hello welcome',7,LEN('hello welcome'));

===============================================================
131. Display 3 characters from 10th position

SELECT SUBSTRING('hello welcome',10,3);

===============================================================
132. Find position of character 'O'

SELECT CHARINDEX('O','HELLO WELCOME');

===============================================================
133. Find position of character 'K'

SELECT CHARINDEX('K','HELLO WELCOME');

===============================================================
134. Find position of second occurrence of 'O'

SELECT CHARINDEX('O','HELLO WELCOME',6);

===============================================================
135. Find position of first space

SELECT CHARINDEX(' ','HELLO WELCOME');

===============================================================
136. Display Customer ID, First Name and Last Name

SELECT cid,
       SUBSTRING(cname,1,CHARINDEX(' ',cname)-1) AS fname,
       SUBSTRING(cname,CHARINDEX(' ',cname)+1,LEN(cname)) AS lname
FROM cust;

===============================================================
137. Reverse the string 'HELLO'

SELECT REVERSE('HELLO');

===============================================================
138. Display employees whose names are palindrome

SELECT *
FROM emp
WHERE ename = REVERSE(ename);

===============================================================
139. Repeat '*' 10 times

SELECT REPLICATE('*',10);

===============================================================
140. Mask employee salary using '*'

SELECT ename,
       REPLICATE('*',LEN(CAST(sal AS VARCHAR))) AS sal
FROM emp;

===============================================================
141. Mask account number except last 4 digits

SELECT REPLICATE('X',LEN(accno)-4) + RIGHT(accno,4)
FROM accounts;

===============================================================
142. Replace 'ELL' with 'ABC'

SELECT REPLACE('HELLO','ELL','ABC');

===============================================================
143. Replace all 'L' with 'ABC'

SELECT REPLACE('HELLO','L','ABC');

===============================================================
144. Remove '@' symbols from string

SELECT REPLACE('@@HE@@LL@O@@','@','');

===============================================================
145. Replace year 1980 with 2020 in HireDate

UPDATE emp
SET hiredate = REPLACE(hiredate,'1980','2020');

===============================================================
146. Replace month 02 with 03 in HireDate

UPDATE emp
SET hiredate = REPLACE(hiredate,'-02-','-03-');

===============================================================
147. Translate E->A, L->B and O->C

SELECT TRANSLATE('HELLO','ELO','ABC');

===============================================================
148. Encrypt employee salary

SELECT ename,
       TRANSLATE(CAST(sal AS VARCHAR),
                 '0123456789.',
                 '$bT*!&#@^%+') AS sal
FROM emp;

===============================================================
149. Remove all special characters

SELECT REPLACE(
       TRANSLATE('!@HE#$LL%^O&*',
                 '!@#$%^&*',
                 '********'),
       '*','');

===============================================================
150. Display employees whose names start with vowels

SELECT *
FROM emp
WHERE LEFT(ename,1) IN ('a','e','i','o','u');

===============================================================
151. Display absolute value of -10

SELECT ABS(-10);

===============================================================
152. Find 3 raised to the power 2

SELECT POWER(3,2);

===============================================================
153. Find square root of 25

SELECT SQRT(25);

===============================================================
154. Find square of 5

SELECT SQUARE(5);

===============================================================
155. Round 38.5678 to nearest integer

SELECT ROUND(38.5678,0);

===============================================================
156. Round 38.4678 to 2 decimal places

SELECT ROUND(38.4678,2);

===============================================================
157. Round 386 to nearest tens

SELECT ROUND(386,-1);

===============================================================
158. Round employee salaries to nearest hundred

UPDATE emp
SET sal = ROUND(sal,-2);

===============================================================
159. Display ceiling value of 3.1

SELECT CEILING(3.1);

===============================================================
160. Display floor value of 3.9

SELECT FLOOR(3.9);

===============================================================
161. Convert decimal value 10.5 to Integer

SELECT CAST(10.5 AS INT);

===============================================================
162. Convert current DateTime to Date

SELECT CAST(GETDATE() AS DATE);

===============================================================
163. Display employee name and salary as a sentence

SELECT ename + ' earns ' + CAST(sal AS VARCHAR) AS details
FROM emp;

===============================================================
164. Display employee name, hire date and job as a sentence

SELECT ename + ' joined on ' +
       CAST(hiredate AS VARCHAR) +
       ' as ' + job AS details
FROM emp;

===============================================================
165. Convert decimal value 10.5 to Integer using CONVERT

SELECT CONVERT(INT,10.5);

===============================================================
166. Convert current DateTime to Date using CONVERT

SELECT CONVERT(DATE,GETDATE());

===============================================================
167. Display current date in MM/DD/YYYY format

SELECT CONVERT(VARCHAR,GETDATE(),101);

===============================================================
168. Display current date in DD-MM-YYYY format

SELECT CONVERT(VARCHAR,GETDATE(),105);

===============================================================
169. Display current date in MM-DD-YYYY format

SELECT CONVERT(VARCHAR,GETDATE(),110);

===============================================================
170. Display current time in HH:MI:SS format

SELECT CONVERT(VARCHAR,GETDATE(),114);

===============================================================
171. Display employee names with hire date in DD-MM-YYYY format

SELECT ename,
       CONVERT(VARCHAR,hiredate,105) AS hiredate
FROM emp;

===============================================================
172. Display salaries with thousand separator

SELECT ename,
       CONVERT(VARCHAR,sal,1) AS salary
FROM emp;

===============================================================
173. Display salaries in Indian currency format

SELECT ename,
       FORMAT(sal,'C','en-IN') AS salary
FROM emp;

===============================================================
174. Display salaries in US currency format

SELECT ename,
       FORMAT(sal,'C','en-US') AS salary
FROM emp;

===============================================================
175. Display ISNULL() example with non-null value

SELECT ISNULL(100,200);

===============================================================
176. Display ISNULL() example with NULL value

SELECT ISNULL(NULL,200);

===============================================================
177. Display employee total salary including commission

SELECT ename,
       sal,
       comm,
       sal + ISNULL(comm,0) AS totalsal
FROM emp;

===============================================================
178. Display commission as 'N/A' when commission is NULL

SELECT ename,
       sal,
       ISNULL(CAST(comm AS VARCHAR),'N/A') AS comm
FROM emp;

===============================================================
179. Display first non-null value using COALESCE

SELECT COALESCE(NULL,100,NULL,200);

===============================================================
180. Display first non-null value using COALESCE

SELECT COALESCE(100,NULL,200,NULL);

===============================================================
181. Display Customer ID, Customer Name and Contact

SELECT cid,
       cname,
       COALESCE(phone,emailid,addr) AS contact
FROM cust;

===============================================================
182. Display employee ranks based on salary using RANK()

SELECT empno,
       ename,
       sal,
       RANK() OVER(ORDER BY sal DESC) AS rnk
FROM emp;

===============================================================
183. Display employee ranks based on salary using DENSE_RANK()

SELECT empno,
       ename,
       sal,
       DENSE_RANK() OVER(ORDER BY sal DESC) AS rnk
FROM emp;

===============================================================
184. Display employee ranks based on salary and hire date

SELECT empno,
       ename,
       hiredate,
       sal,
       DENSE_RANK() OVER(ORDER BY sal DESC,hiredate ASC) AS rnk
FROM emp;

===============================================================
185. Display department-wise employee ranks

SELECT empno,
       ename,
       sal,
       deptno,
       DENSE_RANK() OVER(PARTITION BY deptno ORDER BY sal DESC) AS rnk
FROM emp;

===============================================================
186. Display row numbers based on salary

SELECT empno,
       ename,
       sal,
       ROW_NUMBER() OVER(ORDER BY sal DESC) AS rno
FROM emp;

===============================================================
187. Display row numbers based on employee number

SELECT empno,
       ename,
       sal,
       ROW_NUMBER() OVER(ORDER BY empno) AS rno
FROM emp;

===============================================================
188. Display the 5th row from EMP table

WITH E AS
(
    SELECT empno,
           ename,
           sal,
           ROW_NUMBER() OVER(ORDER BY empno) AS rno
    FROM emp
)
SELECT *
FROM E
WHERE rno = 5;

===============================================================
189. Display 5th, 10th and 15th rows

WITH E AS
(
    SELECT empno,
           ename,
           sal,
           ROW_NUMBER() OVER(ORDER BY empno) AS rno
    FROM emp
)
SELECT *
FROM E
WHERE rno IN (5,10,15);

===============================================================
190. Display rows from 5th to 10th

WITH E AS
(
    SELECT empno,
           ename,
           sal,
           ROW_NUMBER() OVER(ORDER BY empno) AS rno
    FROM emp
)
SELECT *
FROM E
WHERE rno BETWEEN 5 AND 10;

===============================================================
191. Display even row numbers

WITH E AS
(
    SELECT empno,
           ename,
           sal,
           ROW_NUMBER() OVER(ORDER BY empno) AS rno
    FROM emp
)
SELECT *
FROM E
WHERE rno % 2 = 0;

===============================================================
192. Display odd row numbers

WITH E AS
(
    SELECT empno,
           ename,
           sal,
           ROW_NUMBER() OVER(ORDER BY empno) AS rno
    FROM emp
)
SELECT *
FROM E
WHERE rno % 2 = 1;

===============================================================
193. Display previous employee salary using LAG()

SELECT empno,
       ename,
       sal,
       LAG(sal,1) OVER(ORDER BY empno) AS previous_salary
FROM emp;

===============================================================
194. Display next employee salary using LEAD()

SELECT empno,
       ename,
       sal,
       LEAD(sal,1) OVER(ORDER BY empno) AS next_salary
FROM emp;

===============================================================
195. Display year, population and growth

SELECT year,
       population,
       population - LAG(population,1)
       OVER(ORDER BY year) AS growth
FROM population;

===============================================================
196. Display year, population, previous year population, growth and growth percentage

WITH T AS
(
    SELECT year,
           population,
           LAG(population,1) OVER(ORDER BY year) AS prev_year_pop
    FROM population
)
SELECT year,
       population,
       prev_year_pop,
       population - prev_year_pop AS growth,
       ((population - prev_year_pop) * 100.0 / prev_year_pop) AS pct
FROM T;

===============================================================
197. Display first salary using FIRST_VALUE()

SELECT empno,
       ename,
       sal,
       FIRST_VALUE(sal) OVER(ORDER BY empno) AS first_salary
FROM emp;

===============================================================
198. Display first day's sales amount

SELECT dateid,
       amount,
       FIRST_VALUE(amount) OVER(ORDER BY dateid) AS first_day_amount
FROM sales;

===============================================================
199. Display difference between today's sales and first day's sales

SELECT dateid,
       amount,
       FIRST_VALUE(amount) OVER(ORDER BY dateid) AS first_day_amount,
       amount - FIRST_VALUE(amount) OVER(ORDER BY dateid) AS difference
FROM sales;

===============================================================
200. Divide employees into 4 salary groups using NTILE()

SELECT ename,
       sal,
       NTILE(4) OVER(ORDER BY sal DESC) AS groups
FROM emp;

===============================================================
201. Display maximum salary

SELECT MAX(sal)
FROM emp;

===============================================================
202. Display latest hire date

SELECT MAX(hiredate)
FROM emp;

===============================================================
203. Display employee whose name is last alphabetically

SELECT MAX(ename)
FROM emp;

===============================================================
204. Display minimum salary

SELECT MIN(sal)
FROM emp;

===============================================================
205. Display earliest hire date

SELECT MIN(hiredate)
FROM emp;

===============================================================
206. Display employee whose name is first alphabetically

SELECT MIN(ename)
FROM emp;

===============================================================
207. Display total salary of all employees

SELECT SUM(sal)
FROM emp;

===============================================================
208. Display total salary rounded to nearest thousand

SELECT ROUND(SUM(sal),-3)
FROM emp;

===============================================================
209. Display total salary with Indian currency format

SELECT FORMAT(ROUND(SUM(sal),-3),'C','en-IN') AS totalsal
FROM emp;

===============================================================
210. Display total salary including commission

SELECT SUM(sal + ISNULL(comm,0)) AS totalsal
FROM emp;

===============================================================
211. Display average salary

SELECT AVG(sal)
FROM emp;

===============================================================
212. Display average salary rounded down

SELECT FLOOR(AVG(sal))
FROM emp;