# Unit 2: Introduction to the Relational Model

## Overview
The relational model is a fundamental data model that organizes data into relations (tables). This unit introduces the core concepts and structure of the relational model.

## Learning Objectives
- Understand relation, attributes, and tuples
- Learn about primary keys and candidate keys
- Understand integrity constraints
- Learn relational algebra basics
- Understand functional dependencies

## Core Concepts

### Relations and Tables
A relation is a 2D table with rows and columns. Each row represents a tuple (record) and each column represents an attribute (field).

### Keys
- **Primary Key**: Uniquely identifies each tuple
- **Candidate Key**: Attributes that could serve as primary key
- **Foreign Key**: Links to primary key in another relation

### Integrity Constraints
- Entity Integrity: Primary key cannot be NULL
- Referential Integrity: Foreign keys must reference valid primary keys
- Domain Constraint: Attributes have defined data types
- User-defined Constraints: Custom business rules

## Exam Notes
- Relations are the basis of relational databases
- Primary key uniquely identifies tuples
- Foreign keys maintain referential integrity
- Normalization eliminates data redundancy
- Relational algebra provides query operations

## Short Questions
1. Define a relation and tuple
2. What is a primary key?
3. Explain entity integrity constraint
4. What are foreign keys?
5. Name the main integrity constraints

## Key Takeaways
- Relational model organizes data into tables
- Keys maintain uniqueness and relationships
- Integrity constraints ensure data quality
