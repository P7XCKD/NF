
<p>
    <span style="float:left;">
        <h3>SQL Experiment 8</h3>
    </span>


### AIM
To demonstrate database connectivity by preparing a simple form using a scripting language.

### OBJECTIVE
- Connect a web application to MySQL using Java.
- Perform CRUD operations on weather observation records.

### SOFTWARE REQUIREMENT
- JDK 17
- MySQL Server 8.0
- MySQL Workbench
- MySQL Connector/J
- Text editor and web browser

### THEORY
JDBC connects Java applications to MySQL databases. HTML, CSS and JavaScript provide the interface, while Java handles database operations.

### PROCEDURE
1. Start MySQL Server.
2. Open MySQL Workbench and execute the following SQL syntax.

### SYNTAX

**1. Create Database**
```sql
CREATE DATABASE climate_form_db;
USE climate_form_db;
````

2. Create Table

```
CREATE TABLE Weather_Observation (
    Observation_ID INT AUTO_INCREMENT PRIMARY KEY,
    Station_ID INT,
    Temperature DECIMAL(5,2),
    Humidity DECIMAL(5,2),
    Heat_Index DECIMAL(5,2)
);
```

### PROCEDURE TO CONNECT DATABASE

1.  Download and add MySQL Connector/J to the project.
    
2.  Configure the database connection in `ClimateServer.java`:
    

```powershell
String url = "jdbc:mysql://localhost:3306/climate_form_db";
String user = "root";
String password = "your_password";

Connection con = DriverManager.getConnection(
    url, user, password
);
```

3. Compile and run the Java backend from the project folder:

```powershell
javac -cp ".;mysql-connector-j-VERSION.jar" backend\ClimateServer.java

java -cp ".;mysql-connector-j-VERSION.jar;backend" ClimateServer
```

Replace `VERSION` with the actual Connector/J JAR version and enter the correct MySQL password.

4.  Open `http://localhost:8080` in the browser.
    
5.  Add, view, update and delete weather records using the form.
    
6.  Verify the records in MySQL Workbench:
    

```sql
USE climate_form_db;
SELECT * FROM Weather_Observation;
```

### OUTCOME

Successfully connected a Java web application to MySQL and performed CRUD operations on weather observation records.

### CONCLUSION

Database connectivity was established using JDBC, allowing the application to manage weather observation data in MySQL.