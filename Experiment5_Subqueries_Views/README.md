# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="959" height="671" alt="image" src="https://github.com/user-attachments/assets/8958c2df-13b1-49d5-9595-c2bf61246cf0" />

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```

**Output:**

<img width="1224" height="433" alt="image" src="https://github.com/user-attachments/assets/d2b51cc3-9c4f-4cb5-b037-9eda0dcb43db" />


**Question 2**
---
<img width="1186" height="627" alt="image" src="https://github.com/user-attachments/assets/95e72ccf-4fda-402e-a463-ffcd9895195e" />


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM ORDERS
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM ORDERS
    WHERE ord_date = '2012-10-10'
);

```

**Output:**

<img width="1230" height="444" alt="image" src="https://github.com/user-attachments/assets/c2159405-4c08-4e3c-a1c9-2bbac343eb89" />


**Question 3**
---
<img width="1188" height="794" alt="image" src="https://github.com/user-attachments/assets/c0406e8d-eedf-41d8-9ba4-7c5d4b3506c7" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
  ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**

<img width="1227" height="444" alt="image" src="https://github.com/user-attachments/assets/ea0cbf56-4c95-4b48-82fb-b00f4dc58447" />


**Question 4**
---
<img width="1247" height="494" alt="image" src="https://github.com/user-attachments/assets/b01ea29f-9cf5-416c-a198-deecbbc37bfe" />

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s
  ON o.salesman_id = s.salesman_id
WHERE s.name = 'Paul Adam';

```

**Output:**

<img width="1232" height="363" alt="image" src="https://github.com/user-attachments/assets/e9edc504-3722-42e6-b463-5e793b4b94c8" />


**Question 5**
---
<img width="1195" height="449" alt="image" src="https://github.com/user-attachments/assets/8f1d44c1-f4dc-4a0e-bdff-1d184a680344" />

```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);

```

**Output:**

<img width="761" height="391" alt="image" src="https://github.com/user-attachments/assets/ef698270-0c1e-4144-b13f-b7862c1d860f" />


**Question 6**
---
<img width="1020" height="512" alt="image" src="https://github.com/user-attachments/assets/eb7a8b20-4e3c-4fa0-8d64-ac09c644bd1c" />


```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);

```

**Output:**

<img width="945" height="382" alt="image" src="https://github.com/user-attachments/assets/c0664e13-7168-4a76-935c-e29ba06b1bfe" />


**Question 7**
---
<img width="1164" height="730" alt="image" src="https://github.com/user-attachments/assets/e3b41e83-0c71-410b-a7e4-c61c41265f4b" />

```sql
SELECT orders.ord_no,
       orders.purch_amt,
       orders.ord_date,
       orders.customer_id,
       orders.salesman_id
FROM orders
JOIN salesman
  ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'London';

```

**Output:**

<img width="1241" height="398" alt="image" src="https://github.com/user-attachments/assets/ab73a35c-7539-48f6-92ea-d080342fd4ac" />

**Question 8**
---
<img width="1154" height="727" alt="image" src="https://github.com/user-attachments/assets/16e28668-b171-4ab0-bc97-3b28d27a5851" />

```sql
SELECT *
FROM customer
WHERE customer_id = (
    (SELECT salesman_id FROM salesman WHERE name = 'Mc Lyon') - 2001
);

```

**Output:**

<img width="1243" height="297" alt="image" src="https://github.com/user-attachments/assets/d7fed460-4d65-4127-9aeb-3718bd9c5b6b" />


**Question 9**
---
<img width="1180" height="711" alt="image" src="https://github.com/user-attachments/assets/26db4371-9815-4c9e-9129-c042aeaf162a" />

```sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c
  ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;

```

**Output:**

<img width="666" height="454" alt="image" src="https://github.com/user-attachments/assets/8143bff1-0f73-4c16-a173-72fb20bcccae" />


**Question 10**
---
<img width="1095" height="676" alt="image" src="https://github.com/user-attachments/assets/ad434b4c-c1d5-4ccb-b048-72efab3ce676" />

```sql
-- Paste your SQL code below for Question 10
```

**Output:**

![Output10](output.png)

**SEB Grades**

<img width="1003" height="73" alt="image" src="https://github.com/user-attachments/assets/c8fb77dd-61fb-4d67-a0a1-dfadcf123130" />

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
