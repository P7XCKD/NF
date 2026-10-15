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
- To demonstrate locks using two MySQL sessions.
- To understand transaction control using AUTOCOMMIT set to 0.

### SOFTWARE REQUIRED

MySQL Server 8.0

### THEORY

Locks are used to control concurrent access to database records.

- **Shared Lock (S Lock):** Allows multiple sessions to read the same record simultaneously.
- **Exclusive Lock (X Lock):** Allows a session to modify a record and prevents conflicting locks from other sessions.

### SYNTAX

**Shared Lock**

```sql
START TRANSACTION;

SELECT * FROM Temperature
WHERE ID = 1
FOR SHARE;

COMMIT;