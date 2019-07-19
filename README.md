# hackerrank_SQL
SQL Skills
Query all columns (attributes) for every row in the CITY table.
```
SELECT *
FROM CITY
```
--------------------------------------------------------------------------------------------
Query all columns for a city in CITY with the ID 1661.
```
SELECT *
FROM CITY
WHERE ID = 1661
```
--------------------------------------------------------------------------------------------
Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
```
SELECT *
FROM CITY
WHERE COUNTRYCODE  = "JPN"
```
--------------------------------------------------------------------------------------------
Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
```
SELECT NAME 
FROM CITY
WHERE COUNTRYCODE = "JPN"
```
--------------------------------------------------------------------------------------------
Query a list of CITY and STATE from the STATION table.
```
SELECT CITY, STATE
FROM STATION
```
--------------------------------------------------------------------------------------------
Query a list of CITY names from STATION with even ID numbers only. You may print the results in any order, but must exclude duplicates from your answer.
```
SELECT DISTINCT CITY
FROM STATION
WHERE (ID % 2) = 0
```
--------------------------------------------------------------------------------------------
Let N be the number of CITY entries in STATION, and let N'  be the number of distinct CITY names in STATION; query the value of N - N'  from STATION. In other words, find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
```
SELECT ( COUNT(CITY) - COUNT(DISTINCT CITY) ) 
FROM STATION
```
--------------------------------------------------------------------------------------------
Query all columns for all American cities in CITY with populations larger than 100000. The CountryCode for America is USA.
```
SELECT *
FROM CITY
WHERE COUNTRYCODE = "USA"
AND POPULATION > 100000
```
--------------------------------------------------------------------------------------------
Query the names of all American cities in CITY with populations larger than 120000. The CountryCode for America is USA.
```
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = "USA"
AND POPULATION > 120000
```
--------------------------------------------------------------------------------------------
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
```
SELECT TOP 1 CITY AS CITY_TOP, LEN(CITY) AS CITY_LEN
FROM STATION
ORDER BY CITY_LEN ASC, CITY_TOP ASC 

SELECT TOP 1 CITY AS CITY_TOP, LEN(CITY) AS CITY_LEN
FROM STATION
ORDER BY CITY_LEN DESC, CITY_TOP DESC 
```
--------------------------------------------------------------------------------------------

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE "a%"
OR CITY LIKE "e%"
OR CITY LIKE "i%"
OR CITY LIKE "o%"
OR CITY LIKE "u%"
```
--------------------------------------------------------------------------------------------
Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE "%a"
OR CITY LIKE "%e"
OR CITY LIKE "%i"
OR CITY LIKE "%o"
OR CITY LIKE "%u"
```
--------------------------------------------------------------------------------------------
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY
FROM STATION
WHERE LEFT(CITY,1) in ("a", "e", "i", "o", "u")
AND RIGHT(CITY,1) in ("a", "e", "i", "o", "u")
```
--------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY
FROM STATION
WHERE LEFT(CITY, 1) NOT IN ("a", "e", "i", "o", "u")
```
--------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY
FROM STATION
WHERE RIGHT(CITY, 1) NOT IN ("a", "e", "i", "o", "u")
```
--------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY 
FROM STATION
WHERE LEFT(CITY,1) NOT IN ("a", "e", "i", "o", "u")
OR RIGHT(CITY,1) NOT IN ("a", "e", "i", "o", "u")
```
--------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```
SELECT DISTINCT CITY 
FROM STATION
WHERE LEFT(CITY,1) NOT IN ("a", "e", "i", "o", "u")
AND RIGHT(CITY,1) NOT IN ("a", "e", "i", "o", "u")
```
--------------------------------------------------------------------------------------------
Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
```
SELECT NAME 
FROM STUDENTS 
WHERE MARKS > 75 
ORDER BY RIGHT(NAME, 3), ID ASC;
```
--------------------------------------------------------------------------------------------
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.
```
SELECT name
FROM Employee 
ORDER BY name
```
--------------------------------------------------------------------------------------------
Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than 2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.
```
SELECT name
FROM Employee
WHERE salary > 2000
    AND months < 10
ORDER BY employee_id ASC
```
--------------------------------------------------------------------------------------------
Query a count of the number of cities in CITY having a Population larger than 100000.
```
SELECT COUNT(*)
FROM CITY
WHERE POPULATION > 100000
```
--------------------------------------------------------------------------------------------
Query the total population of all cities in CITY where District is California.
```
SELECT SUM(POPULATION)
FROM CITY
WHERE DISTRICT = "California"
```
--------------------------------------------------------------------------------------------
Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.
```
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE  = "JPN"
```
--------------------------------------------------------------------------------------------
Query the difference between the maximum and minimum populations in CITY.
```
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY
```
--------------------------------------------------------------------------------------------
Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.
```
SELECT SUM(CITY.POPULATION)
FROM CITY 
INNER JOIN COUNTRY 
    ON CITY.COUNTRYCODE = COUNTRY.CODE
WHERE CONTINENT = "Asia"
```
--------------------------------------------------------------------------------------------
Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.
```
SELECT CITY.NAME
FROM CITY
INNER JOIN COUNTRY 
    ON CITY.COUNTRYCODE = COUNTRY.CODE
WHERE CONTINENT = "Africa"
```
--------------------------------------------------------------------------------------------
Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:
Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.
```
SELECT CASE WHEN A + B > C AND A+C>B AND B+C>A THEN CASE 
WHEN A = B AND B = C THEN 'Equilateral' 
WHEN A = B OR B = C OR A = C THEN 'Isosceles' 
WHEN A != B OR B != C OR A != C THEN 'Scalene' END 
ELSE 'Not A Triangle' END 
FROM TRIANGLES;
```
--------------------------------------------------------------------------------------------
Query the average population for all cities in CITY, rounded down to the nearest integer.
```
SELECT FLOOR(AVG(POPULATION)) 
FROM CITY
```
--------------------------------------------------------------------------------------------
Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.
```
SELECT COUNTRY.Continent, FLOOR(AVG(CITY.Population))
FROM CITY INNER JOIN COUNTRY 
    ON CITY.CountryCode = COUNTRY.Code
GROUP BY COUNTRY.Continent
```   
--------------------------------------------------------------------------------------------
P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

* * * * * 
* * * * 
* * * 
* * 
*
Write a query to print the pattern P(20).
```
DECLARE @i INT = 20

WHILE (@i > 0) 
BEGIN
   PRINT REPLICATE('* ', @i) 
   SET @i = @i - 1
END
```
--------------------------------------------------------------------------------------------
Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeroes removed), and the actual average salary.
Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer
```
SELECT CAST(CEILING(AVG(CAST(SALARY as float)) - AVG(CAST(REPLACE(SALARY, '0', '') as float))) as int )
FROM EMPLOYEES                                                                            
```
--------------------------------------------------------------------------------------------
Query the following two values from the STATION table:
The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.
```
SELECT CAST(ROUND(SUM(LAT_N),2) as decimal (10,2)), CAST(ROUND(SUM(LONG_W),2) as decimal (10,2)) FROM station;
```
--------------------------------------------------------------------------------------------
P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):
*
* * 
* * * 
* * * * 
* * * * *
Write a query to print the pattern P(20).
```
DECLARE @i INT = 0

WHILE (@i < 21) 
BEGIN
   PRINT REPLICATE('* ', @i) 
   SET @i = @i + 1
END
```
--------------------------------------------------------------------------------------------
Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than  and less than . Truncate your answer to  decimal places.
```
SELECT CAST(SUM(LAT_N) AS DECIMAL(10,4))
FROM STATION
WHERE LAT_N > 38.7880
    AND LAT_N < 137.2345
 ```   
--------------------------------------------------------------------------------------------
Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than . Truncate your answer to  decimal places.
```
SELECT CAST(MAX(LAT_N) AS DECIMAL (10,4))
FROM STATION
WHERE LAT_N < 137.2345              
```
--------------------------------------------------------------------------------------------
Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.
```
SELECT CAST(LONG_W AS DECIMAL(10,4))
FROM STATION
WHERE LAT_N = 
    (
        SELECT MAX(LAT_N)
        FROM STATION
        WHERE LAT_N < 137.2345
    )
```
--------------------------------------------------------------------------------------------
Query the smallest Northern Latitude (LAT_N) from STATION that is greater than . Round your answer to  decimal places.
```
SELECT CAST(MIN(LAT_N) AS decimal(10,4))
FROM STATION
WHERE LAT_N > 38.7780
```
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------
