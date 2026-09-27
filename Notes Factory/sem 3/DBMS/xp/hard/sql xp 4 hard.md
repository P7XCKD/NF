### AIM

Create and populate database using Data Manipulation Language (DML) commands.

### OBJECTIVE

-   To manage the data stored in the Climate Intelligence database.
    
-   To insert climate-related records into the required tables using the INSERT command.
    
-   To modify existing climate-related records using the UPDATE command.
    
-   To remove unwanted or incorrect records using the DELETE command.
    
-   To retrieve and display stored records using the SELECT command.
    
-   To verify the changes made to the data in the database.
    

### SOFTWARE REQUIREMENT

MySQL Server 8.0  
MySQL Shell 8.0

### THEORY

Data Manipulation Language (DML) is used to manage data stored in database tables.

The main DML commands are:

-   **INSERT** – Adds new records.
    
-   **UPDATE** – Modifies existing records.
    
-   **DELETE** – Removes records.
    
-   **SELECT** – Retrieves records.
    

### GROUP 1 — CREATING DATABASE AND TABLES

The database and required tables are created before performing DML operations. Appropriate constraints are applied to maintain data consistency.

#### Syntax

```sql
CREATE DATABASE database_name;

USE database_name;

CREATE TABLE table_name
(
    column_name datatype constraint,
    column_name datatype constraint
);

SHOW TABLES;
```

### GROUP 2 — INSERTING VALUES AND DISPLAYING THE TABLES

The `INSERT INTO` command adds records to tables, while `SELECT` displays the stored data.

#### Syntax

```sql
INSERT INTO table_name
VALUES (value1, value2, value3);

SELECT * FROM table_name;
```

### GROUP 3 — PERFORMING DML COMMANDS

#### INSERT

The `INSERT` command adds new records to an existing table.

##### Syntax

```sql
INSERT INTO table_name
VALUES (value1, value2, value3);
```

#### UPDATE

The `UPDATE` command modifies existing records using a condition.

##### Syntax

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

#### DELETE

The `DELETE` command removes selected records using a condition.

##### Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

#### SELECT

The `SELECT` command retrieves and displays records from a table.

##### Syntax

```sql
SELECT *
FROM table_name;
```

### OUTCOME

The Climate Intelligence database was successfully managed using DML commands.

### CONCLUSION

Thus, INSERT, UPDATE, DELETE and SELECT commands were successfully used to manage climate-related data.