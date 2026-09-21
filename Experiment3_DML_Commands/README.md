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
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
UPDATE suppliers set supplier_name=UPPER(supplier_name) 
where contact_person LIKE '%Singh%';
```

**Output:**

<img width="1235" height="435" alt="image" src="https://github.com/user-attachments/assets/bdfeaa29-46a7-477a-87b7-128a3cefacda" />

**Question 2**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```sql
UPDATE Employees set salary = salary+500,
email='updated'
where job_id='SA_REP' AND commission_pct>0.15;
```

**Output:**

<img width="1212" height="582" alt="image" src="https://github.com/user-attachments/assets/290ab9fd-f079-470e-8d8c-649bb973417e" />

**Question 3**
---
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT 
```sql
update Products set sell_price= sell_price*1.15
where quantity<50 and supplier_id=10;
```

**Output:**

<img width="1222" height="562" alt="image" src="https://github.com/user-attachments/assets/e76bb5db-0e48-40cf-9eb2-040c23379d1d" />

**Question 4**
---
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT     
```sql
update Products set category='Household' where product_name LIKE '%Detergent%';
```

**Output:**

<img width="1208" height="572" alt="image" src="https://github.com/user-attachments/assets/d5c3f727-fc39-4827-ad67-95ec1a983114" />

**Question 5**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
delete from Doctors where specialization='Pediatrics' and first_name='Michael';
```

**Output:**

<img width="1238" height="447" alt="image" src="https://github.com/user-attachments/assets/08c1c642-dc35-4378-9f79-f768cf762f5e" />

**Question 6**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
```sql
delete from Surgeries where surgery_id=3;
```

**Output:**

<img width="1222" height="447" alt="image" src="https://github.com/user-attachments/assets/60174ba2-b787-454b-80c3-d3fda02cac43" />

**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
delete from Doctors where last_name IS NULL;
```

**Output:**

<img width="1198" height="657" alt="image" src="https://github.com/user-attachments/assets/49703adb-11e6-4290-86c6-4272e7ee132e" />

**Question 8**
---
write a SQL query to identify customers who do not belong to the city of 'New York' or have a grade value that exceeds 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer where city<>'New York'and grade<=100;
```

**Output:**

<img width="1232" height="462" alt="image" src="https://github.com/user-attachments/assets/7d217c15-71f2-47c8-a434-be704ec9462f" />

**Question 9**
---
Write a SQL query to retrieve all orders where the purchase amount is between 500 and 4000 but exclude orders with purchase amounts of 948.50 and 1983.43. The query should return the columns: ord_no, purch_amt, ord_date, customer_id, and salesman_id.

Table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
```sql
select * from orders where purch_amt between 2000 and 4000;

```

**Output:**

<img width="1206" height="477" alt="image" src="https://github.com/user-attachments/assets/61218d6b-5405-4a33-b9ff-a14bccb8efd2" />

**Question 10**
---
Write a query to list all products that have a discounted price between $100 and $250. Return product_id, original_price, discount_percentage, and discounted_price from products table.


```sql
SELECT product_id,original_price,discount_percentage,
original_price*(1-discount_percentage) as discounted_price
from products
where original_price*(1-discount_percentage) between 100 and 250;```

**Output:**

<img width="1222" height="347" alt="image" src="https://github.com/user-attachments/assets/8e2e5d66-a094-4cd5-8781-1002d10a9767" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
