# General

- Short queries can be written to a single line with a semicolon at the end, e.g.: `SELECT * FROM tbl WHERE amount > 0;`
- More complex queries should span to multiple lines with a semicolon at a new line:

```sql
-- Good
SELECT
  employee_number
  ,first_name
  ,last_name
FROM employee
WHERE department_number = 23
;

-- Bad
SELECT employee_number, first_name, last_name FROM employee
WHERE department_number = 23
```

- When a SQL clause (`SELECT`, `FROM`, etc.) has a single item it can be written in the same line as the clause.
  - However, multiple items should be written to separate lines.

```sql
-- Good
SELECT
  employee_number
  ,first_name
FROM employee
WHERE department_number = 23
;

-- Also good
SELECT
  employee_number
  ,first_name
FROM
  tbl
WHERE
  department_number = 23
  
-- Bad
SELECT employee_number
  first_name
FROM employee
WHERE department_number = 23
;
```

- Keywords and function names should be capitalized (`SELECT`, `GROUP BY`, `COALESCE`, etc.)
- Field names should be lowercased
- Use spaces instead of tabs.
  - 2 or 4 spaces are the most common. Choose whatever you prefer, but be consistent.
  - There is an insert tabs as spaces option in every text editor / DB tools, so you can still use tabs, but spaces will be inserted instead. 
- Use underscores (`_`) in table and field names. (`account_id` instead of `accountId`)
- Adding extra whitespace for better readibility is fine, although not required

```sql
-- Good
SELECT
  CASE WHEN dep.department_name IN ('Finance', 'Accounting') THEN 1 ELSE 0 END AS fin_flag
  ,CASE WHEN dep.department_name = 'IT' THEN 1 ELSE 0 END                      AS it_flag
  
-- Also good, but more readable thanks to additional whitespace
SELECT
   CASE WHEN dep.department_name IN ('Finance', 'Accounting') THEN 1 ELSE 0 END AS fin_flag
  ,CASE WHEN dep.department_name = 'IT'                       THEN 1 ELSE 0 END AS it_flag
```

# Aliasing

- Always use aliases with an explicit `AS` keyword.
  - In Oracle you can't use the `AS` keyword for aliasing table names in `FROM` and `JOIN` clauses. Instead use extra whitespace to make the aliases more noticable.
- Field name aliases and table aliases can be aligned together or separately

- When using aliases always reference the field names explicitly.

```sql
-- Good
SELECT
  emp.employee_number
  ,emp.first_name
  ,emp.department_number
  ,dep.department_name
FROM employee   AS emp
JOIN department AS dep
  ON emp.department_number = dep.department_number
;

-- Bad: Field names should be aliased explicitly.
SELECT
  employee_number
  ,first_name
  ,emp.department_number
  ,department_name
FROM employee   AS emp
JOIN department AS dep
  ON emp.department_number = dep.department_number
;
```

```sql
-- Good
SELECT
  emp.employee_number                     AS employee_id
  ,emp.first_name || ' ' || emp.last_name AS employee_name
  ,dep.department_number
FROM
  employee    AS emp
JOIN
  department  AS dep
  ON emp.department_number = dep.department_number

-- Also good
SELECT
  emp.employee_number                     AS employee_id
  ,emp.first_name || ' ' || emp.last_name AS employee_name
  ,dep.department_number
FROM
  employee                                AS emp
JOIN
  department                              AS dep
  ON emp.department_number = dep.department_number
```

# SELECT clause

- Put field names and expressions to new rows
- Always put the comma at the start
  - It's easier to find missing commas when they are aligned
  - The last column is much more likely to be commented out

```sql

# Good
SELECT
  employee_number
  ,first_name
  ,last_name
  ,first_name || ' ' || last_name AS full_name
FROM
  employee
;

# Bad
SELECT employee_number, first_name, last_name, first_name || ' ' || last_name AS full_name
FROM ...
;
```
  
# FROM clause
- The table name can be placed in a new row, or directly after the `FROM` clause. It's up to preference.
- When using a single table in the query no alias is required, however in case of `JOIN`s always use an alias.
- Never use the `FROM`, `WHERE` type of joining.

```sql

-- Good
SELECT
  *
FROM
  employee         AS emp
JOIN
  department       AS dep
  ON emp.department_number = dep.department_number
;

-- Bad: Joining in the WHERE clause
SELECT
  *
FROM
  employee AS emp, department AS dep
WHERE emp.department_number = dep.department_number
;
```

# JOIN clause
- Align the table name, and the `ON`, `AND` keywords to the same column
- Use source -> destination order. e.g.: `source_table.column_name = destination_table.column_name`
  - Using the same order in the code allows you to see which tables are used in a `JOIN`.

```sql
-- Good
SELECT
  *
FROM
  employee    AS emp
JOIN
  department  AS dep
  ON emp.department_number = dep.department_number
  AND emp.department_type_code = 2
JOIN
  positions   AS pos
  ON emp.position_id = pos.position_id
;
```

- The order in the `ON` clause should always be the following:
  1. The fields to `JOIN` by
  2. Filtering the destination table (if needed)
  
```sql
-- Good
SELECT
  *
FROM employee    AS emp
JOIN department  AS dep
  ON emp.department_number = dep.department_number
  AND emp.department_type_code = 2
;

-- Bad: Filtering should be at the bottom
SELECT
  *
FROM employee    AS emp
JOIN department  AS dep
  ON emp.department_type_code = 2
  AND emp.department_number = dep.department_number
;
```


- Always use aliases when using the `JOIN` clause
- Use meaningful table aliases (e.g.: emp for employee, acct for account)
  - Prefer to use 3-4 letter aliases. It's okay to use shorter or longer aliases sometimes.

```sql
-- Good
SELECT
  *
FROM
  employee    AS emp
LEFT JOIN
  department  AS dep
  ON emp.department_number = dep.department_number
;

-- Bad: Not meaningful aliases
SELECT
  *
FROM
  employee    AS x
LEFT JOIN
  department  AS y
  ON x.department_number = y.department_number
;
```

- Prefer `LEFT JOIN` over `RIGHT JOIN` if possible. 

```sql
-- Good
SELECT
  *
FROM
  employee    AS emp
LEFT JOIN
  department  AS dep
  ON emp.department_number = dep.department_number
;

-- Bad
SELECT
  *
FROM
  department  AS dep
RIGHT JOIN
  employee    AS emp
  ON dep.department_number = emp.department_number
;
```

- Write `LEFT JOIN` instead of `LEFT OUTER JOIN`, and `RIGHT JOIN` instead of `RIGHT OUTER JOIN`. Writing `OUTER` is obsolate.

# CASE WHEN

- Short cases can be written to a single line
- Longer cases should span to multiple lines:
  - `CASE` and `END` should be at the same indentation level
  - Every `WHEN` conditional should be written to new lines with one indent further.  

```sql
SELECT
  CASE WHEN employee_number > 5 THEN 'Greater than 5' ELSE 'Less than 5' END AS gr5_flag
  ,CASE
    WHEN employee_number > 10 THEN '10+'
    WHEN employee_number > 5 THEN '6-10'
    ELSE '0-5'
   END AS employee_no_bin
```

# Comments
Comments can be generally used for:

1. Writing useful comments to explain:
- Why a table is `JOIN`-ed
- What a long code snippet is doing
- What a certain hard coded id stands for

```sql
...
WHERE house_id = 17 -- Apartment
```

Comments should have a space after the comment to more visibly differentiate between an unused code line and helper text.

2. Breaking up the code to different sections

```sql
------------------------------------------------
-- Section 1 -----------------------------------
------------------------------------------------

...

------------------------------------------------
-- Section 2 -----------------------------------
------------------------------------------------

...
```

3. Commenting out unused code that might still be useful later on.
- Unused code should not include a space after the comment symbols

```sql
SELECT *
FROM employee
WHERE
  department_number = 5 -- IT dep
  --AND employee_number = 17
```
