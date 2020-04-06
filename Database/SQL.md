* [SQL Basics](#fireSQL-Basics)
* [SQL Query](#fireSQL-Query)
* [Join](#fireJoin)
* [View](#fireView)
* [Index](#fireIndex)
* [Transaction](#fireTransaction)

## :fire:SQL Basics
### What is SQL?
* **Structured Query language**, SQL is an ANSI(American National Standard Institute) standard programming language that is designed specifically for storing and managing the data in the relational database management system (RDBMS) using all kinds of data operations.
* **SQL query**
`Select distinct DEPARTMENT from Worker;`
The following query is using the correlated subquery to return the 5th highest salary:
`SELECT Salary
FROM Worker W1
WHERE 4 = (
 SELECT COUNT( DISTINCT ( W2.Salary ) )
 FROM Worker W2
 WHERE W2.Salary >= W1.Salary
 );`
 
 ### How many SQL statements are used? Define them. What are the different subsets of SQL?
 SQL statements are basically divided into three categories, DDL, DML, and DCL.
 * **Data Definition Language (DDL)** commands are used to define the structure that holds the data. These commands are auto-committed i.e. changes done by the DDL commands on the database are saved permanently.
 * **Data Manipulation Language (DML)** commands are used to manipulate the data of the database. These commands are not auto-committed and can be rolled back.
 * **Data Control Language (DCL)** commands are used to control the visibility of the data in the database like revoke access permission for using data in the database.

 ### Enlist some commands of DDL, DML, and DCL.
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

### Define DML Compiler.
DML compiler translates DML statements in a query language into a low-level instruction and the generated instruction can be understood by Query Evaluation Engine.

### What is DDL interpreter?
DDL Interpreter interprets the DDL statements and records the generated statements in the table containing metadata.

### Enlist the advantages of SQL.
* Simple SQL queries can be used to retrieve a large amount of data from the database very quickly and efficiently.
* SQL is easy to learn and almost every DBMS supports SQL.
* It is easier to manage the database using SQL as no large amount of coding is required.

## :fire:SQL Query
#### comment
    SELECT *
    FROM mytable; -- 注释
    /* 注释1
    注释2 */
    
#### Create database
    CREATE DATABASE test;
    USE test;

#### Create table
    CREATE TABLE mytable (
    # int 类型，不为空，自增
    id INT NOT NULL AUTO_INCREMENT,
    # int 类型，不可为空，默认值为 1，不为空
    col1 INT NOT NULL DEFAULT 1,
    # 变长字符串类型，最长为 45 个字符，可以为空
    col2 VARCHAR(45) NULL,
    # 日期类型，可为空
    col3 DATE NULL,
    # 设置主键为 id
    PRIMARY KEY (`id`));

#### Modify table

    ALTER TABLE mytable
    ADD col CHAR(20); //添加列
    DROP COLUMN col; //删除列
    DROP TABLE mytable; //删除表
Insert

    INSERT INTO mytable(col1, col2)
    VALUES(val1, val2);
    //
    INSERT INTO mytable1(col1, col2)
    SELECT col1, col2
    FROM mytable2;
    //
    CREATE TABLE newtable AS
    SELECT * FROM mytable;
Update

    UPDATE mytable
    SET col = val
    WHERE id = 1;
Delete

    DELETE FROM mytable
    WHERE id = 1;
Select

    SELECT DISTINCT col1, col2
    FROM mytable;
    //
    SELECT *
    FROM mytable
    LIMIT 5;
    //sort
    SELECT *
    FROM mytable
    ORDER BY col1 DESC, col2 ASC;
    //
    SELECT cust_name, (SELECT COUNT(*)
                       FROM Orders
                       WHERE Orders.cust_id = Customers.cust_id)
                       AS orders_num
    FROM Customers
    ORDER BY cust_name;
Group

    SELECT col, COUNT(*) AS num
    FROM mytable
    GROUP BY col
    ORDER BY num;

#### What's constraints?
 * Constraints are the rules enforced on the data columns of a table. These are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the database.
* Constraints could be either on a column level or a table level. The column level constraints are applied only to one column, whereas the table level constraints are applied to the whole table.

 * Following are some of the most commonly used constraints available in SQL. These constraints have already been discussed in SQL - RDBMS Concepts chapter, but it’s worth to revise them at this point.
        * **NOT NULL** Constraint − Ensures that a column cannot have NULL value.
        * **DEFAULT** Constraint − Provides a default value for a column when none is specified.
        * **UNIQUE** Constraint − Ensures that all values in a column are different.
        * **PRIMARY** Key − Uniquely identifies each row/record in a database table.
        * **FOREIGN** Key − Uniquely identifies a row/record in any of the given database table.
        * **CHECK** Constraint − The CHECK constraint ensures that all the values in a column satisfies certain conditions.
        * **INDEX** − Used to create and retrieve data from the database very quickly.
        
#### How do you delete duplicate rows from a table?
Use a NOT EXISTS() to a subquery containing a MIN() or MAX() aggregate, or use ROW_NUMBER.

#### Differentiate between ‘DELETE’, ‘TRUNCATE’ and ‘DROP’ commands.
* After the execution of **‘DELETE’** operation, COMMIT and ROLLBACK statements can be performed to retrieve the lost data.
* After the execution of **‘TRUNCATE’** operation, COMMIT, and ROLLBACK statements cannot be performed to retrieve the lost data.
* **‘DROP’** command is used to drop the table or key like the primary key/foreign key.

## :fire:Join
### What do you understand by Join?
Join is the process of explaining the relationship between different tables by combining columns from one or more table having common values in each. When a table joins with itself, it is known as Self Join.

### Define Join types.
1) **Inner JOIN**: Inner JOIN is also known as a simple JOIN. This SQL query returns results from both the tables having a common value in rows.
```
SELECT A.value, B.value
FROM tablea AS A INNER JOIN tableb AS B
ON A.key = B.key;
```
2) **Natural JOIN**: This is a type of Inner JOIN that returns results from both the tables having the same data values in the columns of both the tables to be joined.
3) **Cross JOIN**: Cross JOIN return results as all the records where each row from the first table is combined with each row of the second table.
1) **Right JOIN**: Right JOIN is also known as Right Outer JOIN. This returns all the rows as a result from the right table even if the JOIN condition does not match any records in the left table.
2) **Left JOIN**: Left JOIN is also known as Left Outer JOIN. This returns all the rows as a result of the left table even if JOIN condition does not match any records in the right table. This is exactly the opposite of Right JOIN.
3) **Outer/Full JOIN**: Full JOIN return results in combining the result of both the Left JOIN and Right JOIN.

### How do you know if data exists in one table and not in another.
Do a left outer join where the linked field in table 2 is null

## :fire:View
* View is a virtual table that does not have its data on its own rather the data is defined from one or more underlying base tables.
* Views account for logical data independence as the growth and restructuring of base tables is not reflected in views.
### What are the advantages and disadvantages of views in the database?
- Advantages of Views:
    * As there is no physical location where the data in views is stored, it generates output without wasting resources.
    * Data access is restricted as it does not allow commands like insertion, updation, and deletion.
- Disadvantages of Views:
    * The view becomes irrelevant if we drop a table related to that view.
    * More memory is occupied when the view is created for large tables.
```
CREATE VIEW myview AS
SELECT Concat(col1, col2) AS concat_col, col3*col4 AS compute_col
FROM mytable
WHERE col5 = val;
```

## :fire:Index
### What do you understand by Index hunting?
* Index hunting is the process of boosting the collection of indexes which helps in improving the query performance as well as the speed of the database.
* An index refers to a performance tuning method of allowing faster retrieval of records from the table. An index creates an entry for each value and hence it will be faster to retrieve data.
```
CREATE INDEX index_name
ON table_name ( column1, column2.....);
```
### How to improve query performance using Index hunting?
Index hunting help in improving query performance by:
* Using a query optimizer to coordinate queries with the workload.
* Observing the performance and effect of index and query distribution.

### Differentiate between ‘Cluster’ and ‘Non-cluster’ index.
* **Clustered** Index alters the table and reorders the way in which the records are stored in the table. Data retrieval is made faster by using the clustered index.
* A **Non-clustered** index does alter the records that are stored in the table but creates a completely different object within the table.

### How many clustered indexes can you have in a table
1

## :fire:Transaction
![](https://camo.githubusercontent.com/5b729240000ac04e2c3e9d315e9b9716591496fe/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f696d6167652d32303139313230373232323233373932352e706e67)
```
START TRANSACTION
// ...
SAVEPOINT delete1
// ...
ROLLBACK TO delete1
// ...
COMMIT
```
### What is the Database transaction?
Sequence of operation performed which changes the consistent state of the database to another is known as the database transaction. After the completion of the transaction, either the successful completion is reflected in the system or the transaction fails and no change is reflected.
* Transactions are completed by COMMIT or ROLLBACK SQL statements, which indicate a transaction’s beginning or end.

### What is ACID?
The ACID acronym defines the properties of a database transaction, as follows:
* **Atomicity**: A transaction must be fully complete, saved (committed) or completely undone (rolled back). 
* **Consistency**: The transaction must be fully compliant with the state of the database as it was prior to the transaction. In other words, the transaction cannot break the database’s constraints.
* **Isolation**: Transaction data must not be available to other transactions until the original transaction is committed or rolled back.
* **Durability**: Transaction data changes must be available, even in the event of database failure.
