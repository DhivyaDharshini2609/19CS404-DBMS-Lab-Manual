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
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE
```sql
select InsuranceCompany,avg(EndDate-StartDate) as AvgCoverageDurationDays
from Insurance group by InsuranceCompany;
```

**Output:**

<img width="1012" height="598" alt="image" src="https://github.com/user-attachments/assets/8d884053-acad-4c84-bac8-37c7b593aa89" />

**Question 2**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select count(id) as employees_count from employee 
where income>50000;
```

**Output:**

<img width="1242" height="375" alt="image" src="https://github.com/user-attachments/assets/650a19c1-81ac-4520-ac45-58b103126661" />

**Question 3**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 
```sql
select name as Employee_Name,min(age) as Age from employee;
```

**Output:**

<img width="1167" height="382" alt="image" src="https://github.com/user-attachments/assets/9e5437e3-48f4-409a-919e-3fe4a3754625" />

**Question 4**
---
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.


```sql
select category_id,COUNT(*) as COUNT from products 
GROUP BY category_id having category_id>2;
```

**Output:**

<img width="1087" height="330" alt="image" src="https://github.com/user-attachments/assets/a69f95ab-3189-4983-ab03-73aae6f75811" />

**Question 5**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.


```sql
select address,SUM(salary) from customer1 
group by address having sum(salary)>2000;
```

**Output:**

<img width="1220" height="542" alt="image" src="https://github.com/user-attachments/assets/ef7d6474-21db-4404-be73-f177abecc227" />

**Question 6**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.


```sql
select category_id,AVG(Price) from products 
group by category_id having avg(price) between 10 and 15;
```

**Output:**

<img width="931" height="402" alt="image" src="https://github.com/user-attachments/assets/12f720cc-241f-4c56-a083-eccec370017a" />

**Question 7**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?


```sql
select Frequency,Count(*) as TotalPrescriptions from prescriptions 
group by frequency;
```

**Output:**

<img width="1062" height="551" alt="image" src="https://github.com/user-attachments/assets/bb02cfed-8e6f-4bcd-8117-8e290fd378f9" />

**Question 8**
---
How many prescriptions were written by each doctor?

```sql
select DoctorID,COUNT(*) as TotalPrescriptions from Prescriptions
group by DoctorID;
```

**Output:**

<img width="987" height="797" alt="image" src="https://github.com/user-attachments/assets/51896836-1a67-4f5e-aa87-771e3d589585" />

**Question 9**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001


```sql
SELECT max(purch_amt) as MAXIMUM from orders;
```

**Output:**

<img width="961" height="390" alt="image" src="https://github.com/user-attachments/assets/f948ee9a-a3c9-4808-a13f-35fe9928b7ec" />

**Question 10**
---
Write a SQL query to calculate the total number of working hours of all employees


```sql
select sum(workhour) as 'Total working hours' from employee1;
```

**Output:**
<img width="823" height="387" alt="image" src="https://github.com/user-attachments/assets/e218e1bf-20b5-4b38-832f-fe33dfd5a220" />

![Output10](output.png)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
