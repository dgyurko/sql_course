# Exercises of the second week 

## Exercises about the schema "flights" 

* Number of delays according to their "origin" airports

```sql 
SELECT 
    origin
    ,count(arr_delay)
FROM flights.flights
WHERE 
    arr_delay > 0
GROUP BY origin
    ;
```
 
* How many airlines flights from their departure airport?

```sql 
SELECT 
    origin
    ,count(DISTINCT carrier)
FROM flights.flights
GROUP BY 1
;
```


## exercises about the schema "Bakery"
* How many different flavoures and bakery products could you buy in the bakery? 

```sql 
SELECT 
    COUNT(DISTINCT flavor) AS flavor_cnt
    ,COUNT(DISTINCT food)  AS food_cnt
FROM bakery.goods
;
```

* How much costs the cheapest and the most expensive food? 

```sql 
SELECT
    food
    ,min(price) AS cheapest
    ,max(price) AS most_expensive
FROM bakery.goods
GROUP BY 
    food
;
```

* According to the previous exercise, Csak azokat jelenítsd meg, ahol: 

	* 1. A min_price és max_price megegyezik, tehát nincs különbség a sütemény különböző ízei közt. 

	```sql
	HAVING 
   count(DISTINCT flavor) > 1 
    ;
	```
	* 2. Több mint 1 ízben kapható a sütemény

	```sql
	HAVING 
   count(DISTINCT flavor) > 1 
    ;
	```

* How much is the difference between the cheapest and the most expensive one?

```sql 
SELECT
    food
    ,max(price) - min(price) AS price_difference
FROM bakery.goods
GROUP BY 
    food
;
```
