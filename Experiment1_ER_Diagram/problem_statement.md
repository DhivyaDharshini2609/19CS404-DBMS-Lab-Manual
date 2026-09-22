# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="617" height="813" alt="image" src="https://github.com/user-attachments/assets/f9318c6b-8898-4b43-9063-2478dc7c0e60" />


### Entities and Attributes

| **Entity**     | **Attributes (PK, FK)**                                          | **Notes**                                |
| -------------- | ---------------------------------------------------------------- | ---------------------------------------- |
| **Member**     | **MemberID (PK)**, Name, Membership_Type, Start_Date             | Stores member details                    |
| **Trainer**    | **TrainerID (PK)**, Name, Expertise, Specialization              | Stores trainer details                   |
| **Program**    | **ProgramID (PK)**, Name, Date, Time                             | Stores fitness program details           |
| **Session**    | **SessionID (PK)**, Session_Date, Start_Time, End_Time, Duration | Stores personal training session details |
| **Payment**    | **PaymentID (PK)**, Date, Amount, MemberID (FK), SessionID (FK)  | Stores payment details                   |
| **Attendance** | **AttendanceID (PK)**, Date, Time, SessionID (FK)                | Stores attendance for sessions           |


### Relationships and Constraints

| **Relationship**                     | **Cardinality** | **Participation**                 | **Notes**                                                               |
| ------------------------------------ | --------------- | --------------------------------- | ----------------------------------------------------------------------- |
| **Member – Makes – Payment**         | 1 : N           | Member → Partial, Payment → Total | One member can make many payments                                       |
| **Member – Joins – Program**         | M : N           | Partial                           | A member can join many programs and a program can have many members     |
| **Trainer – Assigned To – Program**  | M : N           | Partial                           | A trainer can handle many programs and a program can have many trainers |
| **Member – Books – Session**         | 1 : N           | Partial                           | A member can book multiple training sessions                            |
| **Trainer – Conducts – Session**     | 1 : N           | Session → Total                   | One trainer can conduct many sessions                                   |
| **Session – Has – Attendance**       | 1 : 1           | Total                             | Each session has an attendance record                                   |
| **Session – Relationship – Payment** | 1 : N           | Partial                           | Payments can be associated with training sessions                       |

### Assumptions
Each member has a unique MemberID.

Each trainer has a unique TrainerID.

Each program has a unique ProgramID.

Each session has a unique SessionID.

A member can join multiple fitness programs.

A program can have multiple trainers.

A member can book multiple personal training sessions.

A trainer can conduct multiple sessions.

Each session has an attendance record.

Payments are recorded with a PaymentID, date and amount.

A member must be registered before joining a program or booking a session.

The payment amount must be a positive value.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="570" height="803" alt="image" src="https://github.com/user-attachments/assets/62cce52c-5b96-44d5-a104-1cc1f0dfdbba" />


### Entities and Attributes

| **Entity**  | **Attributes (PK, FK)**                                                          | **Notes**                     |
| ----------- | -------------------------------------------------------------------------------- | ----------------------------- |
| **Book**    | **Book_ID (PK)**, Title, Author, Category                                        | Stores details of books       |
| **Member**  | **Member_ID (PK)**, Name, Phone                                                  | Stores library member details |
| **Loan**    | **Loan_ID (PK)**, Loan_Date, Return_Date, Due_Date, Member_ID (FK), Book_ID (FK) | Stores book borrowing details |
| **Event**   | **Event_ID (PK)**, Name, Date, Time                                              | Stores library event details  |
| **Room**    | **Room_ID (PK)**, Room_Name, Capacity, Room_Type                                 | Stores room details           |
| **Speaker** | **Speaker_ID (PK)**, Name, Phone_No                                              | Stores speaker/author details |
| **Fine**    | **Fine_ID (PK)**, Amount, Date, Payment_Status, Loan_ID (FK)                     | Stores overdue fine details   |

### Relationships and Constraints

| **Relationship**                   | **Cardinality** | **Participation**              | **Notes**                                   |
| ---------------------------------- | --------------- | ------------------------------ | ------------------------------------------- |
| **Member – Borrows – Loan**        | 1 : N           | Loan → Total, Member → Partial | One member can have many loans              |
| **Book – Borrow – Loan**           | 1 : N           | Loan → Total, Book → Partial   | A book can be borrowed many times over time |
| **Member – Registers For – Event** | M : N           | Partial                        | A member can register for many events       |
| **Room – Booked – Event**          | 1 : N           | Event → Total, Room → Partial  | A room can be booked for different events   |
| **Event – Has – Speaker**          | 1 : N           | Speaker → Total                | An event can have one or more speakers      |
| **Loan – Generates – Fine**        | 1 : 0..1        | Fine → Total, Loan → Partial   | A late loan may generate a fine             |


### Assumptions

Each Book, Member, Loan, Event, Room, Speaker and Fine has a unique ID.

A member can borrow multiple books.

A book can be borrowed multiple times over its lifetime.

A member can register for multiple events.

An event can have one or more speakers/authors.

A room can be booked for different events at different times.

A fine is generated only when a book is returned after its due date.

The fine amount must be a positive value.

A member must be registered before borrowing a book or registering for an event.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="567" height="773" alt="image" src="https://github.com/user-attachments/assets/f57a4dd3-4873-4c42-b673-a01f97be2606" />

### Entities and Attributes
| **Entity**      | **Attributes (PK, FK)**                       | **Notes**                       |
| --------------- | --------------------------------------------- | ------------------------------- |
| **Customer**    | **Customer_ID (PK)**, Name, Email             | Stores customer details         |
| **Waiter**      | **Waiter_ID (PK)**, Name, Shift               | Stores waiter details           |
| **Reservation** | **Reservation_ID (PK)**, No_of_People, Date   | Stores reservation details      |
| **Table**       | **Table_ID (PK)**, Capacity, Table_No, Status | Stores restaurant table details |
| **Order**       | **Order_ID (PK)**, Date, Time, Amount         | Stores food order details       |
| **Dishes**      | **Dish_ID (PK)**, Name, Price                 | Stores dish details             |
| **Category**    | **Category_ID (PK)**, Category_Name           | Stores dish categories          |
| **Bill**        | **Bill_ID (PK)**, Date, Amount                | Stores bill details             |


### Relationships and Constraints
| **Relationship**                      | **Cardinality** | **Participation**                       | **Notes**                               |
| ------------------------------------- | --------------- | --------------------------------------- | --------------------------------------- |
| **Customer – Makes – Reservation**    | 1 : N           | Reservation → Total, Customer → Partial | One customer can make many reservations |
| **Waiter – Serves – Reservation**     | 1 : N           | Reservation → Total                     | A waiter can serve many reservations    |
| **Reservation – Assigned to – Table** | N : 1           | Reservation → Total                     | Each reservation is assigned to a table |
| **Reservation – Has – Order**         | 1 : N           | Order → Total                           | A reservation can have multiple orders  |
| **Order – Contains – Dishes**         | M : N           | Partial                                 | An order can contain multiple dishes    |
| **Category – Includes – Dishes**      | 1 : N           | Dishes → Total                          | A category can contain many dishes      |
| **Reservation – Generates – Bill**    | 1 : 1           | Bill → Total                            | A reservation generates a bill          |

### Assumptions

Each customer has a unique Customer_ID.

Each reservation has a unique Reservation_ID.

A customer can make multiple reservations.

Each reservation is assigned to one table and one waiter.

A reservation can have multiple food orders.

An order can contain multiple dishes.

Each dish belongs to one category.

A bill is generated for each reservation.

The bill amount includes the charges for the food and service.

A table cannot be assigned to two reservations at the same date and time.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
