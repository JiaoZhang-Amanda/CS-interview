* [Basic](#firebasic)
* [Normalization](#fireNormalization)
* [E-R model](#fireER-model)
* [Others](#fireothers)
* [Database Troubleshooting](#firedatabase-troubleshooting)

## :fire:Basic
### Define DBMS.
* DBMS stands for Database Management system. It is a collection of application programs which allow the user to organize, restore and retrieve information about data efficiently and as effectively as possible.
* Some of the popular DBMS's are MySql, Oracle, Sybase, etc.
* Advantages of DBMS
    * Data is stored in a structured way and hence redundancy is controlled.
    * Validates the data entered and provide restrictions on unauthorized access to the database.
    * Provides backup and recovery of the data when required.
    * Provides multiple user interfaces.
* There are two types of DBMS:
    * Relational Database Management System: The data is stored in relations (tables). Example – MySQL.
    * Non-Relational Database Management System: There is no concept of relations, tuples and attributes.  Example – Mongo
    
### Define RDBMS.
Relational Database Management System(RDBMS) is based on a relational model of data that is stored in databases in separate tables and they are related to the use of a common column. Data can be accessed easily from the relational database using Structured Query Language (SQL).

## :fire:Normalization
### Explain Normalization and De-Normalization.
* **Normalization** is the process of removing redundant data from the database by splitting the table in a well-defined manner in order to maintain data integrity. This process saves much of the storage space.
* **De-normalization** is the process of adding up redundant data on the table in order to speed up the complex queries and thus achieve better performance.

### Explain the Primary Key, Foreign key and Composite Key.
* **The primary key** is that column of the table whose every row data is uniquely identified. Every row in the table must have a primary key and no two rows can have the same primary key. Primary key value can never be null nor can it be modified or updated.
* **Foreign key** maintains referential integrity by enforcing a link between the data in two tables. The foreign key in the child table references the primary key in the parent table. The foreign key constraint prevents actions that would destroy links between the child and parent tables.
* **Composite Key** is a form of the candidate key where a set of columns will uniquely identify every row in the table.

### What do you understand by the Unique key?
A Unique key is the same as the primary key whose every row data is uniquely identified with a difference of null value i.e. Unique key allows one value as a NULL value.

### What are the different types of Normalization?
* **First Normal Form (1NF)**: A relation is said to be in 1NF only when all the entities of the table contain unique or atomic values.
* **Second Normal Form (2NF)**: A relation is said to be in 2NF only if it is in 1NF and all the non-key attribute of the table is fully dependent on the primary key.
* **Third Normal Form (3NF)**: A relation is said to be in 3NF only if it is in 2NF and every non-key attribute of the table is not transitively dependent on the primary key.

### What is BCNF?
BCNF is the Boyce Code Normal form. It is the higher version of 3NF which does not have any multiple overlapping candidate keys.

## :fire:E-R model
### What do you understand by the E-R model?
* E-R model is an Entity-Relationship model which defines the conceptual view of the database.
* The E-R model basically shows the real-world entities and their association/relations. Entities here represent the set of attributes in the database.<br>
![](https://camo.githubusercontent.com/30b13bf542f6115d8bcecc903ed08a0f16d21304/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f31643238616430352d333965352d343961322d613661312d6136663439366164626136612e706e67)
![](https://camo.githubusercontent.com/144cd455691b6d05e58c063d5272b6e1681689d4/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f31343338396561342d386439362d346539362d396637362d3536346361333332346331652e706e67)
### What are the various types of relationships in Database? Define them.
There are 3 types of relationships in Database:
* **One-to-one**: One table has the relationship with another table having the similar kind of column. Each primary key relates to only one or no record in the related table.
* **One-to-many**: One table has a relationship with another table that has a primary and foreign key relations. The primary key table contains only one record that relates to none, one or many records in the related table.
* **Many-to-many**: Each record in both the tables can relate to many numbers of record in another table.

## :fire:Others
### Explain the terms ‘Record’, ‘Field’ and ‘Table’ in terms of database.
* **Record**: Record is a collection of values or fields of a specific entity. Example: An employee, Salary account, etc.
* **Field**: A field refers to an area within a record that is reserved for a specific piece of data. Example: Employee ID.
* **Table**: Table is the collection of records of specific types. Example: Employee table is a collection of record related to all the employees.

### What do you understand by Data Independence? What are its two types?
* **Data Independence** refers to the ability to modify the schema definition in one level in such a way that it does not affect the schema definition in the next higher level. The 2 types of Data Independence are:
    * **Physical Data Independence**: It modifies the schema at the physical level without affecting the schema at the conceptual level.
    * **Logical Data Independence**: It modifies the schema at the conceptual level without affecting or causing changes in the schema at the view level.

### What do you understand by Functional dependency?
A relation is said to be in Functional dependency when one attribute uniquely defines another attribute.
* For Example, R is a Relation, X and Y are two attributes. T1 and T2 are two tuples. Then, T1[X]=T2[X] and T1[Y]=T2[Y] means the value of component X uniquely define the value of component Y. Also, X->Y means Y is functionally dependent on X.

### When is functional dependency said to be the fully functional dependency?
* To fulfill the criteria of fully functional dependency, the relation must meet the requirement of functional dependency.
* A functional dependency ‘A’ and ‘B’ are said to be fully functional dependent when removal of any attribute say ‘X’ from ‘A’ means the dependency does not hold anymore.

### Define Entity, Entity type, and Entity set.
* **Entity** can be anything, be it a place, class or object which has an independent existence in the real world.
* **The entity type**represents a set of entities that have similar attributes.
* **Entity set** in the database represents a collection of entities having a particular entity type.

### Define a Weak Entity set.
Weak entity set is the one whose primary key comprises of its partial key as well as the primary key of its parent entity. This is the case because the entity set may not have sufficient attributes to form a primary key.

### Explain the terms ‘Attribute’ and ‘Relations’
* **Attribute** describes the properties or characteristics of an entity. For Example, Employee ID, Employee Name, Age, etc., can be attributes of the entity Employee.
* The **relation** is a two-dimensional table containing a number of rows and columns where every row represents a record of the relation. Here, rows are also known as ‘Tuples’ and columns are known as ‘Attributes’.

### Define Cursor and its types.
Cursor is a temporary work area that stores the data, as well as the result set, occurred after manipulation of data retrieved. A cursor can hold only one row at a time. The 2 types of Cursor are:
* **Implicit cursors** are declared automatically when DML statements like INSERT, UPDATE, DELETE is executed.
* **Explicit cursors** have to be declared when SELECT statements that are returning more than one row are executed.

## :fire:Database Troubleshooting
### Can’t login?
This problem occurs if the user tries to log in with credentials that cannot be validated. This problem can occur in the following scenarios:
* Scenario 1: The login may be a SQL Server login but the server only accepts Windows Authentication
<br> To resolve this issue, configure SQL Server in Mixed Authentication Mode.
* Scenario 2: You are trying to connect by using SQL Server Authentication but the login used does not exist on SQL Server
<br> To resolve this issue, verify that the SQL Server login exists
* Scenario 3: The login may use Windows Authentication but the login is an unrecognized Windows principal
<br> An unrecognized Windows principal means that Windows can't verify the login. This might be because the Windows login is from an untrusted domain. To resolve this issue, verify that you are logged in to the correct domain.

### Can’t connect to the database
* Incorrect Login Credentials
For instance, it can be because of the wrong login username and password being used to access the admin panel.
* Corrupt Databasehe 
WordPress database can be corrupted by a number of things like installing a faulty or incompatible plugin. Another likely reason might be that the server that hosts your database may temporarily be down.
* To **Fix**
1) Repair the Database
2) Change Login Credentials: take a look at the database login settings in the wp-config file. Your database login credentials may have stopped working because you might have changed your hosting company or some useful information about your database which wasn’t manually updated in the wp-config file.
3) Fix Corrupted Files
