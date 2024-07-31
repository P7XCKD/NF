
### Aim:
Implementation of Aggregate and Character Functions

### Theory:
Aggregative operators perform computations or summarizations in SQL, such as MIN and SUM.

1. **Count**: Returns the count of tuples in a column.
   - **Syntax**: `COUNT(Column name)`
   - **Example**: `SELECT COUNT(Sal) FROM emp;`

2. **SUM**: Returns the sum of all values in a column.
   - **Syntax**: `SUM(Column name)`
   - **Example**: `SELECT SUM(Sal) FROM emp;`

3. **AVG**: Returns the average value of a column.
   - **Syntax**: `AVG(Column name)`
   - **Example**: `SELECT AVG(Sal) FROM emp;`

4. **MAX**: Returns the maximum value of a column.
   - **Syntax**: `MAX(Column name)`
   - **Example**: `SELECT MAX(Sal) FROM emp;`
   - **Group By Example**: `SELECT deptno, MAX(sal) FROM emp GROUP BY deptno;`