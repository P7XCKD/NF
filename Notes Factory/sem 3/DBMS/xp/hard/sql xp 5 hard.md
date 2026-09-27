### AIM

Perform Authorization using GRANT and REVOKE commands.

### OBJECTIVE

-   To understand Data Control Language (DCL).
    
-   To create a new database user.
    
-   To provide permissions using the GRANT command.
    
-   To perform operations using the authorized user.
    
-   To remove permissions using the REVOKE command.
    
-   To verify the effect of authorization and revocation.
    

### SOFTWARE REQUIREMENT

MySQL Server 8.0  
MySQL Shell 8.0

### THEORY

Data Control Language (DCL) controls access to database data.

-   **GRANT** – Gives permissions to a user.
    
-   **REVOKE** – Removes permissions from a user.
    

### GROUP 1 — LOGIN WITH ROOT USER

The root user creates a new user and grants required permissions.

#### Syntax

```sql
SHOW DATABASES;

SELECT user, host
FROM mysql.user;

CREATE USER 'username'@'localhost'
IDENTIFIED BY 'password';

GRANT permission
ON database_name.*
TO 'username'@'localhost';
```

### GROUP 2 — LOGIN WITH AUTHORIZED USER

The authorized user performs operations allowed by the granted permissions.

#### Procedure

Login with the newly created username and password.

#### Syntax

```sql
USE database_name;

CREATE TABLE table_name
(
    column_name datatype
);

INSERT INTO table_name
VALUES (value1, value2);

SELECT * FROM table_name;

UPDATE table_name
SET column_name = value
WHERE condition;

DELETE FROM table_name
WHERE condition;
```

### GROUP 3 — REVOKING PERMISSIONS USING ROOT USER

The root user removes selected permissions using `REVOKE`.

#### Syntax

```sql
REVOKE permission1, permission2
ON database_name.*
FROM 'username'@'localhost';
```

### GROUP 4 — VERIFYING REVOKED PERMISSIONS

The authorized user verifies the remaining permissions after revocation.

#### Syntax

```sql
SELECT * FROM table_name;

INSERT INTO table_name
VALUES (value1, value2);

UPDATE table_name
SET column_name = value
WHERE condition;

DELETE FROM table_name
WHERE condition;
```

Revoked operations are denied, while remaining permissions continue to work.

### OUTCOME

Authorization was successfully performed using GRANT and REVOKE commands.

### CONCLUSION

Thus, DCL was successfully implemented to control database user access.