# Database Management System (DBMS)

### Introduction

- DBMS is a software using which we can store and retrieve and manage data efficiently
- Some of the examples of DBMS softwares are MySQL, PostgreSQL, MongoDB, etc.,
- Types of DBMS:
  
  - SQL (Relational)
  - NoSQL (Unstructured and Semi-structured)
 
### Database

- Data is nothing but information
- Each single data is a piece of information
- Collecting all these data and storing it in one place called as a **database**
- Software that we use to perform any operation with the database is called **DBMS**

### ACID Properties

- A - Atomicity
- C - Consistency
- I - Isolation
- D - Durability

#### Atomicity

- A transcation or any operation should be done either completely or should not be started at all
- Any process i.e., transcation or operation should not be done partially
- For example, let's consider a scenario of movie ticket booking for 4 persons
- It should be done in a way that either all four of the tickets should be booked and charged for that
- Or it should be done at all i.e., the process should not be initiated at all

#### Consistency

- In a database, when we are moving from one state to another state, it should be consistent
- Let's say Table A and Table B are in relationship
- Whatever changes or updates happens in Table A, it should also be reflected in Table B and vice versa
- In simple words, changes in one table should be consistently available in another table

#### Isolation

- Each and every transcation should be independently processed
- Let's say we are deleting and updating certain things in the database
- Both of these operations should happen independently in an orderly manner
- In simple terms, deletion happens first and then updation process will happen
- The processes should not happen simultaneously i.e., in a combined manner

#### Durability

- Changes happened in the database should be available permanently both to the user side as well as the admin side
- Let's say we have booked 10 tickets after that the completion of booking process,
- It should not show that the tickets have not been booked once refreshing the screen

### Normalization

#### Primary Key

- field that should be unique in a table which is kept as a PRIMARY KEY

#### Why PRIMARY KEY?

- Used for indexing
- Used for immediate accessing
- Used to uniquely identify a row in a table

#### FOREIGN KEY

- **FOREIGN KEY** is used to connect one row in Table A and another row in Table B
- For example, **CUSTOMER_ID** in customers table and **PRODUCT_ID** in products table is connected using **FOREIGN KEY**
- The main usecase of FOREIGN KEY is if an entity in parent table is being deleted, the child table also gets deleted via **Cascading Effect**

#### Cascading Effect

- Cascading effect is simply like the domino effect in the domino game
  
#### ONDELETE CASCADE

- One entity parent table is being deleted means the connected entities in child table is also deleted automatically via cascading effect
- This process is called as **ONDELETE CASCADE**

#### ONDELETE NULL

- **ONDELETE NULL** is a similar case in which the entity in parent table when gets deleted, the connected entities in child table becomes NULL
- Both **ONDELETE CASCADE** and **ONDELETE NULL** becomes useful when we are using both **PRIMARY KEY** and **FOREIGN KEY** together

#### CANDIDATE KEY

- A **Candidate Key** is a minimal set of attributes that uniquely identifies a row in a table
- There can be multiple candidate keys in a table, but only one is chosen as the **Primary Key**
- **Key Points**:
  
  - Must be unique
  - Cannot have redundant attributes (minimal)
  - A table can have more than one Candidate Key
  - It can consist of a single attribute or multiple attributes

- **Example**:
  
  Table: `Students`

  | StudentID | Email            | Name        | Phone     |  
  |-----------|------------------|-------------|-----------|  
  | 101       | john@gmail.com   | John        | 987654321 |  
  | 102       | mary@gmail.com   | Mary        | 876543210 |  

- In this table, `StudentID` and `Email` are **Candidate Keys** because both uniquely identify each student
- However, only one can be selected as the **Primary Key**

#### COMPOSITE KEY

- A **Composite Key** is a Candidate Key that consists of two or more attributes (columns) that together uniquely identify a row in a table
- No single attribute in the composite key can uniquely identify the row by itself
- **Key Points**:
  
  - A type of Candidate Key
  - Requires a combination of multiple attributes to ensure uniqueness
  - Often used in **junction tables** (many-to-many relationships)

- **Example**:
  
  Table: `StudentCourses` (junction table between `Students` and `Courses`)

  | StudentID | CourseID | EnrollmentDate |  
  |-----------|----------|----------------|  
  | 101       | CSE101   | 2025-01-10     |  
  | 101       | CSE102   | 2025-01-12     |  
  | 102       | CSE101   | 2025-01-11     |  

- In this table, Neither `StudentID` nor `CourseID` alone can uniquely identify a row.
- **`(StudentID, CourseID)` together form a Composite Key**, as their combination uniquely identifies each record.

### Types of Normalization

- 1NF
- 2NF
- 3NF
- 3.5NF (BCNF)
- 4NF
- 5NF (PJNF)
- 6NF (DKNF)

#### 1NF

- In this form, every value should be a single element in a single entire column or in a single entire row
- Values should not be comma seperated values like list or tuples

#### 2NF

- In this form, a non-key attribute should not depend on another non key attribute
- A non-key attribute should always depend on a key attribute

![2NF](/Diagram/2NF.png)

#### 3NF

- The main aim in this form is to remove transitive dependency
- One duplicating element should not identify another duplicating element

![3NF-1](/Diagram/3NF-1.png)

![3NF-2](/Diagram/3NF-2.png)

### Denormalization

- Denormalization is simply the opposite of Normalization
- This process is done often in NoSQL for optimization
- In normalization, we spilt the single table into multiple tables to avoid combining of duplicating elements
- Whereas in denormalization, we combine multiple tables into a single table
- Example for denormalization is creating a playlist in a music app which has multiple tables connected to a single playlist table

### RDBMS

- Has only structured database
- Can query using SQL language

### NoSQL

- Has unstructured or semi-structured database
- We can also enforce schema in a NoSQL database but generally we don't do it
- Used in very large distributed systems where it has too unstructed, unrelated, missing data 

### Transcation

- A transcation should be done either completely or should not be started at all
- Any process i.e., transcation or operation should not be done partially
- For example, let's consider a scenario of movie ticket booking for 4 persons
- It should be done in a way that either all four of the tickets should be booked and charged for that
- Or it should be done at all i.e., the process should not be initiated at all

### Concurrency Control

- Executing a single transcation at a time will increase the waiting time of other transcations which will result in delay of the overall execution
- Hence for increasing the overall throughput and efficiency of the system, several transcations and locking mechanisms are executed
- For example, During the booking time, the tickets of a particular row are locked so that no others cannot book that same row tickets
- This called as **Row-level Locking**. Once after booking, if the booking is failed, that same row is accessible for booking
- If booking is succeeded, cancelling or refunding and other transcations are done seperately
- **Page-level Locking** is the same as **Row-level Locking**
- But the difference here is we lock a set of rows in a table or rows in a set of tables
- Lokcing is of two types:
  
  - Optimistic Locking
  - Pessimistic Locking

#### Pessimistic Locking

- Pessimistic locking is the locking that is enabled whenever we try to access data
- Once after completing any transcation with data, the lock is released to avoid errors

#### Optimistic Locking

- Optimistic locking is the kind of locking which checks for errors at the end of any transcation
- If errros are present, it rollbacks to the previous state. If no errors present, it commits that state
- But this kind of locking creates frequent update in data ultimately resulting inconsistency of data
- The important keywords here are **BEGIN, COMMIT, ROLLBACK**

### Deadlock

- Once when two or more transcation block each other by holding resources the other needs
- Use a timeout or a wait-for-graph to prevent deadlock

### Indexing

- If we want to take a single piece of data in a collection of data
- Using indexing, we can take that particular data within seconds but that indexing process takes time
- We don't need to traverse the entire collection of data to get that particular data
- The usecase of indexing comes in handy when a user requests for a particular data
- And we can give it in seconds by already indexing the data elements
- There are two types of indexing:
  
  - Clustered Indexing
  - Non-Clustered Indexing

#### Clustered Indexing

- Clustered Indexing is simply the arranging of rows in a table in random manner
- Clustered Indexing is prefered whenever we want to get the data fastly rather than sorting and other related processes 
  
#### Non-Clustered Indexing

- Non-clustered indexing involves a seperate structure which points to the actual data
- It is simply like a Hashmap or Hashtable which is a seperate structure pointing to the actual data
- Whenever sorting is done, **Non-Clustered Indexing** is mostly prefered
- Implementation of indexing is of two types:

  - **B-Tree Indexing**
  
    - Balanced Binary Trees are used to order the keys so as to access them in O(Log N) time complexity
      
  - **Hashing Indexing**
    
    - Whenever Primary Key is given, it does some mathematical calculations which returns the memory address
    - Using that memory address, we can get the values inside that memory address
  
### Stored Procedure

- Stored Procedure is using of the pre-compiled SQL for carrying out repeated operations
- It is similar to functions in various other programming languages

### TRIGGER

- **TRIGGER** is used when we want to trigger one operation while performing another operation
- For example, whenever we are ordering food means the notification table should be called automatically

### VIEW 

- **VIEW** is a kind of virtual table and it is used for performing complex queries 
- Whenever we are performing SQL queries and we want to access the result often means we can store it in a **VIEW**

### Peformance Tuning

- Performance tuning can be done by
  
  - Query Optimization
  - Database Sharding
  - CAP Theorem 
  - Indexing
  - Caching
  
