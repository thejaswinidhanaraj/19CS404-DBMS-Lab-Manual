# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="802" height="377" alt="image" src="https://github.com/user-attachments/assets/53f1ccbf-806d-4040-afa1-70e74ae75f49" />

```sql
insert into Customers
values('302','Laura Croft','456 Elm St','Seattle','98101'),
('303','Bruce Wayne','789 Oak St','Gotham','10001');
```

**Output:**

<img width="1196" height="406" alt="image" src="https://github.com/user-attachments/assets/69984bde-d846-4e78-a911-d89daf732588" />

**Question 2**
---
<img width="1195" height="590" alt="image" src="https://github.com/user-attachments/assets/c5e17bde-b408-495f-9f5f-f15fd7ea1bd8" />


```sql
ALTER table customer ADD column email VARCHAR(100);
```

**Output:**

<img width="1231" height="380" alt="image" src="https://github.com/user-attachments/assets/61832030-6ec1-46e6-8b1d-b8345f0b9080" />

**Question 3**
---
<img width="1014" height="346" alt="image" src="https://github.com/user-attachments/assets/81292957-790b-4a51-8715-41206125b0ad" />


```sql
CREATE table Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
Amount REAL check(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER ,
foreign key(OrderID)references Orders(OrderID));
```

**Output:**
<img width="1220" height="328" alt="image" src="https://github.com/user-attachments/assets/fac44ae5-af8f-4cea-80c3-bd4be0290099" />

**Question 4**
---
<img width="883" height="337" alt="image" src="https://github.com/user-attachments/assets/c7ebbf26-c26d-4383-bb49-2bd3f786354f" />


```sql
INSERT into Books(ISBN,Title,Author,Publisher,YearPublished)
select ISBN, Title, Author, Publisher, YearPublished
from Out_of_print_books;

```

**Output:**
<img width="1228" height="320" alt="image" src="https://github.com/user-attachments/assets/92068a25-9b8b-4fce-a333-0502c268f9e9" />

**Question 5**
---
<img width="991" height="236" alt="image" src="https://github.com/user-attachments/assets/297281f5-2cd9-43fd-a23f-5b83fb222d45" />


```sql
insert into products
values(101,'Laptop','Electronics',1500,50);
```

**Output:**
<img width="1236" height="285" alt="image" src="https://github.com/user-attachments/assets/0b503cf3-ae0d-44a4-acd1-8aa94769806c" />

**Question 6**
---
<img width="894" height="419" alt="image" src="https://github.com/user-attachments/assets/9cd01bdd-91ca-4c6d-873b-c1b09a316c8b" />


```sql
create table Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME);

```

**Output:**
<img width="1221" height="413" alt="image" src="https://github.com/user-attachments/assets/7429eb47-91a5-42b4-8965-2825251599b1" />

**Question 7**
---
<img width="1235" height="234" alt="image" src="https://github.com/user-attachments/assets/556bf7b8-5506-4b50-afa7-6d421e3769e6" />


```sql
CREATE TABLE jobs (
    job_id INTEGER PRIMARY KEY,
    job_title TEXT DEFAULT '',
    min_salary INTEGER DEFAULT 8000,
    max_salary INTEGER DEFAULT NULL
);
```

**Output:**
<img width="1224" height="341" alt="image" src="https://github.com/user-attachments/assets/66be2dc9-bed9-4ed0-a9fa-bc4c70d9edc0" />

**Question 8**
---
<img width="1242" height="383" alt="image" src="https://github.com/user-attachments/assets/71893abd-e884-4101-87fe-7bf448fb6aaa" />


```sql
ALTER table employees add salary INTEGER;
```

**Output:**
<img width="1220" height="305" alt="image" src="https://github.com/user-attachments/assets/2c888394-7abe-4aad-a488-5e6bdcc1cc36" />

**Question 9**
---
<img width="977" height="289" alt="image" src="https://github.com/user-attachments/assets/28655557-37e8-436e-8a2b-5331137df80c" />


```sql
CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**
<img width="1214" height="322" alt="image" src="https://github.com/user-attachments/assets/c7f113b6-5ee9-486f-8b5a-1bb78c76acbc" />

**Question 10**
---
<img width="1210" height="454" alt="image" src="https://github.com/user-attachments/assets/798de4bb-b5f9-489a-86cc-8036bff54007" />


```sql
Create Table products(
product_id  INTEGER primary key,
product_name TEXT not NULL,
list_price DECIMAL(10, 2) not NULL,
discount DECIMAL(10, 2) not NULL default 0,
CHECK(list_price>=discount and discount>=0 and list_price>=0)
);
```

**Output:**
<img width="1218" height="300" alt="image" src="https://github.com/user-attachments/assets/dd64b57c-039e-4bd7-9a86-4e8601489932" />

**SEB Grades**

<img width="1058" height="64" alt="image" src="https://github.com/user-attachments/assets/b82401b7-3c7d-4cec-b9bf-9f6c24525fea" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
