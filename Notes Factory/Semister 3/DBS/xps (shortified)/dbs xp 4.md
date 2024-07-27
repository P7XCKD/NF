

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
   - Syntax: 
     ```sql
     RENAME TABLE old_relation_name TO new_relation_name;
     ```
   - Example: 
     ```sql
     RENAME TABLE std TO std1;
     ```

4. **UPDATE-SET-WHERE**: Update the content of a record in a table.
   - Syntax:
     ```sql
     UPDATE relation_name SET field_name1 = data, field_name2 = data WHERE field_name = data;
     ```
   - Example:
     ```sql
     UPDATE student SET sname = 'kumar' WHERE sno = 1;
     ```

5. **DELETE-FROM**: Delete all the records of a table but retain its structure.
   - Syntax:
     ```sql
     DELETE FROM relation_name;
     ```
   - Example:
     ```sql
     DELETE FROM std;
     ```

6. **DELETE-FROM-WHERE**: Delete a selected record from a table.
   - Syntax:
     ```sql
     DELETE FROM relation_name WHERE condition;
     ```
   - Example:
     ```sql
     DELETE FROM student WHERE sno = 2;
     ```