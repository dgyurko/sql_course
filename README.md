# SQL course

## Description
This repo contains teaching materials for a SQL course I am teaching at KRE University. The aim of this course is to get students familiar with the data manipulation (DML) and data definition (DDL) parts of SQL as well as learning design concepts.

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
- Week 2
  - How to use comments? (`--`, `/**/`)
  - Using `DISTINCT`
  - Aggregation functions (`MIN`, `MAX`, `SUM`, `COUNT`, `AVG`, ...)
  - `GROUP BY` clause
  - `HAVING` clause
  - Exercises using `GROUP BY`, `HAVING`, `DISTINCT`
- Week 3
  - Common SQL data types:
    - Integer
    - Float / Double
    - Varchar / Char / Text
    - Boolean
  - SQL operators (`=`, `>`, `<`, `<=`, `<>`, `IN`)
  - The purpose of views and how to create them
  - Different types of `JOIN`s
  - `NULL` value: Why they are special. `COALESCE` function.
  - Solving more complex exercises using `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `JOIN`, `ORDER BY`, `LIMIT` clauses.
- Week 4
  - `CASE WHEN` statements
  - Subqueries
  - `LIKE` operator
  - String functions
  - Date functions
  - Exercises involving string and date manipulation
- Week 5
  - Using regular expressions (**Regex**)
- Week 6
  - Window functions (`ROW_NUMBER`, `LEAD`, `LAG`)
  - Sliding windows
  - Solving exercises using Window functions
- Week 7
  - DDL: `CREATE TABLE`, `ALTER TABLE` statements
  - `UNION`, `INTERSECT`, `MINUS`
  - `EXISTS` clause
  - Slowly changing dimensions (**SCD**)
- Week 8
  - Design patterns: **Snowflake** and **Starschema**
  - Using temp tables
  - Common table expressions (**CTE**)
  - Indexes
  - Exercises for Database design

## License
All of the materials can be reused under the MIT License.
