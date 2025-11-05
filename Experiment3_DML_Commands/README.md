# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
<img width="809" height="98" alt="image" src="https://github.com/user-attachments/assets/4b0598b4-86c6-43d6-96d1-9d9d7e874dba" />

```sql
update Customer
set grade=5
where city='Chennai';
```

**Output:**
<img width="1185" height="520" alt="image" src="https://github.com/user-attachments/assets/d7826d51-2c4a-433e-b0e0-7958a63dea12" />


**Question 2**
---
<img width="1204" height="609" alt="image" src="https://github.com/user-attachments/assets/ba7a368f-b410-4462-ab52-777e4c186e6a" />

```sql
update employees
set salary=salary*2
where department_id=20 and job_id LIKE '%MAN';
```

**Output:**
<img width="1192" height="381" alt="image" src="https://github.com/user-attachments/assets/3e969666-c7ea-442a-9185-daa8d454deca" />


**Question 3**
---
<img width="1194" height="613" alt="image" src="https://github.com/user-attachments/assets/709b004b-a81f-4e79-bb33-4e3530b38be3" />

```sql
update Employees
set email='not available',commission_pct=0.55
where department_id=110;
```

**Output:**

<img width="1186" height="405" alt="image" src="https://github.com/user-attachments/assets/2835da06-633a-44cb-a0a8-45839e86ce5e" />


**Question 4**
---
<img width="1223" height="726" alt="image" src="https://github.com/user-attachments/assets/301dd61b-4388-4330-840d-cb00ce442244" />

```sql
update Employees
set salary=salary+500,email='updated'
where job_id='SA_REP' AND commission_pct>0.15;
```

**Output:**

<img width="1187" height="554" alt="image" src="https://github.com/user-attachments/assets/50092ab5-da91-4f48-baa6-4524c086b67b" />


**Question 5**
---
<img width="818" height="468" alt="image" src="https://github.com/user-attachments/assets/84fb9834-5a19-416a-8575-b12c3a9cf3c7" />

```sql
delete from Surgeries
where surgery_id=3;
```

**Output:**

<img width="1195" height="416" alt="image" src="https://github.com/user-attachments/assets/6e509db0-4a6f-4f9f-b093-8cf3602f2fad" />


**Question 6**
---
<img width="1224" height="280" alt="image" src="https://github.com/user-attachments/assets/0992ffb6-f2e4-41e1-a7ad-73546e6509d6" />

```sql
delete from Customer
where WORKING_AREA='New York';
```

**Output:**

<img width="1246" height="671" alt="image" src="https://github.com/user-attachments/assets/06ce061e-279c-426f-a258-5039e49425c0" />


**Question 7**
---
<img width="1208" height="533" alt="image" src="https://github.com/user-attachments/assets/933edf4d-cb6c-4bd8-bd65-966c0a150004" />

```sql
delete from Customer
where (GRADE>2 and PAYMENT_AMT<(SELECT AVG(PAYMENT_AMT)FROM CUSTOMER)) OR OUTSTANDING_AMT>8000;
```

**Output:**

<img width="1239" height="567" alt="image" src="https://github.com/user-attachments/assets/d1949571-213f-436f-bdff-58787d544da4" />


**Question 8**
---
<img width="928" height="547" alt="image" src="https://github.com/user-attachments/assets/11846a74-1ec2-4731-9af4-a3342b5af3e0" />

```sql
DELETE FROM doctors
WHERE specialization is NULL;
```

**Output:**

<img width="1124" height="842" alt="image" src="https://github.com/user-attachments/assets/e13c06f1-942f-4dd1-bc27-cfefefe1b854" />


**Question 9**
---
<img width="1269" height="368" alt="image" src="https://github.com/user-attachments/assets/d8c6e677-3de4-471c-b0c9-b487b62ca6fa" />

```sql
delete from Customer
where CUST_COUNTRY not in ('India','USA');
```

**Output:**

<img width="1249" height="464" alt="image" src="https://github.com/user-attachments/assets/df1fe973-11b0-4128-9f2c-0aee20d59140" />


**Question 10**
---
<img width="675" height="366" alt="image" src="https://github.com/user-attachments/assets/669cf8e2-2022-4ba4-851a-254ac020dad1" />

```sql
select EmpID,EmpPosition,DateOfJoining,Salary
from EmployeePosition
order by salary DESC
LIMIT 3;
```

**Output:**

<img width="860" height="238" alt="image" src="https://github.com/user-attachments/assets/8a696ac0-5e32-4f66-be39-fa7a0232d65b" />


**SEB Grades**

<img width="1023" height="70" alt="image" src="https://github.com/user-attachments/assets/ac139edc-8004-4ea7-ac73-b92de1f3d56b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
