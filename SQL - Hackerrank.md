## Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

> The LEFT() function extracts a number of characters from a string (starting from left).

> The UPPER() function converts a string to upper-case.

```sql
SELECT DISTINCT CITY FROM STATION WHERE UPPER(LEFT(CITY,1)) IN ("A","E","I","O","U")
```

<hr>
<hr>

## Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

> The RIGHT() function extracts a number of characters from a string (starting from right).

```sql
SELECT DISTINCT CITY FROM STATION WHERE UPPER(RIGHT(CITY,1)) IN ("A","E","I","O","U")
```

<hr>
<hr>

## Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY FROM STATION WHERE UPPER(LEFT(CITY,1)) IN ("A","E","I","O","U") AND UPPER(RIGHT(CITY,1)) IN ("A","E","I","O","U")
```

<hr>
<hr>

## Query the Name of any student in STUDENTS who scored higher than Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

> The ORDER BY keyword is used to sort the result-set in ascending or descending order.

> The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.

```sql
SELECT Name FROM STUDENTS WHERE Marks>75 ORDER BY RIGHT(Name,3),ID ASC
```

<hr>
<hr>

## Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with sides of equal length.  
Isosceles: It's a triangle with sides of equal length.  
Scalene: It's a triangle with sides of differing lengths.  
Not A Triangle: The given values of A, B, and C don't form a triangle.  

```sql
SELECT CASE
            WHEN A+B>C AND A+C>B AND B+C>A THEN 
                CASE WHEN A=B AND B=C THEN 'Equilateral'
                     WHEN A=B OR A=C OR B=C THEN 'Isosceles'
                     ELSE 'Scalene'
                END
            ELSE 'Not A Triangle'
        END
FROM TRIANGLES;
```

<hr>
<hr>

## Generate the following two result sets:

    Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).

    Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

    There are a total of [occupation_count] [occupation]s.

    where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

> The GROUP BY statement groups rows that have the same values into summary rows, like "find the number of customers in each country".

> The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

```sql
select concat (name, '(', left(occupation,1), ')')
from occupations
order by name;

select concat('There are a total of',' ',count(occupation),' ',lower(occupation),'s.') from occupations
group by occupation
order by count(occupation), occupation
```

<hr>
<hr>

## Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's 0 keywas broken
 until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.:
average monthly salaries), and round it up to the next integer.

> The REPLACE() function replaces all occurrences of a substring within a string, with a new substring. - (works for integers too)

```sql
SELECT CEIL(AVG(SALARY) - AVG(REPLACE(SALARY,0,''))) FROM EMPLOYEES
```

<hr>
<hr>

## We define an employee's total earnings = SALARY*MONTHS to be their monthly worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as space-separated integers.

> The AS command is used to rename a column or table with an alias.

```sql
select (months * salary) as income, count(employee_id) from employee group by income order by income desc limit 1
```

<hr>
<hr>

## Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically. 

```sql
SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY),CITY LIMIT 1;
SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY) DESC LIMIT 1
```

<hr>
<hr>

## Consider and to be two points on a 2D plane where are the respective minimum and maximum values of Northern Latitude (LAT_N) and are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION. Query the Euclidean Distance between points and and format your answer to display decimal digits.

```sql
SELECT ROUND(SQRT(POWER(MAX(LAT_N) - MIN(LAT_N),2) + POWER(MAX(LONG_W) - MIN(LONG_W),2)),4) FROM STATION
```

<hr>
<hr>

## Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

```sql
SELECT SUM(CITY.POPULATION) FROM CITY JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE WHERE COUNTRY.CONTINENT = "Asia"
```

<hr>
<hr>

## Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

```sql
SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION)) FROM CITY JOIN COUNTRY ON COUNTRY.CODE=CITY.COUNTRYCODE GROUP BY COUNTRY.CONTINENT
```

<hr>
<hr>


<br>

# Medium

## Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.

```sql
select Doctor, Professor, Singer, Actor from ( 
    select Name_Order, max(case Occupation when 'Doctor' then Name end) as Doctor, 
                       max(case Occupation when 'Professor' then Name end) as Professor,                            max(case Occupation when 'Singer' then Name end) as Singer, 
                       max(case Occupation when 'Actor' then Name end) as Actor from ( 
                           select Occupation, Name, row_number() over(
                               partition by Occupation order by Name ASC) 
                           as Name_Order from Occupations ) 
                           as Name_Lists group by Name_Order ) 
                           as Names
```

<hr>
<hr>