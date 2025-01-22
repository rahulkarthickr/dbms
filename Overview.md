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

#### CANDITATE KEY

- Combination of two or more fields as a KEY
- If two or more rows and columns that can be uniquely identified means that is called **CANDITATE KEY**
- For example, let's say we are creating new mail-ids using an existing single mail-id
- And the condition is kept as phone number should be unique, then we can club email-id and phone number to uniquely identify users
- That is called as **CANDITATE KEY**

### Types of Normalization

- 1NF
- 2NF
- 3NF
- 3.5NF (BCNF)
- 4NF
- 5NF (PJNF)
- 6NF (DKNF)

#### 1NF (First Normalization Form)

- In this form, every value should be a single element in a single entire column or in a single entire row
- Values should not be comma seperated values like list or tuples

#### 2NF (Second Normalization Form)

- In this form, a non-key attribute should not depend on another non key attribute
- A non-key attribute should always depend on a key attribute

![2NF](/Diagram/2NF.png)
