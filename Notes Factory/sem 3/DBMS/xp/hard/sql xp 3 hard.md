
<p>
    <span style="float:left;">
        <h3> SQL Experiment 3
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

Create and populate database using Data Definition Language (DDL) Integrity Constraints.

### OBJECTIVE

- To create the Climate Intelligence database and its required tables.
- To apply appropriate integrity constraints such as Primary Key, Foreign Key, NOT NULL and CHECK.
- To populate the tables with sample climate-related data.
- To perform DDL operations such as CREATE, ALTER, RENAME, TRUNCATE and DROP.
- To verify the structure and contents of the created database.

### SOFTWARE REQUIREMENT

MySQL Server 8.0  
MySQL Shell 8.0

### THEORY

Data Definition Language (DDL) is used to create and modify the structure of a database.

The main DDL commands are:

- **CREATE** – Creates databases and tables.
- **ALTER** – Modifies the structure of a table.
- **RENAME** – Changes the name of a table.
- **TRUNCATE** – Removes all records while keeping the table structure.
- **DROP** – Permanently removes a table and its structure.

Integrity constraints maintain valid and consistent data. **PRIMARY KEY** uniquely identifies records, **FOREIGN KEY** maintains relationships, **NOT NULL** prevents empty values, and **CHECK** restricts values according to conditions.

### GROUP 1 — CREATING DATABASE AND TABLES

The `CREATE DATABASE` command creates a new database, while `CREATE TABLE` creates tables with required columns and constraints.

#### Syntax

```sql
CREATE DATABASE database_name;

USE database_name;

CREATE TABLE table_name
(
    column_name datatype constraint,
    column_name datatype constraint
);
````

#### Query Example

```sql
CREATE DATABASE climate_monitor_sys;

USE climate_monitor_sys;

CREATE TABLE City
(
    city_code INT PRIMARY KEY,
    city_name VARCHAR(50) NOT NULL
);
```

### GROUP 2 — INSERTING VALUES AND DISPLAYING TABLES

The `INSERT INTO` command is used to add records to a table. The `SELECT` command is used to display the stored records.

#### Syntax

```sql
INSERT INTO table_name
VALUES (value1, value2, value3);

SELECT * FROM table_name;
```

#### Query Example

```sql
INSERT INTO City
VALUES (101, 'Mumbai', 21000000);

SELECT * FROM City;
```

### GROUP 3 — PERFORMING DDL COMMANDS

#### ALTER TABLE

The `ALTER TABLE` command is used to modify the structure of an existing table, such as adding a new column.

##### Syntax

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

##### Query Example

```sql
ALTER TABLE City
ADD state VARCHAR(50);
```

#### RENAME TABLE

The `RENAME TABLE` command changes the name of an existing table.

##### Syntax

```sql
RENAME TABLE old_table_name
TO new_table_name;
```

##### Query Example

```sql
RENAME TABLE City
TO Cities;
```

### GROUP 4 — TRUNCATE TABLE

The `TRUNCATE TABLE` command removes all records from a table but keeps its table structure.

#### Syntax

```sql
TRUNCATE TABLE table_name;
```

#### Query Example

```sql
TRUNCATE TABLE AlertSystem;
```

### GROUP 5 — DROP TABLE

The `DROP TABLE` command permanently removes a table along with its structure and records.

#### Syntax

```sql
DROP TABLE table_name;
```

#### Query Example

```sql
DROP TABLE AlertSystem;
```

### OUTCOME

The Climate Intelligence database was created and DDL commands with integrity constraints were successfully performed.

### CONCLUSION

Thus, DDL commands were successfully used to create, modify and manage the database structure while maintaining data consistency.