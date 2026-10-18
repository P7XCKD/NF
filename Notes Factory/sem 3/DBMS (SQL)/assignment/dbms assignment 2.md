# DBMS Assignment – II Solutions

**Course Code:** ITC303  
**Course:** Database Management System  
**Class:** SY IT, Semester III  
**Roll Number:** 62

---

## Q2 (a). What is the highest normal form for the R3 relation?

Given:

`R3(A, B, C, D)` and functional dependencies `{A → C, CD → B}`.

### Candidate key

- `A+ = {A, C}`, so A is not a key.
- `(AD)+ = {A, D, C, B}`, using `A → C` and `CD → B`.
- Therefore, **AD is the candidate key**.
- Prime attributes: A, D. Non-prime attributes: B, C.

### Normal form

Assuming all attributes contain atomic values, the relation is in 1NF. However, `A → C` is a partial dependency because A is a proper subset of the candidate key AD and C is non-prime. Therefore, it violates 2NF.

**Answer: The highest normal form is 1NF.**

---

## Q2 (b). Consider a relation in 3NF but not in BCNF. Demonstrate redundancy with a suitable instance and normalize the relation to BCNF.

Consider `R(A, B, C)` with functional dependencies `{AB → C, C → B}`.

The candidate keys are **AB** and **AC**. Hence, A, B, and C are all prime attributes.

- The relation is in **3NF** because in `C → B`, B is a prime attribute.
- It is **not in BCNF** because C is not a superkey.

### Example showing redundancy

| A | B | C |
|---|---|---|
| 1 | 10 | X |
| 2 | 10 | X |
| 3 | 20 | Y |

Since `C → B`, C value X determines B value 10. This fact is repeated for multiple A values, causing redundancy.

### BCNF decomposition

Decompose using the violating dependency `C → B`:

**R1(C, B)** — Primary key: C

| C | B |
|---|---|
| X | 10 |
| Y | 20 |

**R2(A, C)** — Primary key: (A, C)

| A | C |
|---|---|
| 1 | X |
| 2 | X |
| 3 | Y |

Both relations are in **BCNF**, and the decomposition is lossless.

---

## Q3. Discuss the deferred update technique of recovery. What are its advantages and disadvantages? Why is it called the NO-UNDO/REDO method?

### Deferred Update Technique

In deferred update, a transaction's changes are recorded in the log but are not applied to the database until the transaction commits.

### Working

1. Record update operations in the log.
2. When the transaction commits, record the commit in the log.
3. Apply the logged updates to the database.
4. After a failure, redo committed transactions if necessary and ignore uncommitted transactions.

### Advantages

- Uncommitted changes do not reach the database.
- Recovery is simpler because uncommitted transactions do not need to be undone.
- The log can be used to restore committed changes.

### Disadvantages

- Committed updates may need to be redone after a failure.
- The log must be maintained and stored reliably.
- Reapplying updates during recovery can increase restart time.

### Why is it called NO-UNDO/REDO?

- **NO-UNDO:** Uncommitted transactions have not updated the database, so their changes do not need to be undone.
- **REDO:** Updates of committed transactions may need to be applied again after a failure.
