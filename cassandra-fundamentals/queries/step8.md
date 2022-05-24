CQL aggregates include `COUNT`, `SUM`, `AVG`, `MIN` and `MAX`. CQL also 
supports many functions, of which we will showcase `CAST`, `NOW`, and `TODATE`. 
It is also possible to create user-defined aggregates and functions using 
statements `CREATE AGGREGATE` and `CREATE FUNCTION`. We will create a function to calculate 
the number of days between two dates. Study and execute the following query examples.

Q1. Analize ratings for the movie:
```
SELECT COUNT(rating) AS count,
       SUM(rating) AS sum,
       AVG(CAST(rating AS FLOAT)) AS avg,
       MIN(rating) AS min,
       MAX(rating) AS max
FROM   ratings_by_movie
WHERE  title = 'Alice in Wonderland'
  AND  year  = 2010;
```{{execute}}

Q2. Find the user name, date of joining and current date:
```
SELECT name, 
       date_joined, 
       TODATE(NOW()) AS date_today
FROM   users
WHERE  email = 'joe@datastax.com';
```{{execute}}

Q3. Calculate how many days passed since the user joined:
```
CREATE FUNCTION IF NOT EXISTS 
  DAYS_BETWEEN_DATES(date1 TEXT, date2 TEXT) 
RETURNS NULL ON NULL INPUT 
RETURNS BIGINT 
LANGUAGE Java AS 
'return java.lang.Math.abs(
   java.time.temporal.ChronoUnit.DAYS.between(
     java.time.LocalDate.parse(date1), 
     java.time.LocalDate.parse(date2)
   )
 );';

SELECT name, 
       DAYS_BETWEEN_DATES( 
         CAST(date_joined   AS TEXT), 
         CAST(TODATE(NOW()) AS TEXT) ) AS days
FROM   users
WHERE  email = 'joe@datastax.com';
```{{execute}}