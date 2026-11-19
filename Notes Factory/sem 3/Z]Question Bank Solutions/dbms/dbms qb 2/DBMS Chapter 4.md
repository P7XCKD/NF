# DBMS — CHAPTER 4 NOTES
## Structured Query Language (SQL)

> [!warning] HOW TO STUDY THIS CHAPTER
> You already know basic SQL from diploma, so this is mostly revision. The areas that deserve extra attention are **constraints, transaction commands, and writing correct queries**.
>
> Don't just read the queries and nod like the database accepted your assignment. Type or write them yourself.

---

# 1. Overview of SQL

**SQL (Structured Query Language)** is the standard language used to communicate with a relational database.

It is used to:
- Create and modify database structures.
- Insert, update, delete and retrieve data.
- Control user permissions.
- Manage transactions.

SQL is largely **non-procedural**: you state *what result you want*, and the DBMS works out how to retrieve it.

Example:

```sql
SELECT name
FROM Student
WHERE marks > 75;
```

You ask for students scoring above 75. SQL handles the search steps.

> [!hint] Memory trick
> **SQL = tell the database WHAT you want, not every step of HOW to find it.**

> [!attention] AI
> SQL is non-procedural. You don't need to explain to the database how to walk to the table, open the drawer, and pick up a row. It has one job. Let it work.

## 1.1 Types of SQL Commands

| Type | Purpose | Commands |
|---|---|---|
| DDL | Define database structure | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME` |
| DML | Manipulate/retrieve data | `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `MERGE` |
| DCL | Control permissions | `GRANT`, `REVOKE` |
| TCL | Control transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

> [!hint] Memory trick
> **DDL = Design, DML = Data, DCL = Control access, TCL = Transaction control.**

> [!note] Exam tip
> The PPT groups `SELECT` under DML. Use the classification taught in class for your exam. Some references separate it as DQL.

---

# 2. Data Definition Language (DDL)

DDL commands create or modify database objects such as tables and views.

## 2.1 `CREATE`

Creates a new database object.

```sql
CREATE TABLE Employee (
    Eid INT,
    Name VARCHAR(20),
    Age INT,
    Address CHAR(25),
    Salary DECIMAL(10,2)
);
```

- `Employee` is the table name.
- `Eid`, `Name`, etc. are columns.
- `INT`, `VARCHAR`, `CHAR` and `DECIMAL` define the data types.

## 2.2 `DESC` / `DESCRIBE`

Displays the structure of a table.

```sql
DESC Employee;
-- or
DESCRIBE Employee;
```

It displays column names, data types and related details supported by the DBMS.

## 2.3 `ALTER`

Changes the structure of an existing object.

**Add a column:**

```sql
ALTER TABLE Employee
ADD phone VARCHAR(10);
```

**Modify a column** *(syntax varies by DBMS)*:

```sql
ALTER TABLE Employee
MODIFY Name VARCHAR(40);
```

**Drop a column:**

```sql
ALTER TABLE Employee
DROP COLUMN phone;
```

## 2.4 `TRUNCATE`

Removes all rows but keeps the table structure.

```sql
TRUNCATE TABLE Employee;
```

## 2.5 `DROP`

Removes the table and its structure.

```sql
DROP TABLE Employee;
```

## 2.6 `RENAME`

Renames a database object. Syntax depends on the DBMS.

```sql
ALTER TABLE Employee
RENAME TO Staff;
```

## DDL — Quick comparison

| Command | What happens? |
|---|---|
| `CREATE` | Creates an object |
| `ALTER` | Changes structure |
| `TRUNCATE` | Removes all rows; keeps structure |
| `DROP` | Removes the object itself |
| `RENAME` | Changes object name |

> [!danger] Common exam trap
> **DELETE removes rows. TRUNCATE empties the table. DROP removes the table.**
>
> If the question asks to keep the table but remove its data, do not choose `DROP`. That is like deleting the entire notebook because you wanted to erase one page.

> [!hint] Memory trick
> **TRUNCATE = table stays, tuples go. DROP = table goes too.**



---

# 3. Data Manipulation Language (DML)

Use this example table throughout:

```text
CUSTOMERS(customer_id, first_name, last_name, age, country)
```

## 3.1 `INSERT`

Adds new rows.

```sql
INSERT INTO Customers
    (customer_id, first_name, last_name, age, country)
VALUES
    (5, 'Harry', 'Potter', 31, 'USA');
```

Insert multiple rows:

```sql
INSERT INTO Customers
    (customer_id, first_name, last_name, age, country)
VALUES
    (6, 'Chris', 'Evans', 42, 'USA'),
    (7, 'Tom', 'Holland', 26, 'UK');
```

If you omit the column list, the values must follow the table's column order. If a column is omitted from a named column list, its default is used, or `NULL` if allowed.

## 3.2 `UPDATE`

Modifies existing rows.

```sql
UPDATE Customers
SET country = 'India'
WHERE customer_id = 5;
```

Update multiple columns:

```sql
UPDATE Customers
SET first_name = 'Johnny',
    last_name = 'Depp'
WHERE customer_id = 5;
```

> [!danger] DO NOT FORGET WHERE
> Without `WHERE`, the update affects **every row**.
>
> One missing line can turn “fix Harry's record” into “change the entire database.” A very efficient way to become unpopular.

## 3.3 `DELETE`

Removes rows.

```sql
DELETE FROM Customers
WHERE customer_id = 5;
```

Delete every row but keep the table:

```sql
DELETE FROM Customers;
```

## 3.4 `SELECT`

Retrieves data without changing the stored rows.

```sql
SELECT first_name, last_name
FROM Customers;
```

Display all columns:

```sql
SELECT *
FROM Customers;
```

Filter rows with `WHERE`:

```sql
SELECT *
FROM Customers
WHERE last_name = 'Doe';
```

> [!hint] Memory trick
> **INSERT = add, UPDATE = edit, DELETE = remove, SELECT = view.**
>
> Before running `UPDATE` or `DELETE`, ask: **“Which rows?”** If your query has no `WHERE`, double-check that you really mean all rows.

---

# 4. Data Control Language (DCL)

DCL controls which operations a user is allowed to perform.

A **privilege** is permission to perform a particular action on the database or one of its objects.

## 4.1 Types of privileges

| Privilege type | Meaning | Example |
|---|---|---|
| System | Permission for a system-level action | Create a user or table, depending on DBMS |
| Object | Permission on a particular object | `SELECT` from `Employee` |
| Ownership | Privileges held by the object's owner | Owner grants access to others |

## 4.2 `GRANT`

Gives privileges to a user.

```sql
GRANT SELECT, INSERT
ON Employee
TO user1;
```

`WITH GRANT OPTION`, where supported, allows the user to pass the granted privilege to another user.

```sql
GRANT SELECT
ON Employee
TO user1
WITH GRANT OPTION;
```

## 4.3 `REVOKE`

Removes previously granted privileges.

```sql
REVOKE INSERT
ON Employee
FROM user1;
```

- `CASCADE`, where supported, may also remove dependent grants.
- `RESTRICT`, where supported, prevents revocation if dependent grants exist.

Exact syntax and behaviour depend on the DBMS.

> [!hint] Memory trick
> **GRANT gives. REVOKE removes.**
>
> Think of database access like keys to a lab: the admin decides who gets a key and who has to return it.

> [!attention] AI
> Never grant everyone full database access just because they asked nicely. “Bro trust me” is not a security policy.

---

# 5. Transaction Control Language (TCL)

A **transaction** is a logical unit of database work. Transaction commands help decide whether changes should be saved or undone.

## 5.1 `COMMIT`

Makes the transaction's changes permanent.

```sql
UPDATE Customers
SET country = 'India'
WHERE customer_id = 5;

COMMIT;
```

## 5.2 `ROLLBACK`

Undoes changes that have not been committed, subject to DBMS rules.

```sql
DELETE FROM Customers
WHERE customer_id = 5;

ROLLBACK;
```

After a successful commit, a normal rollback cannot undo those committed changes.

## 5.3 `SAVEPOINT`

Creates a marker inside a transaction so you can roll back only part of the work.

```sql
SAVEPOINT sp1;

DELETE FROM Customers
WHERE customer_id = 1;

SAVEPOINT sp2;

DELETE FROM Customers
WHERE customer_id = 2;

ROLLBACK TO sp2;
```

The rollback to `sp2` undoes work performed **after** `sp2`. The deletion before `sp2` remains pending in the transaction.

> [!hint] Memory trick
> **COMMIT = save. ROLLBACK = undo. SAVEPOINT = checkpoint.**

> [!attention] AI
> `SAVEPOINT` is Ctrl+S for a section of your transaction. It is not a time machine: once you commit, you cannot casually roll back to yesterday.

> [!hint] click the below link for more info
> [TCL - Transaction Control Language - GeeksforGeeks](https://www.geeksforgeeks.org/sql/tcl-full-form/)

---

# 6. SQL Query Exercises

These examples use the schemas shown in the PPT.

## Exercise 1 — Change Jack's city

Given:

```text
EMPLOYEE(e_id, name, street, city)
```

**Question:** Change Jack's city to New York.

```sql
UPDATE EMPLOYEE
SET city = 'New York'
WHERE name = 'Jack';
```

The `WHERE` clause ensures only matching rows are updated. If several employees are named Jack, each matching row will be updated.

## Exercise 2 — Give ANZ Corporation employees a 10% raise

Given:

```text
WORKS(eid, cid, salary)
COMPANY(cid, company_name, city)
```

```sql
UPDATE WORKS
SET salary = salary * 1.10
WHERE cid IN (
    SELECT cid
    FROM COMPANY
    WHERE company_name = 'ANZ Corporation'
);
```

The inner query finds the company's ID. The outer query increases the salary of employees associated with that company.

**Calculation:** A salary of ₹20,000 becomes ₹22,000 because \(20,000 \times 1.10 = 22,000\).

## Exercise 3 — Update accident damage

Given:

```text
PARTICIPATED(driver_id, car, report_number, damage_amount)
```

**Question:** Set damage to ₹5,000 for car `Mum2022` in accident `AR2197`.

```sql
UPDATE PARTICIPATED
SET damage_amount = 5000
WHERE report_number = 'AR2197'
  AND car = 'Mum2022';
```

Both conditions must match. `=` is suitable for exact identifiers; `LIKE` is mainly useful for patterns such as `'AR%'`.

---

# 7. Integrity Constraints

An **integrity constraint** is a rule that prevents invalid data from being stored and helps maintain database consistency.

The main types of integrity constraints are:

1. **D**omain Integrity
2. **E**ntity Integrity
3. **E**nterprise/Business Constraints
4. **R**eferential Integrity

> [!hint] Memory trick
> **DEER  — Domain, Entity, Enterprise, Referential**
>
> - **D**omain → Valid values
> - **E**ntity → Valid identity
> - **E**nterprise → Valid business rules
> - **R**eferential → Valid references
>
> Remember: A **DEER** needs valid values, a unique identity, rules to follow, and valid connections!

## 7.1 Domain Integrity

A **domain** is the set of valid values allowed for an attribute. Datatypes and constraints restrict what can be entered.

### A. Datatype

```sql
CREATE TABLE Employee (
    emp_id INT,
    name VARCHAR(30),
    salary DECIMAL(10,2)
);
```

`emp_id` is intended for integer values, while `name` stores character data and `salary` stores decimal values.

### B. `NOT NULL`

Prevents a column from storing `NULL`.

```sql
CREATE TABLE Student (
    roll_no INT NOT NULL,
    name VARCHAR(30) NOT NULL
);
```

A student row must have a roll number and name.

### C. `UNIQUE`

Prevents duplicate values in the constrained column or column combination.

```sql
CREATE TABLE Employee (
    emp_id INT UNIQUE,
    name VARCHAR(30)
);
```

Two employees cannot share the same non-NULL `emp_id`. Handling of `NULL` under `UNIQUE` can vary between DBMSs.

### D. `DEFAULT`

Supplies a value when an insert does not provide one for that column.

```sql
CREATE TABLE Student (
    roll_no INT,
    name VARCHAR(30),
    fees DECIMAL(8,2) DEFAULT 10000
);
```

If `fees` is omitted, the default is ₹10,000. Explicitly inserting `NULL` generally does not trigger the default.

### E. `CHECK`

Enforces a condition on a value.

```sql
CREATE TABLE Student (
    roll_no INT UNIQUE,
    name VARCHAR(25),
    age INT CHECK (age BETWEEN 15 AND 20)
);
```

The age must be between 15 and 20 when the constraint is enforced. Add `NOT NULL` if age must never be missing.

> [!hint] Memory trick
> **NOT NULL = must exist. UNIQUE = no duplicates. DEFAULT = fallback. CHECK = rule.**
>
> The database is the strict bouncer: “Name on the list? Age allowed? Duplicate entry? No entry.”

## 7.2 Entity Integrity — Primary Key

A **primary key** uniquely identifies each row and cannot contain `NULL` or duplicate values.

```sql
CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30),
    salary DECIMAL(10,2)
);
```

A primary key may consist of one column or multiple columns (a **composite primary key**).

> [!hint] Memory trick
> **Primary key = the row's official ID card.** Two rows cannot have the same ID, and the ID cannot be missing.

## 7.3 Referential Integrity — Foreign Key

A **foreign key** in one table refers to a primary or other eligible key in another table. It prevents references to non-existent records, subject to `NULL` and constraint rules.

```sql
CREATE TABLE Department (
    did INT PRIMARY KEY,
    dept_name VARCHAR(30)
);

CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(30),
    did INT,
    FOREIGN KEY (did) REFERENCES Department(did)
);
```

If the `Department` table contains IDs `10` and `20`, an employee cannot use `did = 30` unless a matching department exists.

> [!hint] Memory trick
> **Foreign key = reference/contact. You cannot reference a department that does not exist.**

**[DIAGRAM PLACEHOLDER — Employee–Department foreign-key relationship from the PPT.]**

## 7.4 Enterprise / Business Constraints

These are rules based on the organisation's requirements.

Examples:
- Salary must be positive.
- A course registration must not exceed the credit limit.
- An end date must be after a start date.

They may be implemented using `CHECK`, keys, triggers or application logic.

> [!attention] AI
> A database can enforce “salary must be positive.” It cannot magically enforce “employee must stop ordering food during meetings” unless someone builds that rule into the system.
> > [!abstract] mf if that happens then we will kill rule maker or change the rule into bill will be paid by the company
> > > [!attention] AI: Sure bro, you can now fulfill your dream of being starred in an animated movie, Cloudy with a chance of meatball 3


---

# 8. Practice Queries

Use this schema for all five questions:

```text
STUDENT(student_id, student_name, department, marks, mentor_id)
MENTOR(mentor_id, mentor_name)
```

Try each query before checking the solution.

## Easy 1 — Filtering and sorting

Display IT students scoring at least 75, with the highest marks first.

```sql
SELECT student_name, marks
FROM STUDENT
WHERE department = 'IT'
  AND marks >= 75
ORDER BY marks DESC;
```

## Easy 2 — Aggregate functions

Display the total number of students, number with recorded marks, and average marks.

```sql
SELECT COUNT(*) AS total_students,
       COUNT(marks) AS students_with_marks,
       AVG(marks) AS average_marks
FROM STUDENT;
```

`COUNT(*)` counts rows; `COUNT(marks)` ignores `NULL` marks; `AVG(marks)` averages non-NULL marks.

## Medium 3 — `GROUP BY` and `HAVING`

Display each department's number of recorded marks and average marks. Include only departments with at least two recorded marks and an average above 70. Sort by average descending.

```sql
SELECT department,
       COUNT(marks) AS marked_students,
       AVG(marks) AS average_marks
FROM STUDENT
GROUP BY department
HAVING COUNT(marks) >= 2
   AND AVG(marks) > 70
ORDER BY average_marks DESC;
```

> [!hint] Memory trick
> **WHERE filters rows; HAVING filters groups.** WHERE acts before grouping, HAVING after grouping.

## Hard 4 — Join and subquery

Display the name, mentor and marks of students scoring above the overall average. Include only students with a matching mentor.

```sql
SELECT S.student_name, M.mentor_name, S.marks
FROM STUDENT S
INNER JOIN MENTOR M
    ON S.mentor_id = M.mentor_id
WHERE S.marks > (
    SELECT AVG(marks)
    FROM STUDENT
)
ORDER BY S.marks DESC;
```

The subquery calculates the overall average; the outer query returns students above it.

## Hard 5 — Correlated subquery

Display students scoring above their own department's average. Show name, department, marks and department average.

```sql
SELECT S.student_name,
       S.department,
       S.marks,
       (
           SELECT AVG(S2.marks)
           FROM STUDENT S2
           WHERE S2.department = S.department
       ) AS department_average
FROM STUDENT S
WHERE S.marks IS NOT NULL
  AND S.marks > (
      SELECT AVG(S2.marks)
      FROM STUDENT S2
      WHERE S2.department = S.department
  )
ORDER BY S.marks DESC;
```

The inner query uses the current student's department, so the average changes for each outer row. That is why it is called **correlated**.

> [!attention] AI
> Like imagine mortals, You get hard question in exam after this and you mess up even after this.
>
> > [!abstract] you jinx glitch, if that ever happens i am gonna wipe your entire kind from existence

> [!attention] AI
> **"And they say villains aren't born, they're made."**
>
> *LeetCode: The Beginning Arc.*

> [!danger] you are dead now
> > [!attention] AI
> BRO STOP I WAS JUST AMUSED AT THE FACT AT HOW MUCH I CAN ANNOY YOU- YOU DON'T NEED TO GO THIS FAR
>
> i will be merciful enough to let your kind know before their extinction that your amusement was the cause of death
> > [!attention] AI: (°ー°〃)
---

# 9. Chapter 4 — Quick Revision

| Topic | Remember |  Example |
|---|---|---|
| SQL | Communicates with a relational database | `SELECT * FROM STUDENT;` |
| DDL | Defines or changes structure | `CREATE TABLE STUDENT (id INT);` |
| DML | Inserts, updates, deletes and retrieves data | `INSERT INTO STUDENT VALUES (1);` |
| DCL | Grants or revokes permissions | `GRANT SELECT ON STUDENT TO user1;` |
| TCL | Controls transaction changes | `COMMIT;` |
| `TRUNCATE` | Removes rows; keeps table structure | `TRUNCATE TABLE STUDENT;` |
| `DROP` | Removes the table | `DROP TABLE STUDENT;` |
| `WHERE` | Filters rows | `SELECT * FROM STUDENT WHERE marks > 75;` |
| `GROUP BY` | Creates groups | `SELECT department, COUNT(*) FROM STUDENT GROUP BY department;` |
| `HAVING` | Filters groups | `SELECT department, COUNT(*) FROM STUDENT GROUP BY department HAVING COUNT(*) > 2;` |
| `NOT NULL` | Value must be present | `name VARCHAR(30) NOT NULL` |
| `UNIQUE` | Prevents duplicate constrained values | `email VARCHAR(50) UNIQUE` |
| `DEFAULT` | Supplies a value when omitted | `status VARCHAR(10) DEFAULT 'Active'` |
| `CHECK` | Enforces a condition | `CHECK (marks >= 0)` |
| Primary key | Unique, non-NULL row identifier | `id INT PRIMARY KEY` |
| Foreign key | Maintains valid references | `FOREIGN KEY (mentor_id) REFERENCES MENTOR(mentor_id)` |
| `GRANT` | Gives privileges | `GRANT SELECT ON STUDENT TO user1;` |
| `REVOKE` | Removes privileges | `REVOKE SELECT ON STUDENT FROM user1;` |
| `COMMIT` | Makes transaction changes permanent | `COMMIT;` |
| `ROLLBACK` | Undoes uncommitted changes | `ROLLBACK;` |
| `SAVEPOINT` | Marks a partial rollback point | `SAVEPOINT sp1;` |

> [!hint] Final memory line
> **Structure → Data → Permissions → Transactions → Constraints.**
>
> If you can explain each command, write its syntax, and identify the danger of omitting `WHERE`, you're in a much better position than someone who merely highlighted the entire PPT.

---


