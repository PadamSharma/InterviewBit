## Euclid's Distance
**medium**


Given a table HOUSES, find the euclidean distance between points with the largest X and Y coordinate, and the points with the smallest X and Y coordinate.

The Euclidean Distance between 2 points P(x1, y1) and Q(x2, y2) is defined as: sqrt((x1 - x2)2 + (y1 - y2)2).

```sql
SELECT sqrt(POW(MAX(XCoordinate)-MIN(XCoordinate),2)+POW(MAX(YCoordinate)-MIN(YCoordinate),2)) as "A" from HOUSES
```

## Big Salary
**medium**


Given a table WORKERS, find how many workers have the maximum total earnings among all the workers.

The total earnings of a worker is calculated as Daily Wage * Number of Days Worked.

```sql
SELECT count(ID) as "A" from WORKERS group by DailyWage * DaysWorked order by DailyWage * DaysWorked limit 1
```

## 5'th Highest Marks
**medium**

Given the ‘STUDENTS’ table. Write an SQL query to find the 5’th highest marks in the students table.

```sql
SELECT min(Marks) as MARKS from (SELECT Marks from STUDENTS order by Marks desc limit 5) as A
```

## 

```sql

```

## 

```sql

```

## 

```sql

```

## 

```sql

```

## 

```sql

```

## 

```sql

```

## 

```sql

```