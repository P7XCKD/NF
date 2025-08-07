

### Aim:
To implement ALTER, UPDATE, DELETE, and DROP commands.

### Theory:

1. **ALTER**:
   - **ALTER TABLE ... ADD ...**: This is used to add some extra fields into existing relation.
     - **Syntax**: 
       ```sql
       ALTER TABLE relation_name ADD (new_field_1 data_type(size), new_field_2 data_type(size), ...);
       ```
     - **Example**: 
       ```sql
       ALTER TABLE std ADD (Address CHAR(10));
       ```

   - **ALTER TABLE ... MODIFY ...**: This is used to change the width as well as data type of fields of existing relations.
     - **Syntax**:
       ```sql
       ALTER TABLE relation_name MODIFY (field_1 newdata_type(size), field_2 newdata_type(size), ...);
       ```
     - **Example**: 
       ```sql
       ALTER TABLE student MODIFY (sname VARCHAR(10), class VARCHAR(5));
       ```

   - **ALTER TABLE ... DROP ...**: This is used to remove any field of existing relations.
     - **Syntax**: 
       ```sql
       ALTER TABLE relation_name DROP COLUMN field_name;
       ```
     - **Example**: 
       ```sql
       ALTER TABLE student DROP COLUMN sname;
       ```

   - **ALTER TABLE ... RENAME ...**: This is used to change the name of fields in existing relations.
     - **Syntax**: 
       ```sql
       ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
       ```
     - **Example**: 
       ```sql
       ALTER TABLE student RENAME COLUMN sname TO stu_name;
       ```

2. **DROP TABLE**: This is used to delete the structure of a relation. It permanently deletes the records in the table.
   - **Syntax**: 
     ```sql
     DROP TABLE relation_name;
     ```
   - **Example**: 
     ```sql
     DROP TABLE std;
     ```

3. **RENAME**: It is used to modify the name of the existing database object.
   - **Syntax**: 
     ```sql
     RENAME TABLE old_relation_name TO new_relation_name;
     ```
   - **Example**: 
     ```sql
     RENAME TABLE std TO std1;
     ```

4. **UPDATE-SET-WHERE**: This is used to update the content of a record in a relation.
   - **Syntax**:
     ```sql
     UPDATE relation_name SET field_name1 = data, field_name2 = data WHERE field_name = data;
     ```
   - **Example**:
     ```sql
     UPDATE student SET sname = 'kumar' WHERE sno = 1;
     ```

5. **DELETE-FROM**: This is used to delete all the records of a relation but it will retain the structure of that relation.
   - **Syntax**:
     ```sql
     DELETE FROM relation_name;
     ```
   - **Example**:
     ```sql
     DELETE FROM std;
     ```

6. **DELETE-FROM-WHERE**: This is used to delete a selected record from a relation.
   - **Syntax**:
     ```sql
     DELETE FROM relation_name WHERE condition;
     ```
   - **Example**:
     ```sql
     DELETE FROM student WHERE sno = 2;
     ```

     conclusion: hence  we successfully implemented  Alter, Update, Delete and Drop Commands in sql