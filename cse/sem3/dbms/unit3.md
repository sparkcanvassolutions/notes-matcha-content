# Unit 3: SQL Fundamentals

## Overview
SQL (Structured Query Language) is the standard language for managing and querying relational databases. This unit covers the essential SQL commands and syntax used to interact with databases. SQL enables users to create, retrieve, update, and delete data from databases efficiently.

## Learning Objectives
- Learn SQL data definition language (DDL) commands: CREATE, ALTER, DROP
- Understand SQL data manipulation language (DML) commands: INSERT, SELECT, UPDATE, DELETE
- Master SELECT queries with WHERE clauses
- Learn about joins to combine data from multiple tables
- Understand aggregate functions and grouping data
- Learn about subqueries and nested SELECT statements

## Core Concepts

### DDL Commands

#### CREATE TABLE
Creates a new table with specified columns and constraints:
```
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Age INT,
    Email VARCHAR(100)
);
```
Defines table structure with columns, data types, and constraints. PRIMARY KEY ensures uniqueness. NOT NULL enforces non-empty values.

#### ALTER TABLE
Modifies an existing table:
```
ALTER TABLE Students ADD COLUMN Department VARCHAR(50);
ALTER TABLE Students MODIFY COLUMN Name VARCHAR(100);
```
Allows adding columns, removing columns, or changing column properties.

#### DROP TABLE
Deletes entire table:
```
DROP TABLE Students;
```
Permanently removes all data. Use carefully!

### DML Commands

#### INSERT
Adds new records:
```
INSERT INTO Students VALUES (1, 'Raj Kumar', 20, 'raj@example.com');
INSERT INTO Students (StudentID, Name) VALUES (2, 'Priya Singh');
```
Inserts single or multiple rows. Specify columns for selective insertion.

#### SELECT
Retrieves data from tables:
```
SELECT * FROM Students;
SELECT Name, Email FROM Students WHERE Age > 20;
SELECT DISTINCT Department FROM Students;
SELECT * FROM Students ORDER BY Age DESC;
```
Most versatile command. Uses WHERE for filtering, ORDER BY for sorting, DISTINCT for unique values.

#### WHERE Clause Operators
- Comparison: =, !=, <>, <, >, <=, >=
- Logical: AND, OR, NOT
- Pattern: LIKE (with % and _ wildcards)
- Range: BETWEEN... AND
- List: IN
- Null: IS NULL, IS NOT NULL

#### UPDATE
Modifies existing records:
```
UPDATE Students SET Age = 21 WHERE StudentID = 1;
UPDATE Students SET Age = Age + 1, Department = 'CSE';
```
Changes column values. WHERE clause specifies which rows to update.

#### DELETE
Removes records:
```
DELETE FROM Students WHERE StudentID = 1;
DELETE FROM Students; -- Deletes all records!
```
Removes rows matching condition. Always use WHERE clause carefully!

### Aggregate Functions
- COUNT(): Counts rows
- SUM(): Sums numeric values
- AVG(): Calculates average
- MAX(): Finds maximum value
- MIN(): Finds minimum value

```
SELECT COUNT(*) FROM Students;
SELECT AVG(Age) FROM Students;
SELECT Department, COUNT(*) FROM Students GROUP BY Department;
```

### JOINs
Combines data from multiple tables:

#### INNER JOIN
Returns matching records only:
```
SELECT s.Name, e.CourseName FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID;
```

#### LEFT JOIN
Includes all rows from left table:
```
SELECT s.Name, e.CourseName FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID;
```

#### RIGHT JOIN
Includes all rows from right table.

#### FULL JOIN  
Includes all rows from both tables.

### Subqueries
Queries within queries:
```
SELECT Name FROM Students WHERE Age > (SELECT AVG(Age) FROM Students);
SELECT * FROM Students WHERE StudentID IN (SELECT StudentID FROM Enrollments);
```
Can be in SELECT, WHERE, or FROM clauses.

## Exam Notes
- SQL is case-insensitive for keywords but column names are database-specific
- NULL is special value; use IS NULL / IS NOT NULL
- DISTINCT removes duplicates; use for efficiency
- Join conditions are mandatory to avoid Cartesian products
- Aggregate functions ignore NULL values
- Use WHERE before GROUP BY for better performance
- Subqueries can nest multiple levels deep
- Primary key enforces uniqueness in INSERT operations

## Practical Examples

### Example 1: Complex SELECT with Multiple Conditions
```
SELECT StudentID, Name, Age FROM Students
WHERE Age >= 20 AND (Department = 'CSE' OR Department = 'IT')
ORDER BY Age DESC;
```

### Example 2: GROUP BY with HAVING
```
SELECT Department, COUNT(*) as Total
FROM Students
GROUP BY Department
HAVING COUNT(*) > 3
ORDER BY Total DESC;
```

### Example 3: JOIN with Aggregation
```
SELECT s.Department, COUNT(e.EnrollmentID) as Enrollments
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
GROUP BY s.Department;
```

## Short Questions
1. Explain DDL vs DML commands with examples.
2. What is the difference between DELETE and DROP?
3. Explain the SELECT query syntax.
4. How does WHERE clause work in SQL?
5. Differentiate between INNER JOIN and LEFT JOIN.
6. Give five examples of aggregate functions.
7. What is the purpose of GROUP BY clause?
8. Explain the difference between WHERE and HAVING.
9. What are subqueries? Provide an example.
10. Write a query to find students with above-average age.

## Key Takeaways
- SQL is fundamental for database management
- DDL manages database structure; DML manages data
- SELECT is the primary query command
- WHERE filters data; HAVING filters groups
- JOINs combine data from multiple tables
- Aggregate functions perform calculations
- Subqueries provide nested query capability
- Always specify WHERE clause to avoid unintended data loss
- Use indexes on frequently queried columns
- Practice writing complex queries regularly
