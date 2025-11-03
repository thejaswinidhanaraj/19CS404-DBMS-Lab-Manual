# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many appointments are scheduled for each patient?

Sample table: Appointments Table

name                  type
--------------------  ----------
AppointmentID         INTEGER
PatientID             INTEGER
DoctorID              INTEGER
AppointmentDateTime   DATETIME
Purpose               TEXT
Status                TEXT
For example:

Result
PatientID   TotalAppointments
----------  -----------------
3           3
5           2
6           1
7           1
10          3


```sql
select PatientID,count(PatientID)as TotalAppointments from appointments
group by PatientID-- Paste your SQL code below for Question 1
```

**Output:**
<img width="642" height="612" alt="image" src="https://github.com/user-attachments/assets/b8a5d9f6-a795-4a2b-b656-43caa5a895b5" />


**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

For example:

Result
PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3


```sql
select PatientID,count(Medications) as AvgMedications 
from MedicalRecords
group by PatientID;
```

**Output:**
<img width="592" height="598" alt="image" src="https://github.com/user-attachments/assets/3388b2b7-72a1-4c10-b3e9-84160f08e391" />


**Question 3**
---
How many medical records are there for each patient?

Sample table:MedicalRecords Table
For example:

Result
PatientID   TotalRecords
----------  ------------
4           4
5           1
6           1
7           1
8           1
10          2


```sql
select PatientID,count(PatientID)as TotalRecords from MedicalRecords
group by PatientID;
```

**Output:**
<img width="623" height="645" alt="image" src="https://github.com/user-attachments/assets/9c875ef5-20ec-41bf-931d-cf777dce1ad1" />

**Question 4**
---
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city
Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length_below_30
-------------------------
14.0


```sql
select avg(length(email)) as avg_email_length_below_30 from customer where city like "%Mumbai%";
```

**Output:**
<img width="628" height="308" alt="image" src="https://github.com/user-attachments/assets/0b88b976-757a-4032-921a-e6c0efb83b80" />

**Question 5**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
employees_count
---------------
8


```sql
select count(id) as employees_count from employee
where income>50000;
```

**Output:**
<img width="639" height="272" alt="image" src="https://github.com/user-attachments/assets/5a140000-800d-4a3b-a9bd-311fabce57bb" />


**Question 6**
---
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 
Note: Inventory attribute contains amount of fruits
Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:
Result
total_available_amount
----------------------
160


```sql
select sum(inventory) as total_available_amount from fruits
where price>0.5;
```

**Output:**
<img width="591" height="306" alt="image" src="https://github.com/user-attachments/assets/91d56112-211e-4d6f-9ecc-093ed4f1e14b" />

**Question 7**
---
Write a SQL query to find the maximum purchase amount.
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001


For example:

Result
MAXIMUM
----------
5760.0


```sql
select max(purch_amt) as MAXIMUM from orders;
```

**Output:**
<img width="364" height="304" alt="image" src="https://github.com/user-attachments/assets/c2ee2049-a4e2-4856-8750-8842c07c215c" />


**Question 8**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.
Sample table: product
For example:

Result
category_id  Total_Cost
-----------  ----------
2            63


```sql
select category_id,sum(price) as Total_Cost from products
group by category_id
having Total_Cost>50;
```

**Output:**
<img width="600" height="329" alt="image" src="https://github.com/user-attachments/assets/5eabf6ed-a289-4b2f-8364-1dff2584979e" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.
Sample table: customer1
For example:

Result
age_group   SUM(salary)
----------  -----------
20          16500
25          16500

```sql
select (age/5)*5 as age_group,SUM(salary) from customer1
group by age_group
having SUM(salary)>5000;
```

**Output:**
<img width="531" height="353" alt="image" src="https://github.com/user-attachments/assets/51c1e635-6476-4ca1-ab20-a7940889fa1c" />


**Question 10**
---
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1
For example:
Result
address     AVG(salary)
----------  -----------
Ahmedabad   2000.0
Bhopal      8500.0
Delhi       1500.0
Hyderabad   4500.0
Indore      10000.0
Kota        2000.0
Mumbai      6500.0


```sql
select address,AVG(salary) from customer1
group by address
having AVG(salary)<15000;
```

**Output:**
<img width="564" height="574" alt="image" src="https://github.com/user-attachments/assets/5f5c3b06-2542-413e-a125-00d604811d1d" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
