# Unit 4: Normalization

## Overview
Normalization systematically reduces data redundancy and improves integrity in relational databases through decomposition into smaller, well-structured tables while maintaining relationships through foreign keys.

## Learning Objectives
- Understand purpose and need for normalization
- Learn functional dependency concepts
- Master 1NF, 2NF, 3NF, and BCNF
- Learn denormalization trade-offs

## Core Concepts

### Problems Without Normalization
- Insertion Anomalies: Cannot insert data without duplicating information
- Update Anomalies: Changes require updates in multiple places
- Deletion Anomalies: Deleting records causes unintended information loss
- Data Redundancy: Same information stored multiple times
- Inconsistency: Different values for the same entity

### Functional Dependency
Attribute B functionally depends on A (A -> B) if a value of A determines a unique value of B.

Example: StudentID -> StudentName (one StudentID maps to exactly one StudentName)

### First Normal Form (1NF)
**Rules:**
1. All attribute values must be atomic (indivisible)
2. No repeating groups
3. Primary key must exist

**Problem Example:**
```
Student(StudentID, Name, Phones)
- Phones contains multiple values: {9876543210, 9988776655}
```

**Solution:**
```
Student(StudentID, Name)
Phone(StudentID, PhoneNumber)
```

### Second Normal Form (2NF)
**Rules:**
1. Must be in 1NF
2. All non-key attributes fully dependent on entire primary key
3. No partial dependencies

**Partial Dependency:** A non-key attribute depends on part of a composite primary key.

**Problem Example:**
```
Enrollment(StudentID, CourseID, CourseName)
- CourseName depends ONLY on CourseID, not on StudentID
```

**Solution:**
```
Enrollment(StudentID, CourseID)
Course(CourseID, CourseName)
```

### Third Normal Form (3NF)
**Rules:**
1. Must be in 2NF
2. No transitive dependencies
3. Non-key attributes depend only on primary key

**Transitive Dependency:** Non-key attribute A depends on primary key, and another non-key attribute B depends on A.

**Problem Example:**
```
Student(StudentID, Name, DeptID, DeptHead)
- DeptHead -> DeptID -> StudentID (transitive)
```

**Solution:**
```
Student(StudentID, Name, DeptID)
Department(DeptID, DeptHead)
```

### Boyce-Codd Normal Form (BCNF)
**Rules:**
1. Must be in 3NF
2. Every determinant must be a candidate key

BCNF is stricter; handles rare 3NF exceptions.

## Normalization Examples

### Step-by-Step Example
**Unnormalized:**
```
StudentCourse(SID, Name, Courses)
1, Raj, Database|OS
2, Priya, WebDev
```

**After 1NF:**
```
Student(SID, Name)
1, Raj
2, Priya

Enrollment(SID, Course)
1, Database
1, OS
2, WebDev
```

**After 2NF and 3NF:** (Already satisfied)

## Exam Notes
- 1NF: No repeating groups, atomic values
- 2NF: No partial dependencies in composite keys
- 3NF: No transitive dependencies
- Most databases use 3NF as standard
- BCNF is ideal but rare
- Denormalization trades performance for simplicity
- Always identify functional dependencies

## Short Questions
1. What problems does normalization solve?
2. Define functional dependency with examples.
3. What are insertion, update, deletion anomalies?
4. Explain 1NF with violation examples.
5. What is partial dependency? How does 2NF fix it?
6. Explain transitive dependency.
7. Difference between 3NF and BCNF?
8. When is denormalization justified?
9. Design a normalized database for a bookstore.
10. Can a table be 2NF but not 3NF? Explain.

## Key Takeaways
- Normalization eliminates anomalies and redundancy
- Functional dependencies drive normal form definitions
- 3NF is practical; 1NF and 2NF are stepping stones
- Balance between normalization and query performance
- Document dependencies for good database design
