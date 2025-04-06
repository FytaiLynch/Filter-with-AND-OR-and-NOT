# Filter-with-AND-OR-and-NOT

This project demonstrates how to filter SQL table data using logical operators — AND, OR, and NOT — to build more precise and flexible queries. Filters are used in SQL to limit the rows a query returns based on specific conditions, helping extract only the relevant data from a table.


<h2>Task 1: Using the AND operator, retrieve the failed login attempts after business hours. Office hours end at 18:00.</h2>
<p>First, we use SELECT to retrieve all data from the login attempts dataset. The WHERE clause specifies our filter conditions. Since we're targeting failed login attempts after office hours (after 18:00), we apply logical operators to ensure both conditions are met — the login was unsuccessful and the time was after 18:00.
</p>

```sql
SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = FALSE;
```
We could have also said success = 0 here. Because it is a Boolean value, 0 will mean False and 1 will mean True.
<p align="center">
<img src="https://github.com/user-attachments/assets/1052d05c-ae60-40b6-940d-f33dbd565485" alt="Filter with AND and > operators"/>
</p>


<h2>Task 2: Retrieve login attempts on specific dates</h2>
<p>
  Using the columns login_date in the log_in_attempts table, we can find the dates in which failed login attempts were made.
</p>

```sql
SELECT * FROM log_in_attempts WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';
```
<p>
  We use the OR filter because we only want either of the two conditions to be met. If we were looking for login attempts before a certain date, we would instead use the less than (<) operator.
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/db758743-e770-480d-ba6d-13d286777a7b" alt="Filter with OR"/>
</p>

<h2>Task 3: Retrieve login attempts outside of Mexico</h2>
<p>
  We will now investigate logins that did not originate in Mexico. To find this, we have to use the LIKE filter along with the wildcard (%) because we are looking for a pattern of unspecified characters. In this case, it would be 'Mex%' since our table previously displayed Mex and Mexico under the country column.
</p>

```sql
SELECT * FROM log_in_attempts WHERE NOT country LIKE 'Mex%';
```
<p align="center">
<img src="https://github.com/user-attachments/assets/0b838394-d127-4ca4-a264-cd23624584a2" alt="Filter with NOT, LIKE and a wildcard"/>
</p>

<h2>
  Task 4: Retrieve employees in Marketing
</h2>
<p>
  For the following tasks, we need to retrieve information from the department and office columns in the employees table. First, we need to obtain information about employees in the Marketing department who are located in all offices in the East building (Such as East-170 or East-320)
</p>

```sql
SELECT * FROM employees WHERE department = 'Marketing' AND office LIKE 'East%';
```
<p>
  You'll notice that the equal (=) operator wasn't used after office but was instead replaced with LIKE. This is because we cannot use the (=) operator when searching for patterns with the percentage (%) wildcard.
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/e7f2fa93-40bc-47a6-a05a-6a049177fa23" alt="Filter with LIKE and a wildcard"/>
</p>

<h1>
  Task 5: Retrieve employees in Finance or Sales
</h1>
<p>
  We now need to retrieve the records for the employees in either the Finance or Sales department. Even though both conditions are based on the same column, we need to write out both full conditions.
</p>

```sql
SELECT * FROM employees WHERE department = 'Finance' OR department = 'Sales';
```
<p align="center">
<img src="https://github.com/user-attachments/assets/5a75924b-6138-43f8-b33e-4b1aace028f5" alt="Filter with OR"/>
</p>

<h2>
  Task 6: Retrieve all employees not in IT
</h2>
<p>
  Lastly, we need to retrieve information about employees who are not in the IT department. For this, we need to use the NOT filter. 
</p>

```sql
SELECT * FROM employees WHERE NOT department = 'Information Technology';
```
<p>
  We could have also used not equal to (!= or <>) operator instead of using the NOT filter.
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/d31d3db8-5d95-4bef-be88-94f09732c616" alt="Filter with NOT"/>
</p>


