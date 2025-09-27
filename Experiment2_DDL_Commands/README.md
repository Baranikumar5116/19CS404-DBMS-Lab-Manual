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
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE NOT NULL,
    CustomerID INTEGER,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```
**Output:**

<img width="1563" height="265" alt="image" src="https://github.com/user-attachments/assets/83b46c90-a873-4f7f-9b4a-d27eb49de030" />



**Question 2**
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

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

<img width="1331" height="198" alt="image" src="https://github.com/user-attachments/assets/2bb96a1c-6047-499f-a97b-b58010afddf8" />

**Question 3**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, Marks) 
VALUES (201, 'David Lee', 'M', 'Physics', 92);
```

**Output:**

<img width="1034" height="171" alt="image" src="https://github.com/user-attachments/assets/2a96eb64-0a40-483f-a1e5-3f37a8d101b2" />

**Question 4**
---
Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT
```sql
CREATE TABLE Reviews (
    ReviewID INTEGER,
    ProductID INTEGER,
    Rating REAL,
    ReviewText TEXT
);
```

**Output:**

<img width="1202" height="272" alt="image" src="https://github.com/user-attachments/assets/cabe7791-6ee2-4da4-ae9a-90df43c53b50" />

**Question 5**
---
Write an SQL command can to add a column named email of type TEXT to the customers table

 
```sql
ALTER TABLE customers
ADD COLUMN email TEXT;

```

**Output:**

<img width="1023" height="200" alt="image" src="https://github.com/user-attachments/assets/17f79160-8f0e-464f-ac87-36b7447802d7" />

**Question 6**
---
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.
```sql
ALTER TABLE Employees
ADD COLUMN salary INTEGER CHECK (salary > 0);
```

**Output:**

<img width="1053" height="206" alt="image" src="https://github.com/user-attachments/assets/e589b5fc-c303-44bf-84e7-98a920671850" />

**Question 7**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001
```sql
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode) 
VALUES
(302, 'Laura Croft', '456 Elm St', 'Seattle', 98101),
(303, 'Bruce Wayne', '789 Oak St', 'Gotham', 10001);
```

**Output:**

<img width="957" height="264" alt="image" src="https://github.com/user-attachments/assets/78100d2e-2e74-4f16-988f-82539a8ca9e8" />

**Question 8**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```sql
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1288" height="207" alt="image" src="https://github.com/user-attachments/assets/7cf48dca-c165-4a26-a2e8-e3ee683cbe9e" />

**Question 9**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```sql
CREATE TABLE contacts (
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK (LENGTH(phone) >= 10)
);
```

**Output:**

<img width="1562" height="234" alt="image" src="https://github.com/user-attachments/assets/8f8180c1-95fd-4147-8f5a-dd7ce101a432" />

**Question 10**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock
```sql
INSERT INTO Products (ProductID, ProductName, Price, Stock)
SELECT ProductID, ProductName, Price, Stock
FROM Discontinued_products;
```

**Output:**

<img width="786" height="199" alt="image" src="https://github.com/user-attachments/assets/6b7d57d5-0d78-459e-87a9-fe7eb399b231" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
