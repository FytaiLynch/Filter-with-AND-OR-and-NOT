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
  We use the OR operator because we only want either of the two conditions to be met. If we were looking for login attempts before a certain date, we would instead use the less than (<) operator.
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/db758743-e770-480d-ba6d-13d286777a7b" alt="Filter with OR"/>
</p>


