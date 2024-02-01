- views
	- A view is an alternative way of representing data that exists in one or more tables or views. 
	- A view can include all or some of the columns from one or more base tables or existing views
	- You can also change the data in the base table by running insert, update, and delete queries against the view. 
	- When you define a view, the definition of the view is stored. The data that the view represents is stored in the base tables, not by the view itself.
 ```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
- stored procedures
	- A stored procedure is a set of SQL statements that are stored and executed on the database server. 
	- Can write stored procedures in many different languages.
	- Reduction in network traffic because only one call is needed to execute multiple statements. 
	- Improvement in performance because the processing happens on the server where the data is stored, with just the final result being passed back to the client. 
	- Reuse of code because multiple applications can use the same stored procedure for the same job. 
	- Increase in security because 
		a) you do not need to expose all of your table and column information to client-side   developers
		b) you can use server-side logic to validate data before accepting it into the system.
- ACID transactions
	- A transaction is an indivisible unit of work. It can consist of one or more SQL statements, but to be considered successful, either all of those SQL statements must complete successfully, leaving the database in a new stable state, or none must complete, leaving the database as it was before the transaction began. 
	- This types of transaction are called ACID transactions. 
		- Atomic - All changes must be performed successfully or not at all. 
		- Consistent - Data must be in a consistent state before and after the transaction. 
		- Isolated - No other process can change the data while the transaction is running. 
		- Durable - The changes made by the transaction must persist.

<h3><span class="header-link octicon octicon-link"></span>Views</h3><table width="100%">
<tbody><tr>
<th style="width:10%;">
Topic
</th>
<th style="width:30%;">
Syntax
</th>
<th style="width:30%;">
Description
</th>
<th style="width:30%;">
Example
</th>
</tr>

<tr>
<td style="width:10%;">
Create View 
</td>
<td style="width:30%;">
<code>
CREATE VIEW view_name AS SELECT column1, column2, ...
FROM table_name
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
A <code>CREATE VIEW</code> is an alternative way of 
representing data that exists in one or more tables.
</td>
<td style="width:30%;">
<code>
CREATE VIEW EMPSALARY AS 
SELECT EMP_ID, F_NAME, L_NAME, 
B_DATE, SEX, SALARY
FROM EMPLOYEES; 
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Update a View
</td>
<td style="width:30%;">
<code>
CREATE OR REPLACE VIEW view_name AS 
SELECT column1, column2, ... FROM table_name 
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
The <code>CREATE OR REPLACE</code> 
VIEW command updates a view.
</td>
<td style="width:30%;">
<code>
CREATE OR REPLACE VIEW EMPSALARY  AS 
SELECT EMP_ID, F_NAME, L_NAME, B_DATE, SEX, 
JOB_TITLE, MIN_SALARY, MAX_SALARY FROM EMPLOYEES, 
JOBS WHERE EMPLOYEES.JOB_ID = JOBS.JOB_IDENT;
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Drop a View
</td>
<td style="width:30%;">
<code>
DROP VIEW view_name;
</code> <br>
</td>
<td style="width:30%;">
Use the <code>DROP VIEW</code> statement 
to remove a view from the database. 
</td>
<td style="width:30%;">
<code>
DROP VIEW EMPSALARY;
</code>
</td>
</tr>
</tbody></table> 




<h3><span class="header-link octicon octicon-link"></span>Transactions with Db2</h3><table width="100%">
<tbody><tr>
<td style="width:10%;">
Commit command           
</td>
<td style="width:30%;">
<code>

<p>COMMIT;</p>
</code><p><code></code> <br></p>
</td>
<td style="width:30%;"> 
A <code>COMMIT command</code> is used to persist the changes in the database.
<br>

<p>The default terminator for a COMMIT command is semicolon (;).</p>
</td>
<td style="width:30%;">
<code>
CREATE TABLE employee(ID INT, Name VARCHAR(20), City VARCHAR(20), Salary INT, Age INT); 


<p>INSERT INTO employee( ID, Name, City, Salary, Age) VALUES( 1, ‘Priyanka pal’, ‘Nasik’, 36000, 21), (2, ‘Riya chowdary’, ‘Bangalor’, 82000, 29);</p>
<p>SELECT *FROM employee;<br>COMMIT;</p>
</code>
</td>
</tr>


<tr>
<td style="width:10%;">
Rollback command           
</td>
<td style="width:30%;">
<code>

<p>ROLLBACK;</p>
</code><p><code></code> <br></p>
</td>
<td style="width:30%;"> 
A <code>ROLLBACK command</code> is used to rollback the transactions which are not saved in the database.
<br>

<p>The default terminator for a ROLLBACK command is semicolon (;).</p>
</td>
<td style="width:30%;">
<code>
    
<blockquote>
<p>As auto-commit is enabled by default, all transactions will be committed. We need to disable this option to see how rollback works.</p>
</blockquote>
<blockquote>
<p>For db2, we have to disable auto-commit manually. Click the gear icon located on the right side of the SQL Assistant window. Next, select the “On Success” drop-down and choose “commit after the last statement in the script” Remember to save your changes!</p>
</blockquote>
<p><img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/images/Disable_auto-commit.png" alt="disable_auto-commit"></p>
<p>INSERT INTO employee VALUES (3, ‘Swetha Tiwari’, ‘Kanpur’, 38000, 38);</p>
<p>SELECT *FROM employee;<br>ROLLBACK;<br>SELECT *FROM employee;</p>
</code>
</td>
</tr>
</tbody></table> 

<h3><span class="header-link octicon octicon-link"></span>Transactions with MySQL</h3><table width="100%">
<tbody><tr>
<td style="width:10%;">
Commit command           
</td>
<td style="width:30%;">
<code>

<p>COMMIT;</p>
</code><p><code></code> <br></p>
</td>
<td style="width:30%;"> 
A <code>COMMIT command</code> is used to persist the changes in the database.
<br>

<p>The default terminator for a COMMIT command is semicolon (;).</p>
</td>
<td style="width:30%;">
<code>
CREATE TABLE employee(ID INT, Name VARCHAR(20), City VARCHAR(20), Salary INT, Age INT);

<p>START TRANSACTION;</p>
<p>INSERT INTO employee( ID, Name, City, Salary, Age) VALUES( 1, ‘Priyanka pal’, ‘Nasik’, 36000, 21), (2, ‘Riya chowdary’, ‘Bangalor’, 82000, 29);</p>
<p>SELECT *FROM employee;<br>COMMIT;</p>
</code>
</td>
</tr>


<tr>
<td style="width:10%;">
Rollback command           
</td>
<td style="width:30%;">
<code>

<p>ROLLBACK;</p>
</code><p><code></code> <br></p>
</td>
<td style="width:30%;"> 
A <code>ROLLBACK command</code> is used to rollback the transactions which are not saved in the database.
<br>

<p>The default terminator for a ROLLBACK command is semicolon (;).</p>
</td>
<td style="width:30%;">
<code>
    
<blockquote>
<p>As auto-commit is enabled by default, all transactions will be committed. We need to disable this option to see how rollback works. For MySQL use the command “SET autocommit = 0;”</p>
</blockquote>
<p>INSERT INTO employee VALUES (3, ‘Swetha Tiwari’, ‘Kanpur’, 38000, 38);</p>
<p>SELECT *FROM employee;<br>ROLLBACK;<br>SELECT *FROM employee;</p>
</code>
</td>
</tr>
</tbody></table>
 - JOINS
	- A join combines the rows from two or more tables based on a relationship between certain columns in these tables.
	-   To combine data from three or more different tables, you simply add new joins to the SQL statement.
	-   There are two types of table joins: inner join and outer join; and three types of outer joins: left outer join, right outer join, and full outer join.
	-   The most common type of join is the inner join, which matches the results from two tables and returns only the rows that match.
	-   You can use an alias as shorthand for a table or column name.
	-   You can use a self-join to compare rows within the same table.
<h3><span class="header-link octicon octicon-link"></span>Joins</h3><table width="100%">
<tbody><tr>
<th style="width:10%;">
Topic
</th>
<th style="width:30%;">
Syntax
</th>
<th style="width:30%;">
Description
</th>
<th style="width:30%;">
Example
</th>
</tr>

</tbody></table><table width="100%">

<tbody><tr>
<td style="width:10%;">
Cross Join
</td>
<td style="width:30%;">
<code>
SELECT column_name(s)
FROM table1
CROSS JOIN table2;
</code> <br>
</td>
<td style="width:30%;">
The <code>CROSS JOIN</code> is used to generate a paired combination of each row of the first table with each row of the second table.
</td>
<td style="width:30%;">
<code>
SELECT DEPT_ID_DEP, LOCT_ID
FROM DEPARTMENTS 
CROSS JOIN LOCATIONS;
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Inner Join
</td>
<td style="width:30%;">
<code>
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
You can use an <code>inner join</code> in a SELECT statement to retrieve only the rows that satisfy the join conditions on every specified table.
</td>
<td style="width:30%;">
<code>
select E.F_NAME,E.L_NAME, JH.START_DATE 
from EMPLOYEES as E 
INNER JOIN JOB_HISTORY as JH on E.EMP_ID=JH.EMPL_ID 
where E.DEP_ID ='5';	
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Left Outer Join
</td>
<td style="width:30%;">
<code>
SELECT column_name(s)
FROM table1
LEFT OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
The <code>LEFT OUTER JOIN</code> will return all records from the left side table and the matching records from the right table.
</td>
<td style="width:30%;">
<code>
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
from EMPLOYEES AS E 
LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP;
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Right Outer Join
</td>
<td style="width:30%;">
<code>
SELECT column_name(s)
FROM table1
RIGHT OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
The <code>RIGHT OUTER JOIN</code> returns all records from the right table, and the matching records from the left table. 

</td>
<td style="width:30%;">
<code>
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
from EMPLOYEES AS E 
RIGHT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP;
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Full Outer Join
</td>
<td style="width:30%;">
<code>
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
The <code>FULL OUTER JOIN</code> clause results in the inclusion of rows from two tables. If a value is missing when rows are joined, that value is null in the result table.
</td>
<td style="width:30%;">
<code>
select E.F_NAME,E.L_NAME,D.DEP_NAME
from EMPLOYEES AS E 
FULL OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP;
</code>
</td>
</tr>

<tr>
<td style="width:10%;">
Self Join
</td>
<td style="width:30%;">
<code>
SELECT column_name(s)
FROM table1 T1, table1 T2
WHERE condition;
</code> <br>
</td>
<td style="width:30%;">
A <code>self join</code> is regular join but it can be used to joined with itself.
</td>
<td style="width:30%;">
<code>
SELECT B.* FROM EMPLOYEES A JOIN EMPLOYEES B
ON A.MANAGER_ID = B.MANAGER_ID
WHERE A.EMP_ID = 'E1001';
</code>
</td>
</tr>

</tbody></table>  

