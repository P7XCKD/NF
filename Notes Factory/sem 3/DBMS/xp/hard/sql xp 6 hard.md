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
> [!abstract] 6B
### GROUP 1 — INNER JOIN

`INNER JOIN` displays records that have matching values in both tables.

#### Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### GROUP 2 — LEFT JOIN

`LEFT JOIN` displays all records from the left table and matching records from the right table. Unmatched records contain NULL values.

#### Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### GROUP 3 — RIGHT JOIN

`RIGHT JOIN` displays all records from the right table and matching records from the left table. Unmatched records contain NULL values.

#### Syntax

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

### GROUP 4 — FULL OUTER JOIN

`FULL OUTER JOIN` displays all matching and unmatched records from both tables.

#### Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column

UNION

SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

### GROUP 5 — CROSS JOIN

`CROSS JOIN` generates all possible combinations of records from two tables.

#### Syntax

```sql
SELECT columns
FROM table1
CROSS JOIN table2;
```

### GROUP 6 — SELF JOIN

`SELF JOIN` joins a table with itself to compare records within the same table.

#### Syntax

```sql
SELECT columns
FROM table1 A
JOIN table1 B
ON A.column = B.column
WHERE A.column > B.column;
```

### GROUP 7 — JOIN BETWEEN THREE TABLES

A three-table join combines related records from three tables using matching columns.

#### Syntax

```sql
SELECT columns
FROM table1
JOIN table2
ON table1.column = table2.column
JOIN table3
ON table2.column = table3.column;
```

### GROUP 8 — NESTED QUERY USING SELECT

A nested query uses one query inside another query to retrieve records based on the result of the inner query.

#### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name > (
    SELECT AVG(column_name)
    FROM table_name
);
```

### GROUP 9 — NESTED QUERY USING IN

`IN` checks whether a value matches any value returned by the nested query.

#### Syntax

```sql
SELECT columns
FROM table1
WHERE column_name IN (
    SELECT column_name
    FROM table2
);
```

### GROUP 10 — INSERT WITH SELECT

`INSERT WITH SELECT` inserts records returned by a SELECT query into another table.

#### Syntax

```sql
INSERT INTO new_table
SELECT *
FROM table_name
WHERE column_name > (
    SELECT AVG(column_name)
    FROM table_name
);
```

### GROUP 11 — UPDATE WITH SELECT

`UPDATE WITH SELECT` modifies records based on conditions returned by a nested query.

#### Syntax

```sql
UPDATE table_name
SET column_name = 'new_value'
WHERE column_name IN (
    SELECT column_name
    FROM another_table
    WHERE condition
);
```

### GROUP 12 — DELETE WITH SELECT

`DELETE WITH SELECT` deletes records based on conditions returned by a nested query.

#### Syntax

```sql
DELETE FROM table_name
WHERE column_name NOT IN (
    SELECT column_name
    FROM another_table
);
```

### OUTCOME

Various SQL joins and nested queries were successfully implemented to retrieve, compare, insert, update, and delete climate-related records.

### CONCLUSION

Thus, SQL joins and nested queries were successfully implemented for heatwave monitoring, prediction, and early warning. Different joins were used to combine related tables, while nested queries were used to filter records and perform data manipulation operations.
