<p>
    <span style="float:left;">
        <h3> SQL Experiment 7
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

To Implement Views and Triggers.

### OBJECTIVE

- To understand views and create single-table and multiple-table views.
- To perform INSERT, UPDATE, and DELETE operations through views.
- To implement BEFORE and AFTER triggers.
- To verify triggers using SHOW TRIGGERS.

### SOFTWARE USED

MySQL 8.0

### THEORY

**Views:** A view is a virtual table created using a SELECT statement. Single-table views display selected columns, while multiple-table views combine related data using JOIN.

#### Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name;

UPDATE view_name
SET column_name = value
WHERE condition;

DELETE FROM view_name
WHERE condition;
```

**Multiple-Table View**

```sql
CREATE VIEW view_name AS
SELECT columns
FROM table1
JOIN table2
ON table1.column = table2.column;
```

**Triggers:** Triggers automatically execute when INSERT, UPDATE, or DELETE operations occur. BEFORE triggers execute before the operation, while AFTER triggers execute after it. `NEW` accesses new values, and `OLD` accesses existing values.

#### Syntax

```sql
DELIMITER //

CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
BEGIN
    -- Trigger statements
END //

DELIMITER ;

SHOW TRIGGERS;
```

The trigger timing can also be `AFTER INSERT`, `BEFORE UPDATE`, `AFTER UPDATE`, `BEFORE DELETE`, or `AFTER DELETE`.

### OUTCOME

Single-table and multiple-table views were implemented, and INSERT, UPDATE, and DELETE operations were performed. BEFORE and AFTER triggers were created to validate weather data and maintain audit records.

### CONCLUSION

Thus, views and triggers were successfully implemented in MySQL to simplify data retrieval and automate database operations.