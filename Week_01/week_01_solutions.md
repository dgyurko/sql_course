

# Soulutions of the exercises from the first week



- Exercise 1;
	-Please select the flight data from 2013.01.10.

```sql
SELECT * 
FROM flights.flights
WHERE
    YEAR = 2013
    AND MONTH = 1
    AND DAY = 10
;
```
	
- Exercise 2;
	-Please select the flights which departed with  delay.	

```sql
SELECT * 
FROM flights.flights
WHERE
    dep_deplay > 0
;
```
    
- Exercise 3;
	-Please select the flights which departed and arrived with  delay.

```sql
SELECT * 
FROM flights.flights
WHERE
    dep_deplay > 0
    AND arr_delay > 0
;
```
    
- Exercise 4;
	-Please select the flights which departed with delay but arrived early or arrived on time.	
	
```sql
SELECT * 
FROM flights.flights
WHERE
    dep_deplay > 0
    AND arr_delay <= 0
;
```

- Exercise 5;
	-Please find the flights which departed early or arrived early.

    
```sql
SELECT * 
FROM flights.flights
WHERE
    dep_deplay > 0
    OR arr_delay > 0
;
```


- Exercise 6;
	-Please select the flights where the scheduled arrival time was earlier than ten o'clock.	
    
```sql
SELECT * 
FROM flights.flights
WHERE
    sched_arr_time < 1000
;
```
 
- Exercise 7;
	-Please list the time of  arrival delay by airports.

```sql
SELECT 
origin, 
count(arr_delay)
FROM flights.flights
GROUP BY origin
;
```