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
Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

```sql
SELECT 
    p.date_of_birth,
    a.appointment_id,
    a.patient_id,
    a.doctor_id,
    a.appointment_date
FROM patients p
INNER JOIN appointments a
    ON p.patient_id = a.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

![Output1](output.png)

**Question 2**
---
Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column. Include conditions to filter for patients discharged between '2024-03-01' and '2024-03-31' but not admitted during the same period.

```sql
SELECT 
    p.first_name,
    s.*
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id
WHERE p.discharge_date BETWEEN '2024-03-01' AND '2024-03-31'
  AND (p.admission_date < '2024-03-01' OR p.admission_date > '2024-03-31');
```

**Output:**

![Output2](output.png)

**Question 3**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS "Salesman",
    s.city AS "salesmancity"
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE c.grade < 300 OR c.grade IS NULL
ORDER BY c.customer_id ASC;
```

**Output:**

![Output3](output.png)

**Question 4**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```sql
-- Paste your SQL code below for Question 4
```

**Output:**

![Output4](output.png)

**Question 5**
---
-- Paste Question 5 here

```sql
-- Paste your SQL code below for Question 5
```

**Output:**

![Output5](output.png)

**Question 6**
---
-- Paste Question 6 here

```sql
-- Paste your SQL code below for Question 6
```

**Output:**

![Output6](output.png)

**Question 7**
---
-- Paste Question 7 here

```sql
-- Paste your SQL code below for Question 7
```

**Output:**

![Output7](output.png)

**Question 8**
---
-- Paste Question 8 here

```sql
-- Paste your SQL code below for Question 8
```

**Output:**

![Output8](output.png)

**Question 9**
---
-- Paste Question 9 here

```sql
-- Paste your SQL code below for Question 9
```

**Output:**

![Output9](output.png)

**Question 10**
---
-- Paste Question 10 here

```sql
-- Paste your SQL code below for Question 10
```

**Output:**

![Output10](output.png)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
