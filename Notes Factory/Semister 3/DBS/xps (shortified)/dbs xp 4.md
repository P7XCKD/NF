

### Aim:
To implement ALTER, UPDATE, DELETE, and DROP commands.

### Theory:

1. **ALTER**:
   - **ALTER TABLE ... ADD ...**: Add new fields to an existing table.
     - Syntax: 
       ```sql
       ALTER TABLE relation_name ADD (new_field_1 data_type(size), new_field_2 data_type(size), ...);
       ```
     - Example: 
       ```sql
       ALTER TABLE std ADD (Address CHAR(10));
       ```

   - **ALTER TABLE ... MODIFY ...**: Change the data type or size of existing fields.
     - Syntax:
       ```sql
       ALTER TABLE relation_name MODIFY (field_1 newdata_type(size), field_2 newdata_type(size), ...);
       ```
     - Example: 
       ```sql
       ALTER TABLE student MODIFY (sname VARCHAR(10), class VARCHAR(5));
       ```

   - **ALTER TABLE ... DROP ...**: Remove a field from an existing table.
     - Syntax: 
       ```sql
       ALTER TABLE relation_name DROP COLUMN field_name;
       ```
     - Example: 
       ```sql
       ALTER TABLE student DROP COLUMN sname;
       ```

   - **ALTER TABLE ... RENAME ...**: Change the name of a field.
     - Syntax: 
       ```sql
       ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
       ```
     - Example: 
       ```sql
       ALTER TABLE student RENAME COLUMN sname TO stu_name;
       ```

2. **DROP TABLE**: Delete the structure and records of a table.
   - Syntax: 
     ```sql
     DROP TABLE relation_name;
     ```
   - Example: 
     ```sql
     DROP TABLE std;
     ```

3. **RENAME**: Modify the name of an existing database object.