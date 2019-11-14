# Week 5: Regex Excersises

## 1. Select different letters of the origin column:
```sql 
SELECT
    LEFT(origin, 1)                 AS first_letter
    ,SUBSTRING(origin FROM 2 FOR 1) AS second_letter
    ,RIGHT(origin, 1)               AS third_letter
FROM flights.flights;
```
## 2. Concatenate two columns with different functions:
```sql 
SELECT 
    firstname
    ,lastname
    ,firstname || ' ' || lastname               AS full_name
    ,CONCAT(firstname, ' ', lastname)           AS full_name2
    ,LOWER(CONCAT(firstname, ' ', lastname))    AS full_name3
    ,INITCAP(CONCAT(firstname, ' ', lastname))  AS full_name4
FROM bakery.customers;
```
## 3. The simplest regex is the LIKE 1. :
```sql
--With LIKE:
SELECT * 
FROM bakery.customers
WHERE lastname LIKE 'L%'; --CASE SENSITIVE

--With ILIKE:
SELECT * 
FROM bakery.customers
WHERE lastname ILIKE 'e%a'; -- CASE INSENSITIVE
```
## 4. Using Regex in WHERE condition similar to LIKE:
```sql
-- Lastname starts with 'L':
SELECT * 
FROM bakery.customers
WHERE
	    lastname ~ '^L';

-- Lastname ends with 'L':
SELECT * 
FROM bakery.customers
WHERE
    lastname ~ 'L$';
```    
## 5. Select every record where the lastname starts with 'L' and ends with 'A':  
```sql
SELECT *
FROM bakery.customers
WHERE lastname ~ '^E.+A$'; 
```
## 6. Select every record where there are two 'S' in the lastname:
```sql
SELECT *
FROM bakery.customers
WHERE lastname ~ 'SS';
```
## 7. Define the results:
```sql
SELECT 
    LEFT('7-5 4-6 7-5 (12-10)', 3)							
    ,regexp_matches('7-5 4-6 7-5 (12-10)', '^.-.')
    ,regexp_matches('7-5 4-6 7-5 (12-10)', '^[0-7]-[0-7]');
```
## 8. Select all first name that contains 'Phil':
```sql
SELECT first_name
FROM regex.personal_data
WHERE first_name LIKE '%Phil%';
```
## 9. Create address, provider and domain variable from email column with regex:
```sql
SELECT 
    email
    ,array_to_string(regexp_matches(email, '^.+(?=@)'), ';')            AS adress
    ,array_to_string(regexp_matches(email, '(?<=\@)(.*?)(?=\.)'), ';')  AS provider
    ,array_to_string(regexp_matches(email, '(?<=@.+?\.)(.+)'), ';')     AS "domain"
FROM  regex.personal_data;
```
## 10. Create 'is_hu_num' flag from phone_num variable, which gives back 1 if the phone number contains '06' or '+36'. In any other cases the value should be 0.
```sql
SELECT
    phone_num
    ,COALESCE(phone_num ~ '^((06)|(\+36))', FALSE) AS is_hun_flag_boolean
    ,CASE
        WHEN phone_num ~ '^((06)|(\+36))' THEN 1
        ELSE 0
     END AS is_hun_flag
FROM  regex.personal_data;
```
## 11. Create same format for all the phone numbers:
```sql
SELECT
    phone_num
    ,REPLACE(
        REPLACE(phone_num, '-', ''),
        ' ',
        ''
        ) AS with_replace
        , regexp_replace(phone_num, '\D', '', 'g') 
FROM  regex.personal_data;
```

## 11. Select phone_password records which contain characters, than count it.
```sql
SELECT 
    phone_password
    ,phone_password ~ '[a-zA-Z]'
FROM regex.personal_data;

SELECT 
    SUM(CASE WHEN phone_password ~ '[a-zA-Z]' THEN 1 ELSE 0 END) AS cnt
FROM regex.personal_data;
```
