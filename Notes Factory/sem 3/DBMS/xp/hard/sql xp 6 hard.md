### AIM

Perform Simple Queries and Complex Queries using SQL.

### OBJECTIVE

-   To understand the use of Structured Query Language (SQL).
    
-   To understand various ways to retrieve data using SELECT commands and clauses.
    
-   To perform simple queries using different comparison and logical operators.
    
-   To use clauses such as LIKE, IN, BETWEEN, ORDER BY, DISTINCT and GROUP BY.
    
-   To perform aggregate operations using COUNT(), AVG() and MAX().
    
-   To use the HAVING clause with grouped data.
    
-   To perform complex queries using multiple SQL clauses.
    

### SOFTWARE REQUIREMENT

MySQL Server 8.0  
MySQL Shell 8.0

### THEORY

Structured Query Language (SQL) is used to store, retrieve and manipulate data in a database. The `SELECT` command retrieves records from tables.

Common SELECT clauses and operators include:

-   **WHERE** – Filters records based on a condition.
    
-   **LIKE / NOT LIKE** – Performs pattern matching.
    
-   **AND / OR / NOT / XOR** – Combines conditions.
    
-   **IN / NOT IN** – Checks values from a set.
    
-   **BETWEEN / NOT BETWEEN** – Checks values within a range.
    
-   **IS NULL / IS NOT NULL** – Checks NULL values.
    
-   **ORDER BY** – Sorts records.
    
-   **DISTINCT** – Displays unique values.
    
-   **GROUP BY** – Groups records.
    
-   **HAVING** – Filters grouped records.
    
-   **COUNT(), AVG(), MAX()** – Perform aggregate calculations.
    

### GROUP 1 — CREATING AND POPULATING THE TABLE

The table is created to store climate-related records and is populated with sample data.

#### Syntax

```sql
CREATE TABLE table_name
(
    column_name datatype constraint,
    column_name datatype constraint
);

INSERT INTO table_name
VALUES (value1, value2, value3);
```

### GROUP 2 — SELECT QUERIES USING DIFFERENT OPERATORS

#### Comparison Operators

Comparison operators are used to compare column values with specified values.

##### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name operator value;
```

### GROUP 3 — STRING PATTERN MATCHING

`LIKE` and `NOT LIKE` are used to find records matching or not matching a specified pattern.

#### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name LIKE 'pattern';

SELECT *
FROM table_name
WHERE column_name NOT LIKE 'pattern';
```

### GROUP 4 — ARITHMETIC OPERATORS

Arithmetic operators are used to perform calculations on numeric column values.

#### Syntax

```sql
SELECT column_name + value
FROM table_name;

SELECT column_name - value
FROM table_name;
```

### GROUP 5 — LOGICAL OPERATORS

Logical operators are used to combine or modify conditions.

#### AND

```sql
SELECT *
FROM table_name
WHERE condition1
AND condition2;
```

#### OR

```sql
SELECT *
FROM table_name
WHERE condition1
OR condition2;
```

#### NOT

```sql
SELECT *
FROM table_name
WHERE NOT condition;
```

#### XOR

```sql
SELECT *
FROM table_name
WHERE condition1
XOR condition2;
```

### GROUP 6 — IN AND NOT IN

`IN` checks whether a value belongs to a given set, while `NOT IN` excludes those values.

#### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name IN (value1, value2);

SELECT *
FROM table_name
WHERE column_name NOT IN (value1, value2);
```

### GROUP 7 — BETWEEN AND NOT BETWEEN

`BETWEEN` checks values within a specified range, while `NOT BETWEEN` checks values outside the range.

#### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name BETWEEN value1 AND value2;

SELECT *
FROM table_name
WHERE column_name NOT BETWEEN value1 AND value2;
```

### GROUP 8 — IS NULL AND IS NOT NULL

These operators are used to check whether a column contains NULL or non-NULL values.

#### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name IS NULL;

SELECT *
FROM table_name
WHERE column_name IS NOT NULL;
```

### GROUP 9 — ORDER BY

`ORDER BY` is used to arrange query results in ascending or descending order.

#### Syntax

```sql
SELECT *
FROM table_name
ORDER BY column_name ASC;

SELECT *
FROM table_name
ORDER BY column_name DESC;
```

### GROUP 10 — DISTINCT

`DISTINCT` is used to display only unique values or unique combinations.

#### Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;

SELECT DISTINCT column1, column2
FROM table_name;
```

### GROUP 11 — GROUP BY

`GROUP BY` groups records based on a column and is commonly used with aggregate functions.

#### Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

### GROUP 12 — HAVING

`HAVING` is used to apply conditions to grouped records.

#### Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING aggregate_function(column_name) operator value;
```

### GROUP 13 — COMBINED QUERY

A combined query uses multiple clauses such as `GROUP BY`, `HAVING` and `ORDER BY` together.

#### Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition
ORDER BY column_name DESC;
```

### OUTCOME

Simple and complex SQL queries were successfully performed using different operators, clauses and aggregate functions.

### CONCLUSION

Thus, SQL queries were successfully implemented to retrieve, filter, sort and group climate-related data.