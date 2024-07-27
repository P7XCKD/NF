https://drive.google.com/drive/folders/1W4gzaImfw_sh5kaB7XqiXsYDVUGrTwTE
lab manual refrence^ ignore this

 **aim**  : Creating of table with constraint and insertion of data. 



**Theory: SQL (Structured Query Language)**

SQL is a language designed for managing data in relational database management systems (RDBMS), rooted in Relational Algebra. It supports data querying, updating, schema creation, modification, and access control. Developed by IBM in the 1970s, SQL was incorporated by Oracle in 1979 and standardized by ANSI in 1989. It became the most widely used language for relational databases.

**Data Types:**

1. **CHAR (Size):** Stores fixed-length character strings. The size (up to 255 characters) defines the length of the string.

2. **VARCHAR (Size) / VARCHAR2 (Size):** Stores variable-length alphanumeric data, with a maximum of 2000 characters.

3. **NUMBER (P, S):** Stores numerical data with up to 38 digits of precision. Precision (p) specifies total digits, and scale (s) specifies digits to the right of the decimal. If omitted, defaults are zero for scale and original precision for numbers.

**Data Types:**

4. **DATE:** Represents date and time in the format DD-MM-YY (e.g., 17-SEP-2009). By default, if no time is specified, the time is 12:00:00 AM, and if no date is provided, it defaults to the first day of the current month. For non-standard formats, use appropriate functions.

5. **LONG:** Stores variable-length character strings up to 2GB. It is used for large text or binary data in ASCII format but cannot be indexed or manipulated with normal character functions like SUBSTR.

6. **RAW:** Stores binary data (e.g., images) without conversion, with a maximum length of 255 bytes. LONG RAW can store up to 2GB.

**SQL Language Elements:**

- **Clauses:** Optional components of statements and queries.
- **Expressions:** Produce scalar values or tables of data.
- **Predicates:** Specify conditions evaluated to SQL three-valued logic (3VL) Boolean values, used to filter data or alter program flow.
- **Queries:** Retrieve data based on criteria.
- **Statements:** Can affect schemas and data or control transactions, program flow, connections, sessions, or diagnostics. SQL statements use a semicolon (";") as a terminator, defined in the SQL standard.
- **Whitespace:** Insignificant white space is ignored, aiding in code readability.

#### There are five types of SQL statements:

1. DDL (Data Definition Language)
2. DML (Data Manipulation Language)
3. DRL (Data Retrieval Language)
4. TCL (Transactional Control Language)
5. DCL (Data Control Language)


***
1. **CREATE TABLE:** Defines a new table with columns and their data types.
   - **Syntax:** `CREATE TABLE <table_name> (column_1 data_type(size), column_2 data_type(size), ...);`
   
   - **CONSTRAINTS:** Rules applied to table data. They can be set during table creation (`CREATE TABLE`) or modified later (`ALTER TABLE`).

     - **NOT NULL:** Requires a column to have a value; it cannot be empty.
       - **Syntax:** `CREATE TABLE Table_Name (column_name data_type(size) NOT NULL, ...);`
       - **Example:** `CREATE TABLE student (sno NUMBER(3) NOT NULL, name CHAR(10));`
     
     - **UNIQUE:** Ensures that all values in a column are unique.
       - **Syntax:** `CREATE TABLE Table_Name (column_name data_type(size) UNIQUE, ...);`
       - **Example:** `CREATE TABLE student (sno NUMBER(3) UNIQUE, name CHAR(10));`

3. **CHECK:** Enforces a condition that each row must satisfy; the condition must be TRUE or unknown (if null).
   - **Syntax:** `CREATE TABLE Table_Name (column_name data_type(size) CHECK (condition), ...);`
   - **Example:** `CREATE TABLE student (sno NUMBER(3), name CHAR(10), class CHAR(5), CHECK (class IN ('CSE', 'CAD', 'VLSI')));`


4. **PRIMARY KEY:** A unique identifier for records in a table, which must be unique, non-null, and minimal. It can be a single column or a combination of columns, and is referenced by other tables. The table with the primary key is known as the Master Table.
   - **Syntax:** `CREATE TABLE Table_Name (column_name data_type(size) PRIMARY KEY, ...);`
   - **Example:** `CREATE TABLE faculty (fcode NUMBER(3) PRIMARY KEY, fname CHAR(10));`
***
**5. FOREIGN KEY**: This is a table-level constraint used to reference a primary key from another table. The table where the foreign key is defined is called the detail table, while the table with the primary key is the master table.

**Syntax**: 
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY(column_name) REFERENCES table_name
);
```

**Example**: 
```sql
CREATE TABLE subject (
  scode NUMBER(3) PRIMARY KEY, 
  subname CHAR(10), 
  fcode NUMBER(3),
  FOREIGN KEY(fcode) REFERENCES faculty
);
```

**Adding Primary Key**: 

**Syntax**: 
```sql
ALTER TABLE Table_Name ADD PRIMARY KEY (column_name);
```

**Example**: 
```sql
ALTER TABLE student ADD PRIMARY KEY (sno);
```

**Adding Constraint**:

**Syntax**: 
```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name PRIMARY KEY (colname);
```

**Example**: 
```sql
ALTER TABLE student ADD CONSTRAINT SN PRIMARY KEY (SNO);
```

**Dropping Constraints**:

**Syntax**: 
```sql
ALTER TABLE Table_Name DROP constraint_name;
```

**Example**: 
```sql
ALTER TABLE student DROP PRIMARY KEY;
```

**Or**

**Syntax**: 
```sql
ALTER TABLE student DROP CONSTRAINT constraint_name;
```

**Example**: 
```sql
ALTER TABLE student DROP CONSTRAINT SN;
```

**6. DEFAULT**: The DEFAULT constraint provides a default value for a column when no value is specified for new records.

**Syntax**: 
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT '<value>'
);
```

**Example**: 
```sql
CREATE TABLE student (
  sno NUMBER(3) UNIQUE, 
  name CHAR(10), 
  address VARCHAR(20) DEFAULT 'Aurangabad'
);
```

Conclusion: hence, we successfully created of table with constraint and insertion of data.