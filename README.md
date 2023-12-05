<h1>Apply Filters to SQL</h1>


<h2>Project description and scenario</h2>

I am working as part of the security team of a large company. My current assignment is to investigate some suspicious login attempts. Furthermore, I was asked to identify employees belonging to specified department who require their machines to be updated.
The task requires to query the company’s database using SQL in order to retrieve the information needed and complete the investigation.
<br />

<h2>Project walk-through:</h2>

<h3><p align="center">Retrieve after hours failed login attempts:</h3>

In this example, I was asked to investigate any failed login attempts that happened after working hours (later than 18:00).
<br />

In order to carry out the investigation, I employed the following queried the log using the following syntax:
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

I started by selecting all data belonging to the `log_in_attempts` table. Then I used a `WHERE` clause with a first condition `login_time > '18:00'`, requesting to filter for the login attempts that occurred strictly after 18:00. This is followed by an `AND` operator with the second condition `success = FALSE` which asks to filter for failed attempts only.
The second part of the screenshot includes a quick view of the output obtained.<br />

<h3><p align="center">Retrieve login attempts on specific dates:</h3>

I was asked to investigate any login activity that happened on 2022-05-09 or on the day before due to a suspicious event that took place on the 2022-05-09.<br />

<img width="80%" alt="image" src="https://github.com/arnius88/SQLFilters/assets/152484037/c2964955-1f36-4c6e-812a-68e8d253ec33"><br />

In order to examine any suspicious login attempt involving two specific dates, as requested by the company, I used the following syntax (also visible in the first part of the screenshot):
<br />

```
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08'
```
<br />


I started by selecting all data belonging to the `log_in_attempts` table. Then I asked SQL to find login dates that occurred either on `'2022-05-09'` or on `'2022-05-08'`.
To do this, I used a `WHERE` clause with a first condition `login_date = '2022-05-09'`, which filters for logins on 2022-05-09. Then I employed the operator `OR` followed by the second condition `login_date = '2022-05-08'`, to filter for any login attempts that occurred on 2022-05-08.
The second part of the screenshot includes a quick view of the output obtained.
<br />



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
