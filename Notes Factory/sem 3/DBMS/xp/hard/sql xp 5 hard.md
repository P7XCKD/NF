### AIM

Perform Authorization using GRANT and REVOKE commands.

### OBJECTIVE

-   To understand Data Control Language (DCL).
    
-   To create a new database user.
    
-   To provide permissions to a user using the GRANT command.
    
-   To perform database operations using the authorized user.
    
-   To remove selected permissions using the REVOKE command.
    
-   To verify the effect of authorization and revocation of permissions.
    

### SOFTWARE REQUIREMENT

MySQL Server 8.0  
MySQL Shell 8.0

### THEORY

Data Control Language (DCL) is used to control access to data stored in a database.

The main DCL commands are:

-   **GRANT** – Gives permissions to a user.
    
-   **REVOKE** – Removes permissions from a user.
    

### GROUP 1 — LOGIN WITH ROOT USER

The root user is used to create a new database user and provide the required permissions.

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

The authorized user can perform only the database operations allowed through the granted permissions.

#### Procedure

Login with the newly created user using the assigned username and password.

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

The root user can remove selected permissions from an authorized user using the `REVOKE` command.

#### Syntax

```sql
REVOKE permission1, permission2
ON database_name.*
FROM 'username'@'localhost';
```

### GROUP 4 — VERIFYING REVOKED PERMISSIONS

The authorized user is used again to verify which operations are still allowed after permissions are revoked.

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

After revocation, operations whose permissions were removed are denied, while the remaining authorized operations can still be performed.

### OUTCOME

Authorization was successfully performed using GRANT and REVOKE commands. User permissions were granted and revoked as required.

### CONCLUSION

Thus, DCL was successfully implemented using GRANT and REVOKE to control database user access.