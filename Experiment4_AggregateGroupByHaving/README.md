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
<img width="556" height="519" alt="image" src="https://github.com/user-attachments/assets/c68ac73a-4d13-4ecc-bf4c-2fc02d8978e6" />


```sql
select PatientID,count(PatientID)as TotalAppointments from appointments
group by PatientID-- Paste your SQL code below for Question 1
```

**Output:**

<img width="642" height="612" alt="image" src="https://github.com/user-attachments/assets/b8a5d9f6-a795-4a2b-b656-43caa5a895b5" />


**Question 2**
---
<img width="891" height="459" alt="image" src="https://github.com/user-attachments/assets/d2ec3e6d-ebef-44de-83f1-cf981cd9eb23" />


```sql
select PatientID,count(Medications) as AvgMedications 
from MedicalRecords
group by PatientID;
```

**Output:**

<img width="592" height="598" alt="image" src="https://github.com/user-attachments/assets/3388b2b7-72a1-4c10-b3e9-84160f08e391" />


**Question 3**
---
<img width="950" height="509" alt="image" src="https://github.com/user-attachments/assets/9f633944-b1a0-4f7d-bb94-802178b2b460" />


```sql
select PatientID,count(PatientID)as TotalRecords from MedicalRecords
group by PatientID;
```

**Output:**

<img width="623" height="645" alt="image" src="https://github.com/user-attachments/assets/9c875ef5-20ec-41bf-931d-cf777dce1ad1" />

**Question 4**
---
<img width="914" height="427" alt="image" src="https://github.com/user-attachments/assets/8662c79e-8481-40f7-8224-2f4d0d36f033" />


```sql
select avg(length(email)) as avg_email_length_below_30 from customer where city like "%Mumbai%";
```

**Output:**

<img width="628" height="308" alt="image" src="https://github.com/user-attachments/assets/0b88b976-757a-4032-921a-e6c0efb83b80" />

**Question 5**
---
<img width="703" height="411" alt="image" src="https://github.com/user-attachments/assets/b0c1ae5e-dc36-43e9-9114-1d58659246b3" />


```sql
select count(id) as employees_count from employee
where income>50000;
```

**Output:**

<img width="639" height="272" alt="image" src="https://github.com/user-attachments/assets/5a140000-800d-4a3b-a9bd-311fabce57bb" />


**Question 6**
---
<img width="871" height="466" alt="image" src="https://github.com/user-attachments/assets/6a8dcd09-4320-4a89-bd7f-5a39a65507f3" />


```sql
select sum(inventory) as total_available_amount from fruits
where price>0.5;
```

**Output:**

<img width="591" height="306" alt="image" src="https://github.com/user-attachments/assets/91d56112-211e-4d6f-9ecc-093ed4f1e14b" />

**Question 7**
---
<img width="599" height="451" alt="image" src="https://github.com/user-attachments/assets/a62e2738-f428-44c8-82fa-f4a2f4581b4e" />

```sql
select max(purch_amt) as MAXIMUM from orders;
```

**Output:**

<img width="364" height="304" alt="image" src="https://github.com/user-attachments/assets/c2ee2049-a4e2-4856-8750-8842c07c215c" />


**Question 8**
---
<img width="1204" height="444" alt="image" src="https://github.com/user-attachments/assets/781f0d49-90e8-4cb9-a30b-57be334917e6" />


```sql
select category_id,sum(price) as Total_Cost from products
group by category_id
having Total_Cost>50;
```

**Output:**

<img width="600" height="329" alt="image" src="https://github.com/user-attachments/assets/5eabf6ed-a289-4b2f-8364-1dff2584979e" />


**Question 9**
---
<img width="1252" height="448" alt="image" src="https://github.com/user-attachments/assets/423767ab-45d4-48db-9165-737e85b862a9" />

```sql
select (age/5)*5 as age_group,SUM(salary) from customer1
group by age_group
having SUM(salary)>5000;
```

**Output:**

<img width="531" height="353" alt="image" src="https://github.com/user-attachments/assets/51c1e635-6476-4ca1-ab20-a7940889fa1c" />


**Question 10**
---
<img width="788" height="496" alt="image" src="https://github.com/user-attachments/assets/c387dfdb-1a1e-46d2-b533-48895d0745bc" />


```sql
select address,AVG(salary) from customer1
group by address
having AVG(salary)<15000;
```

**Output:**

<img width="564" height="574" alt="image" src="https://github.com/user-attachments/assets/5f5c3b06-2542-413e-a125-00d604811d1d" />

**SEB Grades**

<img width="1053" height="67" alt="image" src="https://github.com/user-attachments/assets/1d94449c-f117-489f-b28d-4bbed4fdb723" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
