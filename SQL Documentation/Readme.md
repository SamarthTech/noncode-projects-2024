

# SQL Documentation

## Introduction

Structured Query Language (SQL) is a powerful language used to interact with relational databases. From simple data retrieval to complex data manipulation, SQL provides a range of tools to manage and control data efficiently. This documentation outlines the key concepts, commands, functions, and best practices to help you understand and work with SQL effectively.

This project is part of Hacktoberfest, and contributions are welcome!

---

## Table of Contents

1. [What is SQL?](#what-is-sql)
2. [Key SQL Concepts](#key-sql-concepts)
3. [Basic SQL Commands](#basic-sql-commands)
    - SELECT
    - INSERT
    - UPDATE
    - DELETE
4. [Data Definition Language (DDL)](#data-definition-language-ddl)
    - CREATE
    - ALTER
    - DROP
5. [Data Manipulation Language (DML)](#data-manipulation-language-dml)
6. [Data Control Language (DCL)](#data-control-language-dcl)
7. [SQL Constraints](#sql-constraints)
    - Primary Key
    - Foreign Key
    - Unique
    - Check
8. [SQL Functions](#sql-functions)
    - Aggregate Functions
    - String Functions
    - Date Functions
9. [Normalization](#normalization)
10. [SQL Joins](#sql-joins)
11. [Subqueries and Nested Queries](#subqueries-and-nested-queries)
12. [Transactions and ACID Properties](#transactions-and-acid-properties)
13. [Views in SQL](#views-in-sql)
14. [Stored Procedures and Functions](#stored-procedures-and-functions)
15. [Indexes](#indexes)
16. [Best Practices](#best-practices)
17. [Advanced Topics](#advanced-topics)
    - Window Functions
    - Common Table Expressions (CTE)
    - Partitioning
18. [Conclusion](#conclusion)
19. [Contributing](#contributing)

---

## What is SQL?

SQL, or **Structured Query Language**, is a standard programming language designed for managing and manipulating relational databases. It allows for a wide range of operations, including querying data, updating records, and defining database structures. SQL is essential for data professionals, developers, and database administrators to work with data efficiently.

---

## Key SQL Concepts

1. **Tables**: Tables store data in rows and columns.
2. **Schemas**: A logical structure defining the organization of data in a database.
3. **Keys**: 
    - **Primary Key**: Uniquely identifies each record.
    - **Foreign Key**: A field that links two tables together.
4. **Indexes**: Improve data retrieval speed by creating data pointers.
5. **Constraints**: Ensure data integrity by restricting the values that can be stored in a table.

---

## Basic SQL Commands

### SELECT
Used to query data from a table.

```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

### INSERT
Adds new records into a table.

```sql
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```

### UPDATE
Modifies existing records in a table.

```sql
UPDATE table_name SET column1 = value1 WHERE condition;
```

### DELETE
Deletes records from a table.

```sql
DELETE FROM table_name WHERE condition;
```

---

## Data Definition Language (DDL)

### CREATE
Creates a new table or other database objects.

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype
);
```

### ALTER
Modifies an existing object.

```sql
ALTER TABLE table_name ADD column_name datatype;
```

### DROP
Removes a database object.

```sql
DROP TABLE table_name;
```

---

## Data Manipulation Language (DML)

DML commands allow manipulation of the data within tables.

- **SELECT**: Retrieves data.
- **INSERT**: Adds new data.
- **UPDATE**: Modifies data.
- **DELETE**: Removes data.

---

## Data Control Language (DCL)

### GRANT
Provides user access to database objects.

```sql
GRANT SELECT, INSERT ON table_name TO user;
```

### REVOKE
Removes user access.

```sql
REVOKE SELECT, INSERT ON table_name FROM user;
```

---

## SQL Constraints

### Primary Key
Uniquely identifies each record.

```sql
CREATE TABLE Employees (
    ID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

### Foreign Key
Links two tables together.

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

### Unique
Ensures that values in a column are unique.

```sql
ALTER TABLE Employees ADD CONSTRAINT UC_Employee UNIQUE (Email);
```

### Check
Ensures that a condition is met before inserting a value.

```sql
ALTER TABLE Employees ADD CONSTRAINT CHK_Age CHECK (Age >= 18);
```

---

## SQL Functions

### Aggregate Functions
- **COUNT()**: Returns the number of rows.
- **SUM()**: Returns the sum of a column.
- **AVG()**: Returns the average value.

### String Functions
- **CONCAT()**: Combines two or more strings.
- **UPPER()**: Converts a string to uppercase.
- **LOWER()**: Converts a string to lowercase.

### Date Functions
- **CURRENT_DATE()**: Returns the current date.
- **DATEDIFF()**: Returns the difference between two dates.

---

## Normalization

Normalization is the process of structuring a relational database to reduce redundancy and improve data integrity. It typically involves breaking down larger tables into smaller, related tables and using keys to establish relationships.

---

## SQL Joins

Joins combine rows from two or more tables:

- **INNER JOIN**: Returns records with matching values in both tables.
- **LEFT JOIN**: Returns all records from the left table and matching records from the right table.
- **RIGHT JOIN**: Returns all records from the right table and matching records from the left table.
- **FULL JOIN**: Returns all records when there’s a match in either table.

```sql
SELECT columns FROM table1
INNER JOIN table2 ON table1.id = table2.id;
```

---

## Subqueries and Nested Queries

Subqueries are queries inside other queries to further refine results.

```sql
SELECT * FROM Employees WHERE Salary > (SELECT AVG(Salary) FROM Employees);
```

---

## Transactions and ACID Properties

**Transactions** ensure that SQL operations either fully complete or fully fail, maintaining data integrity. ACID (Atomicity, Consistency, Isolation, Durability) are properties that ensure reliable transaction processing.

```sql
BEGIN TRANSACTION;
UPDATE Accounts SET Balance = Balance - 100 WHERE AccountID = 1;
UPDATE Accounts SET Balance = Balance + 100 WHERE AccountID = 2;
COMMIT;
```

---

## Views in SQL

Views are virtual tables created from SQL queries.

```sql
CREATE VIEW EmployeeView AS SELECT Name, Department FROM Employees;
```

---

## Stored Procedures and Functions

### Stored Procedure
Reusable SQL code stored in the database.

```sql
CREATE PROCEDURE GetEmployees AS SELECT * FROM Employees;
```

### Function
Returns a single value from a SQL query.

```sql
CREATE FUNCTION GetEmployeeCount() RETURNS INT AS
RETURN (SELECT COUNT(*) FROM Employees);
```

---

## Indexes

Indexes improve the speed of data retrieval by creating fast access paths to data.

```sql
CREATE INDEX idx_employee_name ON Employees (Name);
```

---

## Best Practices

1. **Use Proper Indexing**: Ensure important columns are indexed for performance.
2. **Avoid SELECT ***: Retrieve only required columns.
3. **Normalize Data**: Minimize redundancy.
4. **Use Prepared Statements**: Protect against SQL injection.
5. **Backup Regularly**: Ensure data is backed up consistently.

---

## Advanced Topics

### Window Functions
Perform calculations across a set of table rows related to the current row.

```sql
SELECT Name, Salary, RANK() OVER (ORDER BY Salary DESC) AS Rank FROM Employees;
```

### Common Table Expressions (CTE)
Temporary result sets used within a query.

```sql
WITH EmployeeCTE AS (SELECT * FROM Employees WHERE Salary > 5000)
SELECT * FROM EmployeeCTE;
```

### Partitioning
Dividing a large table into smaller, manageable pieces.

---

## Conclusion

This SQL documentation provides a comprehensive guide, from basic commands to advanced techniques, for managing relational databases. Whether you're querying data or optimizing database performance, SQL offers powerful tools for efficient data management.

---

