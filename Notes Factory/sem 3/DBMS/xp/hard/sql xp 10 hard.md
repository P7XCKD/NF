<p>
    <span style="float:left;">
        <h3> SQL Experiment 10
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

To perform Stored Procedures and Functions.

### OBJECTIVE

- To understand stored procedures and functions.
- To create procedures for INSERT, UPDATE, and DELETE operations.
- To create and execute a stored function.

### SOFTWARE REQUIRED

MySQL Server 8.0

### THEORY

**Stored Procedure:** A stored procedure is saved SQL code that can accept parameters and perform operations. It is executed using the `CALL` command.

**Stored Function:** A stored function accepts parameters and returns a value. The `DETERMINISTIC` keyword indicates that the same inputs produce the same result.

### SYNTAX

**Stored Procedure**

```sql
DELIMITER //

CREATE PROCEDURE procedure_name(
    IN parameter_name datatype
)
BEGIN
    SQL statements;
END //

DELIMITER ;

CALL procedure_name(value);
```

**Stored Function**

```sql
DELIMITER //

CREATE FUNCTION function_name(
    parameter_name datatype
)
RETURNS datatype
DETERMINISTIC
BEGIN
    DECLARE variable_name datatype;
    -- SQL statements
    RETURN variable_name;
END //

DELIMITER ;

SELECT function_name(value);
```

### OUTCOME

Stored procedures and functions were successfully created and executed. Procedures performed INSERT, UPDATE, and DELETE operations, while a stored function calculated population in millions.

### CONCLUSION

Thus, stored procedures and functions were successfully implemented in MySQL using parameters, SQL commands, and return values.