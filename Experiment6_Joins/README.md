# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1203" height="710" alt="image" src="https://github.com/user-attachments/assets/94295a9d-d59b-4a8d-8f10-996e9ddb72a8" />

```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="1238" height="449" alt="image" src="https://github.com/user-attachments/assets/f0a1823f-1b32-48df-9110-be52d734e7b0" />


**Question 2**
---
<img width="1244" height="464" alt="image" src="https://github.com/user-attachments/assets/5002ffca-7c95-4464-9094-8284b5cb50e6" />


```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM 
    salesman s
LEFT JOIN 
    customer c
ON 
    s.salesman_id = c.salesman_id
WHERE 
    s.salesman_id IN (
        SELECT 
            salesman_id
        FROM 
            customer
        GROUP BY 
            salesman_id
        HAVING 
            COUNT(*) > 1
    );

```

**Output:**
<img width="1232" height="670" alt="image" src="https://github.com/user-attachments/assets/c5da89af-4012-4395-b325-4761adb1ae1a" />

**Question 3**
---
<img width="1289" height="840" alt="image" src="https://github.com/user-attachments/assets/d24bc55d-c364-4915-9575-6a36b3a79e64" />

```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**
<img width="1264" height="740" alt="image" src="https://github.com/user-attachments/assets/c0a64dd9-26b8-419e-83db-de11e7e6440b" />


**Question 4**
---
<img width="1226" height="854" alt="image" src="https://github.com/user-attachments/assets/39d62d99-1136-481c-a597-9290c2b0c859" />


```sql
SELECT
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**
<img width="1268" height="821" alt="image" src="https://github.com/user-attachments/assets/daa9a587-f319-4c6d-aa48-b5473fa708f2" />


**Question 5**
---
<img width="1245" height="725" alt="image" src="https://github.com/user-attachments/assets/bf2815f8-ef8f-404c-a08e-229a50fb056e" />


```sql
SELECT 
    p.first_name
FROM 
    patients p
INNER JOIN 
    surgeries s
ON 
    p.patient_id = s.patient_id
WHERE 
    s.surgery_date = '2024-01-15';

```

**Output:**
<img width="486" height="392" alt="image" src="https://github.com/user-attachments/assets/41356078-a4dc-4fd3-b3c7-5df4bdc453d4" />

**Question 6**
---
<img width="1189" height="847" alt="image" src="https://github.com/user-attachments/assets/6b73fc22-a0ac-4156-9233-55bbd87c0a77" />


```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city AS city,
    s.name AS Salesman,
    s.commission AS commission
FROM
    customer  c
INNER JOIN
    salesman  s
ON
    c.salesman_id = s.salesman_id;

```

**Output:**
<img width="1248" height="819" alt="image" src="https://github.com/user-attachments/assets/263bf4bc-96ae-4327-a7fd-5f7b82215d34" />


**Question 7**
---
<img width="1280" height="812" alt="image" src="https://github.com/user-attachments/assets/d74811b2-0e0e-4294-a68a-ab5a5d133750" />

```sql
SELECT
    s.name AS Salesman,
    c.cust_name,
    c.city
FROM
    salesman s
JOIN
    customer c
ON
    s.city = c.city;

```

**Output:**
<img width="961" height="650" alt="image" src="https://github.com/user-attachments/assets/432d7fc2-042f-41c4-94c7-5b783819ee5d" />

**Question 8**
---
<img width="1261" height="711" alt="image" src="https://github.com/user-attachments/assets/d22d8e8a-09bc-453d-9063-3c7bb6304395" />

```sql
SELECT 
    p.first_name,
    s.*
FROM 
    patients p
INNER JOIN 
    surgeries s
ON 
    p.patient_id = s.patient_id
WHERE 
    p.first_name = 'Alice';

```

**Output:**
<img width="1260" height="377" alt="image" src="https://github.com/user-attachments/assets/cd349409-8b08-44b6-9429-f49965a24fa5" />

**Question 9**
---
<img width="1251" height="309" alt="image" src="https://github.com/user-attachments/assets/657f784b-3e57-4c18-a0a0-a5073b9c8c54" />


```sql
SELECT 
    s.*
FROM 
    salesman s
LEFT JOIN 
    customer c
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.cust_name = 'Fabian Johns';

```

**Output:**
<img width="1208" height="347" alt="image" src="https://github.com/user-attachments/assets/2378f18a-5174-4727-a4f8-c7a2e09a5f25" />


**Question 10**
---
<img width="1089" height="867" alt="image" src="https://github.com/user-attachments/assets/4d0d716e-48e6-4f3f-af4e-554cc2460e9b" />

```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM orders   AS o
JOIN customer AS c ON c.customer_id = o.customer_id
JOIN salesman AS s ON s.salesman_id = o.salesman_id;
```

**Output:**
<img width="1326" height="822" alt="image" src="https://github.com/user-attachments/assets/27f5af84-5def-40e7-99f6-649597b1f8b8" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
