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
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.

NURSES TABLE:

ATTRIBUTES - nurse_id, first_name, last_name, department_id

DEPARTMENTS TABLE:

ATTRIBUTES - department_id, department_name
```sql
SELECT 
    n.nurse_id, 
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d 
ON 
    n.department_id = d.department_id
WHERE 
    n.first_name = 'David' 
    AND n.last_name = 'Moore';

```

**Output:**

<img width="731" height="339" alt="image" src="https://github.com/user-attachments/assets/a0dfd071-9380-4ab5-8406-0b7e9d6cc593" />

**Question 2**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)
```sql
SELECT 
    c.cust_name, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o 
ON 
    c.customer_id = o.customer_id;
```

**Output:**

<img width="1046" height="877" alt="image" src="https://github.com/user-attachments/assets/5cbc3ee1-672c-4515-a861-9c7910aa8020" />

**Question 3**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

Sample table: orders

```sql
SELECT 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt, 
    c.cust_name AS "Customer Name", 
    c.grade, 
    s.name AS "Salesman", 
    s.commission
FROM 
    orders o
JOIN 
    customer c 
    ON o.customer_id = c.customer_id
JOIN 
    salesman s 
    ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1321" height="771" alt="image" src="https://github.com/user-attachments/assets/f9851849-647f-4385-b76f-fa1c99d6ceec" />

**Question 4**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

Sample table: customer

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

<img width="1256" height="457" alt="image" src="https://github.com/user-attachments/assets/8bed1c2e-a4fa-49e9-83c5-9f91aa160473" />

**Question 5**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

Sample table: customer

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1214" height="766" alt="image" src="https://github.com/user-attachments/assets/786eed45-2742-460e-b357-6fb8953f3c0d" />

**Question 6**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name AS "name",
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o 
    ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s 
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1057" height="573" alt="image" src="https://github.com/user-attachments/assets/dc33408f-5cea-4a51-9344-5e35229d3b52" />

**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.

Customer Table: (customer_id, cust_name, city, grade, salesman

```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.name = 'Mc Lyon';

```

**Output:**

<img width="1256" height="267" alt="image" src="https://github.com/user-attachments/assets/2b70d729-13ec-4eac-9c71-6eed9463b516" />


**Question 8**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

```sql
SELECT 
    c.cust_name AS "cust_name",
    c.city AS "city",
    c.grade,
    s.name AS "Salesman",
    s.city AS "city"
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

<img width="1246" height="689" alt="image" src="https://github.com/user-attachments/assets/c0eee311-ec64-4d2f-bc18-43f2222b83d9" />


**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

APPOINTMENTS TABLE:

ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date

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

<img width="1238" height="359" alt="image" src="https://github.com/user-attachments/assets/c48b2e3c-a587-4e62-b2cc-ca7dfcd64147" />

**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.

NURSES TABLE:

ATTRIBUTES - nurse_id, first_name, last_name, department_id

DEPARTMENTS TABLE:

ATTRIBUTES - department_id, department_name
```sql
SELECT 
    n.*, 
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d
ON 
    n.department_id = d.department_id;
```

**Output:**

<img width="1241" height="368" alt="image" src="https://github.com/user-attachments/assets/d0cad1dc-1ca9-4f39-a18b-5522a34d8c12" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

<img width="657" height="413" alt="image" src="https://github.com/user-attachments/assets/b08f4df3-b017-4aa3-817d-15ef81d1a790" />

