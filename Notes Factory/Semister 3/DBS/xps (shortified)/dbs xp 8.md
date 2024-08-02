### Experiment 8: Inner Join, Outer Join & Natural Join

**Aim:** 
To implement different types of joins

### Theory

The SQL Joins clause is used to combine records from two or more tables in a database. A JOIN is a means for combining fields from two tables by using values common to each. The join is performed by the `WHERE` clause which combines specified rows of tables.

**Syntax:**
```sql
SELECT column1, column2, column3...
FROM table_name1, table_name2
WHERE table_name1.column_name = table_name2.column_name;
```

#### Types of Joins:
1. Simple Join
2. Self Join
3. Outer Join
***

#### Simple Join
It retrieves rows from 2 tables having a common column and is further classified into:

- **Equi-Join:** 
  - **Definition:** A join based on equalities.
  - **Example:**
    ```sql
    SELECT * FROM item, cust WHERE item.id = cust.id;
    ```
***

- **Non Equi-Join:**
  - **Definition:** Specifies the relationship between columns using relational operators other than `=`.
  - **Example:**
    ```sql
    SELECT * FROM item, cust WHERE item.id < cust.id;
    ```
***

#### Table Aliases
Table aliases are used to make multiple table queries shorter and more readable by giving an alias name to the table in the `FROM` clause and using it throughout the query.
***

#### Self Join
Joining of a table to itself is known as self-join. It compares each row of the table to itself and with other rows of the same table.
- **Example:**
  ```sql
  SELECT * FROM emp x, emp y WHERE x.salary >= (SELECT AVG(salary) FROM emp WHERE emp.deptno = y.deptno);
  ```
***

#### Outer Join
An outer join returns all the rows returned by a simple join as well as those rows from one table that do not match any row from the other table. The symbol `+` represents an outer join.

- **Types:**
  - **Left Outer Join**
  - **Right Outer Join**
  - **Full Outer Join**
***