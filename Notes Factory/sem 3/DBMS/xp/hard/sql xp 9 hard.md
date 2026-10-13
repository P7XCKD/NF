<p>
    <span style="float:left;">
        <h3> SQL Experiment 9
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

To perform Transaction Control (TCL) using SQL commands.

### OBJECTIVE

- To perform transactions using COMMIT, ROLLBACK, and SAVEPOINT.
- To understand AUTOCOMMIT in transactions.
- To save or undo changes made during a transaction.

### SOFTWARE REQUIRED

MySQL Server 8.0

### THEORY

Transaction Control Language (TCL) manages database transactions.

- **COMMIT:** Saves transaction changes permanently.
- **ROLLBACK:** Undoes uncommitted changes.
- **SAVEPOINT:** Creates a point to which a transaction can be rolled back.
- **AUTOCOMMIT:** Automatically commits each statement when enabled.

### SYNTAX

**COMMIT**

```sql
COMMIT;
```

**ROLLBACK**

```sql
ROLLBACK;
```

**SAVEPOINT**

```sql
SAVEPOINT savepoint_name;
```

**ROLLBACK TO SAVEPOINT**

```sql
ROLLBACK TO SAVEPOINT savepoint_name;
```

**Check AUTOCOMMIT**

```sql
SHOW VARIABLES LIKE 'autocommit';
```

**Disable AUTOCOMMIT**

```sql
SET autocommit = 0;
```

**Enable AUTOCOMMIT**

```sql
SET autocommit = 1;
```

### OUTCOME

Transaction operations were successfully performed on climate data using COMMIT, ROLLBACK, and SAVEPOINT.

### CONCLUSION

Thus, TCL commands were successfully implemented to manage and control transactions in the Climate Intelligence database.