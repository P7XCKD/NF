## Experiment 5: Implementation of Aggregate and Character Functions

### Aim:
Implementation of Aggregate and Character Functions

### Theory:
Aggregative operators allow performing computations or summarizations on data retrieved from a database using SQL. Examples include MIN, MAX, SUM, AVG, and COUNT.

1. **Count**: Returns the count of tuples (row) in a column. Using `DISTINCT` returns only the count of unique tuples.
   - **Syntax**: `COUNT(Column name)`
   - **Example**: `SELECT COUNT(Sal) FROM emp;`

2. **SUM**: Returns the sum of all values in a column.
   - **Syntax**: `SUM(Column name)`
   - **Example**: `SELECT SUM(Sal) FROM emp;`

3. **AVG**: Returns the average value of a column's values.
   - **Syntax**: `AVG(Column name)`
   - **Example**: `SELECT AVG(Sal) FROM emp;`

4. **MAX**: Returns the maximum value of a column.
   - **Syntax**: `MAX(Column name)`
   - **Example**: `SELECT MAX(Sal) FROM emp;`
   - **Group By Example**: `SELECT deptno, MAX(sal) FROM emp GROUP BY deptno;`

| DEPTNO | MAX(SAL) |
|--------|----------|
| 10     | 5000     |
| 20     | 3000     |
| 30     | 2850     |

   - **Example**:
     ```sql
     SELECT deptno, MAX(sal) 
     FROM emp 
     GROUP BY deptno 
     HAVING MAX(sal) < 3000;
     ```
   - **Result**:
     | DEPTNO | MAX(SAL) |
     |--------|----------|
     | 30     | 2850     |

5. **MIN Function**:
   - **Usage**: Returns the minimum value of a column.
   - **Example**:
     ```sql
     SELECT deptno, MIN(sal) 
     FROM emp 
     GROUP BY deptno 
     HAVING MIN(sal) > 1000;
     ```
   - **Result**:
     | DEPTNO | MIN(SAL) |
     |--------|----------|
     | 10     | 1300     |

6. **Character Functions**:
   - **initcap(char)**: Capitalizes the first letter of each word.
     ```sql
     SELECT initcap('hello') FROM dual;
     ```
   - **lower(char)**: Converts all characters to lowercase.
     ```sql
     SELECT lower('HELLO') FROM dual;
     ```
   - **upper(char)**: Converts all characters to uppercase.
     ```sql
     SELECT upper('hello') FROM dual;
     ```
   - **ltrim(char, [set])**: Trims characters from the left.
     ```sql
     SELECT ltrim('cseit', 'cse') FROM dual;
     ```
   - **rtrim(char, [set])**: Trims characters from the right.
     ```sql
     SELECT rtrim('cseit', 'it') FROM dual;
     ```
   - **replace(char, search)**: Replaces occurrences of a substring.
     ```sql
     SELECT replace('jack and jue', 'j', 'bl') FROM dual;
     ```

     Conclusion:
  hence , we successfully performed Implementation of Aggregate and Character Functions