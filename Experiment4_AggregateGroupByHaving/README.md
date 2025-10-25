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
How many prescriptions were written for each medication?
```sql
SELECT 
    Medication, 
    COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

<img width="917" height="901" alt="image" src="https://github.com/user-attachments/assets/84c6afe4-0115-416c-9ac6-a0cea8b35149" />

**Question 2**
---
What is the average duration of insurance coverage for patients covered by each insurance company?
```sql
SELECT 
    InsuranceCompany,
    AVG(EndDate - StartDate) AS AvgCoverageDurationDays
FROM Insurance
WHERE StartDate IS NOT NULL 
  AND EndDate IS NOT NULL
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1109" height="816" alt="image" src="https://github.com/user-attachments/assets/aed5717f-40a5-4a52-bad1-d6f14bb96197" />

**Question 3**
---
How many patients are there in each city?
```sql
SELECT 
    Address, 
    COUNT(*) AS TotalPatients
FROM Patients
WHERE Address IS NOT NULL
GROUP BY Address;
```

**Output:**

<img width="729" height="478" alt="image" src="https://github.com/user-attachments/assets/70b634ee-a0d2-4279-9cad-31667bcfa1ac" />

**Question 4**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.
```sql
SELECT 
    COUNT(DISTINCT customer_id) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="463" height="347" alt="image" src="https://github.com/user-attachments/assets/64517285-41b7-4e83-accd-1ec0d2234d1f" />

**Question 5**
---
Write a SQL query to find the customer with longest name?
```sql
SELECT 
    name,
    LENGTH(name) AS length
FROM customer
ORDER BY length DESC
LIMIT 1;
```

**Output:**

<img width="771" height="356" alt="image" src="https://github.com/user-attachments/assets/9c934bda-cf8c-4cbb-8b87-094babb3883a" />

**Question 6**
---
Write a SQL query to  find the average salary of all employees?


```sql
SELECT 
    AVG(income) AS Average_Salary
FROM employee;
```

**Output:**

<img width="572" height="361" alt="image" src="https://github.com/user-attachments/assets/0a63a7ab-3c5a-42c2-98b3-f3c8a5d2c6bb" />

**Question 7**
---
Write a SQL query to find the Fruit with the lowest available quantity.


```sql
SELECT 
    name AS fruit_name,
    inventory AS lowest_quantity
FROM fruits
ORDER BY inventory ASC
LIMIT 1;
```

**Output:**

<img width="806" height="355" alt="image" src="https://github.com/user-attachments/assets/66864d23-1f69-4517-a018-c14b71ba5f97" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.


```sql
SELECT 
    city,
    SUM(income) AS Income
FROM employee
GROUP BY city
HAVING SUM(income) > 200000;
```

**Output:**

<img width="659" height="627" alt="image" src="https://github.com/user-attachments/assets/ed415e45-2012-419e-84e8-06bda2dcd6ff" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.


```sql
SELECT 
    age,
    MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income) < 1000000;
```

**Output:**

<img width="658" height="496" alt="image" src="https://github.com/user-attachments/assets/7f7c38a9-ffcc-4c8f-b28a-59d0b11d9190" />

**Question 10**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.


```sql
SELECT 
    category_id,
    SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;
```

**Output:**

<img width="709" height="398" alt="image" src="https://github.com/user-attachments/assets/ce4c1b1c-2186-401a-ad0f-0e77f26295f2" />

<img width="2534" height="1479" alt="image" src="https://github.com/user-attachments/assets/62aa4ab7-f8b9-40f2-a1aa-0330901d12af" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
