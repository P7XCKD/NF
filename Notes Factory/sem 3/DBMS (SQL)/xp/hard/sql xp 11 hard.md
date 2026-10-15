<p>
    <span style="float:left;">
        <h3> SQL Experiment 11
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

To implement Cursors in SQL.

### OBJECTIVE

- To understand the concept of cursors.
- To fetch temperature records one by one using a cursor.
- To process weather observations using a stored procedure.

### SOFTWARE REQUIREMENT

MySQL Server 8.0

### THEORY

A cursor processes query results one row at a time. It is useful when individual records need separate processing.

The main cursor operations are:

- **DECLARE:** Defines the cursor and its SELECT query.
- **OPEN:** Opens the cursor.
- **FETCH:** Retrieves the next record.
- **CLOSE:** Closes the cursor.

A `NOT FOUND` handler detects when no more records are available.

### SYNTAX

**Declare Cursor**
```sql
DECLARE cursor_name CURSOR FOR
SELECT columns FROM table_name;
```

**Open Cursor**
```sql
OPEN cursor_name;
```

**Fetch Record**
```sql
FETCH cursor_name INTO variable1, variable2;
```

**Close Cursor**
```sql
CLOSE cursor_name;
```

### OUTCOME

A cursor was successfully implemented to fetch and display station IDs and temperatures one record at a time using a stored procedure.

### CONCLUSION

Thus, SQL cursors were successfully implemented using DECLARE, OPEN, FETCH, and CLOSE to process weather observation records sequentially.