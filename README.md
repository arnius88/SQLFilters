<h1>Apply Filters to SQL</h1>


<h2>Project description and scenario</h2>

I am working as part of the security team of a large company. My current assignment is to investigate some suspicious login attempts. Furthermore, I was asked to identify employees belonging to specified department who require their machines to be updated.
The task required to query the company’s database using SQL in order to retrieve the information needed and complete the investigation.
<br />

<h2>Project walk-through:</h2>

<h3><p align="center">Retrieve after hours failed login attempts:</h3>

In this example, I was asked to investigate any failed login attempts that happened after working hours (later than 18:00).
<br />

In order to carry out the investigation, I queried the log using the following syntax:
<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/ae46cd20-93d7-43b1-9f25-520af17542be">
<br />

The first part of the screenshot includes a query that filters for failed login attempts occurred after 18:00:
<br />

```
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE
```
<br />

I started by selecting all data belonging to the `log_in_attempts` table. Then I used a `WHERE` clause with a first condition `login_time > '18:00'`, requesting to filter for the login attempts that occurred after 18:00. This is followed by an `AND` operator with the second condition `success = FALSE` which asks to filter for failed attempts only.
The second part of the screenshot includes a quick view of the output obtained.<br />

<h3><p align="center">Retrieve login attempts on specific dates:</h3>

I was asked to investigate any login activity that happened on 2022-05-09 or on the day before due to a suspicious event that took place on 2022-05-09.<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/c2964955-1f36-4c6e-812a-68e8d253ec33"><br />

In order to examine any suspicious login attempt involving two specific dates I used the following syntax (also visible in the first part of the screenshot):
<br />

```
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08'
```
<br />


I started by selecting all data belonging to the `log_in_attempts` table. Then I asked SQL to find login attempts that occurred either on `'2022-05-09'` or on `'2022-05-08'`.
To do this, I used a `WHERE` clause with a first condition `login_date = '2022-05-09'`, which filters for logins on 2022-05-09. Then I employed the operator `OR` followed by the second condition `login_date = '2022-05-08'`, to filter for any login attempts that occurred on 2022-05-08.
The second part of the screenshot includes a quick view of the output obtained.
<br />

<h3><p align="center">Retrieve login attempts outside of Mexico:</h3>

Some suspicious login activities were detected. However, the login attempts are almost certainly not coming from Mexico. For this reason, I was asked to investigate login attempts from locations that are _not_ Mexico.
<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/2fee359d-c99f-4b3e-b2ca-2440a305c27e"><br />

To complete the investigation, I used the below query (also visible in the first part of the above screenshot):
<br />

```
SELECT * 
FROM log_in_attempts 
WHERE NOT country LIKE 'MEX%'
```
<br />

Firstly, I asked SQL to select all data belonging to the `log_in_attempts` table. The rest of the query retrieves any login attempts that were made outside of Mexico. To do this, I used a `WHERE` clause in conjunction with the `NOT` operator to look for countries (included in the `country` column) other than Mexico. This is followed by `LIKE`, which is the operator that allows to look for patterns when combined with wildcards such as `%`. Since the `country` column contains rows including both `Mexico` and `Mex` I felt it was appropriate to use the `%` wildcard following `MEX` in order to exclude both types of results.
The second part of the screenshot shows a snippet of the output.
<br />

<h3><p align="center">Retrieve employees in Marketing:</h3>

My team wanted to perform a security updates on specific machines in the Marketing department. I was responsible for getting information on the machines to update.<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/2a97fa1b-d06a-4903-b2c1-dd6ce43f11d3"><br />

To achieve this I employed the following syntax, also visible in first part of the above screenshot:<br />

```
SELECT * 
FROM employees 
WHERE department = 'Marketing' AND office LIKE 'East%'
```
<br />

Firstly, I asked SQL to select all data belonging to the `employees` table. The following line begins with `WHERE` followed by the condition `department = 'Marketing'`, which filters for employees belonging to the marketing department. Then, I included the `AND` operator followed by the condition `office LIKE 'East%'` to specify that I am looking for employees belonging to Marketing that are also working in any office located in the East building. Once again, I found appropriate to use the `%` wildcard in conjunction with `LIKE` because each East building offices are followed by specific identification numbers and I needed to include them all in the final output (visible in the second part of the screenshot).
<br />

<h3><p align="center">Retrieve employees in Finance or Sales:</h3>

My team needed to perform a different security update on machines for employees in the Sales and Finance departments. The below shows how I used filters in SQL to create a query that identifies all employees in the Sales or Finance departments.<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/520b94e1-1d53-4c4d-9b6e-fcbc414e3bed"><br />

As shown in the screenshot, I completed this task by using the following syntax:<br />

```
SELECT * 
FROM employees 
WHERE department = 'Finance' OR department = 'Sales'
```
<br />

The query helped me to retrieve information about employees either belonging to the Finance or Sales team. I started by selecting all data belonging to the `employees` table. Then, I included the `WHERE` clause in conjunction with the `OR` operator to filter through the `department` column and retrieve the data needed. In this case, I user `OR` because I was interested in retrieving information about employees belonging to either department. The two conditions allowed me to be specific on the department that I needed to investigate.
<br />

<h3><p align="center">Retrieve all employees not in IT:</h3>

My team needed to perform a security update on machines who did not belong to employees from the Information Technology department. To make the update, I first had to get information on these employees.
<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/41b468f4-1913-4a1b-a55d-164b2efb7f88"><br />

The following demonstrates how I used SQL to retrieve information regarding employees in departments that were not Information Technology:
<br />

```
SELECT * 
FROM employees 
WHERE NOT department = 'Information Technology'
```
<br />

After selecting all data included in the `employees` table, I used `WHERE NOT` followed by the condition `department = 'Information Technology'` to get an inclusive list of employees not belonging to the Information Technology department. A snippet of the output can be seen in the second part of the above screenshot.
<br />

<h3><p align="center">Project summary:</h3>

This project has allowed me to showcase my skills with SQL, in particular the use of advanced filters. This involves the correct use of operators such as `AND`, `OR` and `NOT` based on the specific information that needs to be mined from the database. I also demonstrated how to use `LIKE` and the percentage sign (`%`) wildcard to filter for patterns.
<br />



