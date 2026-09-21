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
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column.


```sql
select p.first_name as patient_name,a.* from patients p inner join appointments a on p.patient_id=a.appointment_id;
```

**Output:**

<img width="1272" height="627" alt="image" src="https://github.com/user-attachments/assets/db44b366-ae6d-4b73-8807-ba84ddc7ad7c" />

**Question 2**
---
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.

```sql
select n.nurse_id,d.department_name from nurses n inner join departments d on n.department_id=d.department_id
where n.first_name='David';
```

**Output:**

<img width="962" height="470" alt="image" src="https://github.com/user-attachments/assets/b23d6b10-2cf9-432d-8fd8-a44c0915a31d" />

**Question 3**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
```sql
select o.ord_no,o.purch_amt,c.cust_name,c.city from orders o inner join customer c on o.customer_id=c.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="1267" height="562" alt="image" src="https://github.com/user-attachments/assets/8e823db7-ee29-4584-87b2-2ddfdf893faa" />

**Question 4**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```sql
select c.cust_name,c.city,c.grade,s.name as Salesman,s.city from customer c inner join salesman s
on c.salesman_id=s.salesman_id order by c.customer_id asc;
```

**Output:**

<img width="1262" height="577" alt="image" src="https://github.com/user-attachments/assets/ee160c0c-af75-48f9-a35f-a2862748a9cc" />

**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
select p.first_name as patient_name,t.* from patients p inner join test_results t 
on p.patient_id=t.patient_id where p.admission_date between '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="1267" height="477" alt="image" src="https://github.com/user-attachments/assets/d162b6de-39a1-4eef-8706-56e0dd693e85" />

**Question 6**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.


```sql
select c.cust_name,o.ord_no,o.ord_date,o.purch_amt from customer c left join orders o
on c.customer_id=o.customer_id;
```

**Output:**

<img width="1255" height="781" alt="image" src="https://github.com/user-attachments/assets/e6cb19e3-0300-450a-b6b4-3d83d8d5bedb" />

**Question 7**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```sql
select c.cust_name,c.city,c.grade,s.name as Salesman,s.city from customer c inner join salesman s
on c.salesman_id=s.salesman_id where c.grade<300
order by customer_id asc;
```

**Output:**

<img width="1258" height="773" alt="image" src="https://github.com/user-attachments/assets/693af492-fddb-4dfb-9a80-25fdec8f3fb1" />

**Question 8**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
```sql
SELECT
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS 'Order Amount'
FROM customer c
left JOIN orders o
    ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**

<img width="1258" height="787" alt="image" src="https://github.com/user-attachments/assets/4e9448ed-278f-4aaf-a9c2-96b746b519a8" />

**Question 9**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1257" height="591" alt="image" src="https://github.com/user-attachments/assets/d9f74b6b-33df-40d7-a816-ca611312b101" />

**Question 10**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)
```sql
SELECT
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
WHERE o.purch_amt > 1000;
```

**Output:**

<img width="1257" height="787" alt="image" src="https://github.com/user-attachments/assets/442d7d30-b84b-45a1-86e1-6c28c47c2c61" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
