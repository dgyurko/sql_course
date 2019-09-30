# History of SQL in a nutshell

- SQL was initially developed at IBM by [Donald D. Chamberlin](https://en.wikipedia.org/wiki/Donald_D._Chamberlin) and [Raymond F. Boyce](Raymond F. Boyce)
- Based on the relational model from [Ted Codd](https://en.wikipedia.org/wiki/Edgar_F._Codd) in the early 1970s.
- It was initially called **SEQUEL** (Structured English Query Language)
- By 1986, **ANSI** and **ISO** standard groups officially adopted the standard "Database Language SQL" language definition. 
  - New versions of the standard were published in 1989, 1992, 1996, 1999, 2003, 2006, 2008, 2011 and 2016.
- Main functionalities exist in all relational database management systems (RDMBS) (e.g.: `SELECT`, `CREATE TABLE`), but **most RDBMS differ from each other**.

Popular RDBMS: Oracle, MS SQL, PostgreSQL, MySQL, Presto, SQLite, Teradata

Source: [Wikipedia](https://en.wikipedia.org/wiki/SQL)

# What is an RDBMS?

## Tables
In a Relational Database Management System (RDBMS) **data are organized into tables**. You can think of database tables as excel sheets for now.

## Schemas

Schemas serve two purposes:

1. Organizing tables into schemas.
2. Namespacing

### Organizing tables
**Schemas provide a way of categorizing objects in a database**. It is really useful when several applications share a single database and while there is some common set of data that all application accesses. [\[1\]](https://stackoverflow.com/a/5324002/4509096)

### Namespacing
Schemas also have a namespacing ability as well: It is possible for multiple tables to have the same name if they are in different schemas. i.e.: `bakery.customers`, `pastry.customers`.

## Databases
A database consists of multiple schemas.

So the relation is: `Database > Schema > Table`

# Different parts of SQL

## Data Definition Language (DDL)

## Data Manipulation Language (DML)

## Data Control Language (DCL)

# SQL query structure

## What goes in the SELECT clause

## What goes in the FROM clause

## What goes in the WHERE clause

# Solving exercises using SELECT, FROM, WHERE, ORDER BY, LIMIT clauses

# Aggregation functions (MIN, MAX, SUM, COUNT, AVG, ...)

# GROUP BY clause

# HAVING clause

# Exercises using GROUP BY, HAVING
