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

- Keywords and function names should be capitalized
- Field names should be lowercased
- Use spaces instead of tabs.
  - 2 or 4 spaces are the most common. Choose whatever you prefer, but be consistent.
  - There is an insert tabs as spaces option in every text editor / DB tools, so you can still use tabs, but spaces will be inserted instead. 
- Adding extra whitespace for better readibility is fine, although not required

```sql
-- Good
SELECT
  CASE WHEN dep.department_name IN ('Finance', 'Accounting') THEN 1 ELSE 0 END AS fin_flag
  ,CASE WHEN dep.department_name = 'IT' THEN 1 ELSE 0 END                      AS it_flag
  
-- Also good
SELECT
   CASE WHEN dep.department_name IN ('Finance', 'Accounting') THEN 1 ELSE 0 END AS fin_flag
  ,CASE WHEN dep.department_name = 'IT'                       THEN 1 ELSE 0 END AS it_flag
```

# Aliasing

- Always use aliases with an explicit `AS` keyword.
  - In Oracle you can't use the `AS` keyword for aliasing table names in `FROM` and `JOIN` clauses. Instead use extra whitespace to make the aliases more noticable.
- Field name aliases and table aliases can be aligned together or separately

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
- For longer queries place the table name in a new row
- When using a single table in the query no alias is required, however in case of `JOIN`s always use an alias.
- Never use the FROM, WHERE type of joining.

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

-- Bad
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


```sql
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
- Always use aliases when `JOIN`ing
- Use meaningful table aliases

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
  employee    AS x
LEFT JOIN
  department  AS y
  ON x.department_number = y.department_number
;
```

- Prefer `LEFT JOIN` over `RIGHT JOIN` if possible

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

- Write `LEFT JOIN` instead of `LEFT OUTER JOIN`, and `RIGHT JOIN` instead of `RIGHT OUTER JOIN`

# CASE WHEN

- Short cases can be written to a single line
- Longer cases should be spanned to multiple lines:
  - `CASE` and `END` should be at the same indentation level
  - Every `WHEN` conditional should be written to new lines with one tab further.  

```sql
SELECT
  CASE WHEN employee_number > 5 THEN 'Greater than 5' ELSE 'Less than 5' END AS gr5_flag
  ,CASE
    WHEN employee_number > 10 THEN '10+'
    WHEN employee_number > 5 THEN '6-10'
    ELSE '0-5'
   END AS employee_no_bin
```
