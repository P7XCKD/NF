
<p>
    <span style="float:left;">
        <h3>SQL Experiment 12</h3>
    </span>
    <span style="float:right; text-align:right;">
        <h3>Name: Dev Mandora<br>
        Roll Number: 62<br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

Implementation and demonstration of transaction and concurrency control technique using lock.

### OBJECTIVE

- To understand shared and exclusive locks.
- To demonstrate concurrency control using two MySQL sessions.
- To understand transaction management using locks.

### SOFTWARE REQUIRED

MySQL Server 8.0

### THEORY

Locks control simultaneous access to database records.

- **Shared Lock:** Allows multiple sessions to read the same record.
- **Exclusive Lock:** Allows a session to modify a record and prevents conflicting access.

### SYNTAX

Shared Lock
```sql
SELECT * FROM Temperature
WHERE ID = 1 FOR SHARE;
````

Exclusive Lock

```
SELECT * FROM Temperature
WHERE ID = 1 FOR UPDATE;
```

Transaction Control

```
START TRANSACTION;
COMMIT;
```

### OUTCOME

Shared and exclusive locks were demonstrated successfully using two MySQL sessions.

### CONCLUSION

Thus, transaction and concurrency control using locks were implemented successfully