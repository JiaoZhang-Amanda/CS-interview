## Database Interview Question

#### Define DBMS.
* DBMS stands for Database Management system. It is a collection of application programs which allow the user to organize, restore and retrieve information about data efficiently and as effectively as possible.
* Some of the popular DBMS's are MySql, Oracle, Sybase, etc.
* Advantages of DBMS
    * Data is stored in a structured way and hence redundancy is controlled.
    * Validates the data entered and provide restrictions on unauthorized access to the database.
    * Provides backup and recovery of the data when required.
    * Provides multiple user interfaces.
#### Define RDBMS.
* Relational Database Management System(RDBMS) is based on a relational model of data that is stored in databases in separate tables and they are related to the use of a common column. Data can be accessed easily from the relational database using Structured Query Language (SQL).
#### What are the various types of relationships in Database? Define them.
There are 3 types of relationships in Database:
* **One-to-one**: One table has the relationship with another table having the similar kind of column. Each primary key relates to only one or no record in the related table.
* **One-to-many**: One table has a relationship with another table that has a primary and foreign key relations. The primary key table contains only one record that relates to none, one or many records in the related table.
* **Many-to-many**: Each record in both the tables can relate to many numbers of record in another table.
#### Explain Normalization and De-Normalization.
* **Normalization** is the process of removing redundant data from the database by splitting the table in a well-defined manner in order to maintain data integrity. This process saves much of the storage space.
* **De-normalization** is the process of adding up redundant data on the table in order to speed up the complex queries and thus achieve better performance.
#### What are the different types of Normalization?
* **First Normal Form (1NF)**: A relation is said to be in 1NF only when all the entities of the table contain unique or atomic values.
* **Second Normal Form (2NF)**: A relation is said to be in 2NF only if it is in 1NF and all the non-key attribute of the table is fully dependent on the primary key.
* **Third Normal Form (3NF)**: A relation is said to be in 3NF only if it is in 2NF and every non-key attribute of the table is not transitively dependent on the primary key.
#### What is BCNF?
BCNF is the Boyce Code Normal form. It is the higher version of 3NF which does not have any multiple overlapping candidate keys.
#### What is SQL?
* **Structured Query language**, SQL is an ANSI(American National Standard Institute) standard programming language that is designed specifically for storing and managing the data in the relational database management system (RDBMS) using all kinds of data operations.
#### How many SQL statements are used? Define them.
SQL statements are basically divided into three categories, DDL, DML, and DCL.
* **Data Definition Language (DDL)** commands are used to define the structure that holds the data. These commands are auto-committed i.e. changes done by the DDL commands on the database are saved permanently.
* **Data Manipulation Language (DML)** commands are used to manipulate the data of the database. These commands are not auto-committed and can be rolled back.
* **Data Control Language (DCL)** commands are used to control the visibility of the data in the database like revoke access permission for using data in the database.
#### Enlist some commands of DDL, DML, and DCL.
- Data Definition Language (DDL) commands:
    * **CREATE** to create a new table or database.
    * **ALTER** for alteration.
    * **Truncate**to delete data from the table.
    * **DROP** to drop a table.
    * **RENAME** to rename a table.
- Data Manipulation Language (DML) commands:
    * **INSERT** to insert a new row.
    * **UPDATE** to update an existing row.
    * **DELETE** to delete a row.
    * **MERGE** for merging two rows or two tables.
- Data Control Language (DCL) commands:
    * **COMMIT** to permanently save.
    * **ROLLBACK** to undo the change.
    * **SAVEPOINT** to save temporarily.
#### Define DML Compiler.
DML compiler translates DML statements in a query language into a low-level instruction and the generated instruction can be understood by Query Evaluation Engine.
#### What is DDL interpreter?
DDL Interpreter interprets the DDL statements and records the generated statements in the table containing metadata.
#### Enlist the advantages of SQL.
* Simple SQL queries can be used to retrieve a large amount of data from the database very quickly and efficiently.
* SQL is easy to learn and almost every DBMS supports SQL.
* It is easier to manage the database using SQL as no large amount of coding is required.
#### Explain the terms ‘Record’, ‘Field’ and ‘Table’ in terms of database.
* **Record**: Record is a collection of values or fields of a specific entity. Example: An employee, Salary account, etc.
* **Field**: A field refers to an area within a record that is reserved for a specific piece of data. Example: Employee ID.
* **Table**: Table is the collection of records of specific types. Example: Employee table is a collection of record related to all the employees.
#### What do you understand by Data Independence? What are its two types?
**Data Independence** refers to the ability to modify the schema definition in one level in such a way that it does not affect the schema definition in the next higher level. The 2 types of Data Independence are:
* Physical Data Independence: It modifies the schema at the physical level without affecting the schema at the conceptual level.
* Logical Data Independence: It modifies the schema at the conceptual level without affecting or causing changes in the schema at the view level.
#### Define the relationship between ‘View’ and ‘Data Independence’.
* View is a virtual table that does not have its data on its own rather the data is defined from one or more underlying base tables.
* Views account for logical data independence as the growth and restructuring of base tables is not reflected in views.
#### What are the advantages and disadvantages of views in the database?
- Advantages of Views:
    * As there is no physical location where the data in views is stored, it generates output without wasting resources.
    * Data access is restricted as it does not allow commands like insertion, updation, and deletion.
- Disadvantages of Views:
    * The view becomes irrelevant if we drop a table related to that view.
    * More memory is occupied when the view is created for large tables.
#### What do you understand by Functional dependency?
A relation is said to be in Functional dependency when one attribute uniquely defines another attribute.
* For Example, R is a Relation, X and Y are two attributes. T1 and T2 are two tuples. Then, T1[X]=T2[X] and T1[Y]=T2[Y] means the value of component X uniquely define the value of component Y. Also, X->Y means Y is functionally dependent on X.

#### When is functional dependency said to be the fully functional dependency?
* To fulfill the criteria of fully functional dependency, the relation must meet the requirement of functional dependency.
* A functional dependency ‘A’ and ‘B’ are said to be fully functional dependent when removal of any attribute say ‘X’ from ‘A’ means the dependency does not hold anymore.

#### What do you understand by the E-R model?
* E-R model is an Entity-Relationship model which defines the conceptual view of the database.
* The E-R model basically shows the real-world entities and their association/relations. Entities here represent the set of attributes in the database.

#### Define Entity, Entity type, and Entity set.
* **Entity** can be anything, be it a place, class or object which has an independent existence in the real world.
* **The entity type**represents a set of entities that have similar attributes.
* **Entity set** in the database represents a collection of entities having a particular entity type.

#### Define a Weak Entity set.
Weak entity set is the one whose primary key comprises of its partial key as well as the primary key of its parent entity. This is the case because the entity set may not have sufficient attributes to form a primary key.

#### Explain the terms ‘Attribute’ and ‘Relations’
* **Attribute** describes the properties or characteristics of an entity. For Example, Employee ID, Employee Name, Age, etc., can be attributes of the entity Employee.
* The **relation** is a two-dimensional table containing a number of rows and columns where every row represents a record of the relation. Here, rows are also known as ‘Tuples’ and columns are known as ‘Attributes’.

#### Define Cursor and its types.
Cursor is a temporary work area that stores the data, as well as the result set, occurred after manipulation of data retrieved. A cursor can hold only one row at a time. The 2 types of Cursor are:
* **Implicit cursors** are declared automatically when DML statements like INSERT, UPDATE, DELETE is executed.
* **Explicit cursors** have to be declared when SELECT statements that are returning more than one row are executed.

#### What is the Database transaction?
Sequence of operation performed which changes the consistent state of the database to another is known as the database transaction. After the completion of the transaction, either the successful completion is reflected in the system or the transaction fails and no change is reflected.
* Transactions are completed by COMMIT or ROLLBACK SQL statements, which indicate a transaction’s beginning or end.
#### What is ACID?
The ACID acronym defines the properties of a database transaction, as follows:
* **Atomicity**: A transaction must be fully complete, saved (committed) or completely undone (rolled back). 
* **Consistency**: The transaction must be fully compliant with the state of the database as it was prior to the transaction. In other words, the transaction cannot break the database’s constraints.
* **Isolation**: Transaction data must not be available to other transactions until the original transaction is committed or rolled back.
* **Durability**: Transaction data changes must be available, even in the event of database failure.
#### What do you understand by Join?
Join is the process of explaining the relationship between different tables by combining columns from one or more table having common values in each. When a table joins with itself, it is known as Self Join.

#### What do you understand by Index hunting?
Index hunting is the process of boosting the collection of indexes which helps in improving the query performance as well as the speed of the database.
#### How to improve query performance using Index hunting?
Index hunting help in improving query performance by:
* Using a query optimizer to coordinate queries with the workload.
* Observing the performance and effect of index and query distribution.
#### Differentiate between ‘Cluster’ and ‘Non-cluster’ index.
* **Clustered** Index alters the table and reorders the way in which the records are stored in the table. Data retrieval is made faster by using the clustered index.
* A **Non-clustered** index does alter the records that are stored in the table but creates a completely different object within the table.
#### Define Join types.
1) **Inner JOIN**: Inner JOIN is also known as a simple JOIN. This SQL query returns results from both the tables having a common value in rows.
2) **Natural JOIN**: This is a type of Inner JOIN that returns results from both the tables having the same data values in the columns of both the tables to be joined.
3) **Cross JOIN**: Cross JOIN return results as all the records where each row from the first table is combined with each row of the second table.
1) **Right JOIN**: Right JOIN is also known as Right Outer JOIN. This returns all the rows as a result from the right table even if the JOIN condition does not match any records in the left table.
2) **Left JOIN**: Left JOIN is also known as Left Outer JOIN. This returns all the rows as a result of the left table even if JOIN condition does not match any records in the right table. This is exactly the opposite of Right JOIN.
3) **Outer/Full JOIN**: Full JOIN return results in combining the result of both the Left JOIN and Right JOIN.
#### Explain the Primary Key and Composite Key.
* **The primary key** is that column of the table whose every row data is uniquely identified. Every row in the table must have a primary key and no two rows can have the same primary key. Primary key value can never be null nor can it be modified or updated.
* **Composite Key** is a form of the candidate key where a set of columns will uniquely identify every row in the table.

#### What do you understand by the Unique key?
A Unique key is the same as the primary key whose every row data is uniquely identified with a difference of null value i.e. Unique key allows one value as a NULL value.

#### Differentiate between ‘DELETE’, ‘TRUNCATE’ and ‘DROP’ commands.
* After the execution of **‘DELETE’** operation, COMMIT and ROLLBACK statements can be performed to retrieve the lost data.
* After the execution of **‘TRUNCATE’** operation, COMMIT, and ROLLBACK statements cannot be performed to retrieve the lost data.
* **‘DROP’** command is used to drop the table or key like the primary key/foreign key.

