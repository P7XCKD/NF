### Experiment 9: Implementation of Views

**Aim:** 
Implementation of views

### Theory

#### VIEW
- **Definition:** A view is a virtual table based on the result-set of an SQL statement. It contains rows and columns, similar to a real table. Fields in a view come from one or more real tables.
- **Functionality:** You can add SQL functions, `WHERE`, and `JOIN` statements to a view and present data as if it were coming from a single table.
- **Characteristics:** A view is a query stored as an object, consisting of columns from one or more tables, but it does not store data itself in the database.

**Syntax:**
```sql
CREATE VIEW <view_name> AS 
SELECT <set of fields> 
FROM relation_name 
WHERE (Condition);
```
- **Example 1:**
  ```sql
  CREATE VIEW employee AS 
  SELECT empno, ename, job 
  FROM EMP 
  WHERE job = 'clerk';
  ```
  Result: `View created.`
***

- **Example 2:**
  ```sql
  CREATE VIEW [Current Product List] AS
  SELECT ProductID, ProductName
  FROM Products
  WHERE Discontinued = No;
  ```
***

#### UPDATING A VIEW
- **Definition:** A view can be updated using the `CREATE OR REPLACE VIEW` command.
- **Syntax:**
  ```sql
  CREATE OR REPLACE VIEW view_name AS
  SELECT column_name(s)
  FROM table_name
  WHERE condition;
  ```
***

#### DROPPING A VIEW
- **Syntax:**
  ```sql
  DROP VIEW <view_name>;
  ```
***

conclusion: hence we successfully implemented views