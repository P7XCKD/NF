## Experiment 5: Implementation of Aggregate and Character Functions

### Aim:
Implementation of Aggregate and Character Functions

### Theory:
Aggregative operators perform computations or summarizations on data using SQL. Examples include MIN, MAX, SUM, AVG, and COUNT.

1. **Count**: Returns the count of tuples (rows) in a column. Using `DISTINCT` returns only the count of unique tuples.
   - **Syntax**: `COUNT(Column name)`
   - **Example**: 
     ```sql
     SELECT COUNT(Sal) FROM emp;
     ```

2. **SUM**: Returns the sum of all values in a column.
   - **Syntax**: `SUM(Column name)`
   - **Example**: 
     ```sql
     SELECT SUM(Sal) FROM emp;
     ```

3. **AVG**: Returns the average value of a column's values.
   - **Syntax**: `AVG(Column name)`
   - **Example**: 
     ```sql
     SELECT AVG(Sal) FROM emp;
     ```

4. **MAX**: Returns the maximum value of a column.
   - **Syntax**: `MAX(Column name)`
   - **Example**: 
     ```sql
     SELECT MAX(Sal) FROM emp;
     ```
   - **Group By Example**: 
     ```sql
     SELECT deptno, MAX(sal) FROM emp GROUP BY deptno;
     ```

   - **Result**:
     | DEPTNO | MAX(SAL) |
     |--------|----------|
     | 10     | 5000     |
     | 20     | 3000     |
     | 30     | 2850     |

   - **Filtered Example**: 
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

5. **MIN**: Returns the minimum value of a column.
   - **Syntax**: `MIN(Column name)`
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

### Conclusion:
We successfully performed the implementation of aggregate and character functions.