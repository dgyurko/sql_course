# SQL course

## Description
This repo contains teaching materials for a SQL course I am teaching at KRE. The aim of this course is to get familiar with the data manipulation (DML) and data definition (DDL) parts of SQL as well as learning design concepts.

## Syllabus

- Week 1
  - Connecting to the SQL environment: Amazon RDS - PostgreSQL (Credentials not included in the Repo)
  - History of SQL in a nutshell
  - What is an RDBMS?
  - Different parts of SQL
    - Data Definition Language (**DDL**)
    - Data Manipulation Language (**DML**)
    - Data Control Language (**DCL**)
  - Database - Schemas - Tables
  - SQL query structure
    - What goes in the `SELECT` clause
    - What goes in the `FROM` clause
    - What goes in the `WHERE` clause
  - Solving exercises using `SELECT`, `FROM`, `WHERE`, `ORDER BY`, `LIMIT` clauses
  - Aggregation functions (`MIN`, `MAX`, `SUM`, `COUNT`, `AVG`, ...)
  - `GROUP BY` clause
  - `HAVING` clause
  - Exercises using `GROUP BY`, `HAVING`
- Week 2
  - How to use comments? (`--`, `/**/`)
  - Style guide: How to format SQL queries?
  - Common SQL data types:
    - Integer
    - Float / Double
    - Varchar / Char
    - Boolean
  - SQL operators
  - Different types of `JOIN`s
  - `CASE WHEN`...
  - Subqueries
  - Solving more complex exercises using `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `JOIN`, `ORDER BY`, `LIMIT` clauses.
  - Extra: Connecting to the database using `R` via the `DBI` and `dbplyr` packages.
- Week 3
  - String functions
  - Date functions
  - Using regular expressions (**Regex**)
  - Exercises involving string and date manipulation
  - Slowly changing dimensions (**SCD**)
- Week 4
  - The purpose of views and how to create them
  - `CREATE TABLE`
  - Unique / Non-unique primary keys
  - `NULL` value: Why they are special
  - `UNION`, `INTERSECT`, `MINUS`
  - Indexes
  - Solving exercises using `TEMP TABLE`, `UNION`
- Week 5
  - Window functions (`ROW_NUMBER`, `LEAD`, `LAG`)
  - Sliding windows
  - Solving exercises using Window functions
- Week 6
  - Design patterns: **Snowflake** and **Starschema**
  - Using temp tables
  - Common table expressions (**CTE**)
  - Exercises for Database design

## License
All of the materials can be reused under the MIT License.
