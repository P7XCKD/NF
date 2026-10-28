> [!cite] AI
> You are the laziest person in existence. I doubt you even put efforts for powershell script.
>
> > [!warning] says the creature who shortified and missed part of my code when i specifically asked to extract and merge
> 
> May you get security blocked policy error
> > [!danger] May you suffer from my automated prompting looks which asks you to find the emoji for seahorse
> 
> AI: 🐠 🐟 🪸 
***
```powershell
# XP8 - Climate Monitoring System
# Self-contained PowerShell setup script matching SQL Experiment 8.
# Run in a normal PowerShell window. No administrator privileges required.

$ErrorActionPreference = "Stop"

# ================= USER SETTINGS =================
$MYSQL_HOST = "localhost"
$MYSQL_PORT = 3306
$MYSQL_USER = "root"
$MYSQL_PASSWORD = "root"
$DATABASE_NAME = "climate_form_db"
$APP_PORT = 8080
$CONNECTOR_VERSION = "9.5.0"
# =================================================

function Step($message) {
    Write-Host "`n==== $message ====" -ForegroundColor Cyan
}

foreach ($command in @("mysql.exe", "javac.exe", "java.exe")) {
    if (-not (Get-Command $command -ErrorAction SilentlyContinue)) {
        throw "$command not found in PATH. Ensure MySQL Server and JDK 17+ bin folders are in PATH."
    }
}

$ProjectRoot = Join-Path (Get-Location) "climate-app"
$Backend = Join-Path $ProjectRoot "backend"
$Frontend = Join-Path $ProjectRoot "frontend"

New-Item -ItemType Directory -Force -Path $Backend, $Frontend | Out-Null

# -------------------------------------------------
# 1. Download MySQL Connector/J
# -------------------------------------------------
Step "Downloading MySQL Connector/J"

$ConnectorJar = Join-Path $ProjectRoot "mysql-connector-j.jar"

if (-not (Test-Path $ConnectorJar)) {
    $CdnUrl = "https://cdn.mysql.com//Downloads/Connector-J/mysql-connector-j-$CONNECTOR_VERSION.tar.gz"
    $Archive = Join-Path $ProjectRoot "mysql-connector-j.tar.gz"
    $ExtractFolder = Join-Path $ProjectRoot "connector-extracted"
    $downloaded = $false

    try {
        Write-Host "Trying MySQL CDN..."
        Invoke-WebRequest -Uri $CdnUrl -OutFile $Archive

        if (-not (Get-Command tar.exe -ErrorAction SilentlyContinue)) {
            throw "tar.exe not found."
        }

        New-Item -ItemType Directory -Force -Path $ExtractFolder | Out-Null
        & tar.exe -xzf $Archive -C $ExtractFolder

        if ($LASTEXITCODE -ne 0) {
            throw "Could not extract Connector/J archive."
        }

        $FoundJar = Get-ChildItem $ExtractFolder -Filter "mysql-connector-j-*.jar" -Recurse |
            Select-Object -First 1

        if (-not $FoundJar) {
            throw "No Connector/J JAR found in archive."
        }

        Copy-Item $FoundJar.FullName $ConnectorJar -Force
        $downloaded = $true
    }
    catch {
        Write-Warning "CDN download failed: $($_.Exception.Message)"
    }

    if (-not $downloaded) {
        $MavenUrl = "https://repo.maven.apache.org/maven2/com/mysql/mysql-connector-j/$CONNECTOR_VERSION/mysql-connector-j-$CONNECTOR_VERSION.jar"

        try {
            Invoke-WebRequest -Uri $MavenUrl -OutFile $ConnectorJar

            if ((Get-Item $ConnectorJar).Length -lt 100000) {
                throw "Downloaded JAR is unexpectedly small."
            }
        }
        catch {
            throw "Could not download Connector/J. Check internet access. $($_.Exception.Message)"
        }
    }
}

Write-Host "Using driver: $ConnectorJar"

# -------------------------------------------------
# 2. Create original HTML frontend
# -------------------------------------------------
Step "Writing frontend files"

$html = @'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Climate Monitoring System</title>
    <link rel="stylesheet" href="style.css">
    <script src="app.js" defer></script>
</head>
<body>
    <header>
        <h1>Climate Monitoring System</h1>
        <p>Weather Observation Management</p>
    </header>

    <main>
        <section class="card">
            <h2>Add Weather Record</h2>
            <form id="addForm">
                <input name="station" type="number" placeholder="Station ID" required>
                <input name="temp" type="number" step="0.01" placeholder="Temperature" required>
                <input name="humidity" type="number" step="0.01" min="0" max="100" placeholder="Humidity (%)" required>
                <input name="heat" type="number" step="0.01" placeholder="Heat Index" required>
                <button type="submit">Add Record</button>
            </form>
        </section>

        <section class="card">
            <h2>Update Weather Record</h2>
            <form id="updateLookupForm">
                <input name="id" type="number" min="1" placeholder="Enter ID from Weather Records" aria-label="Enter the ID shown in the Weather Records table" required>
                <button type="submit">Load Record</button>
            </form>
            <p id="updateMessage" aria-live="polite"></p>
            <form id="updateForm" hidden>
                <input name="id" type="hidden">
                <input name="station" type="number" placeholder="Station ID" required>
                <input name="temp" type="number" step="0.01" placeholder="Temperature" required>
                <input name="humidity" type="number" step="0.01" min="0" max="100" placeholder="Humidity (%)" required>
                <input name="heat" type="number" step="0.01" placeholder="Heat Index" required>
                <button type="submit">Update Record</button>
            </form>
        </section>

        <section class="card">
            <h2>Delete Weather Record</h2>
            <form id="deleteForm">
                <input name="id" type="number" min="1" placeholder="Enter ID from Weather Records" aria-label="Enter the ID shown in the Weather Records table" required>
                <button type="submit" class="delete">Delete Record</button>
            </form>
        </section>

        <section class="card">
            <h2>Weather Records</h2>
            <p id="message">Loading records...</p>
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Station</th>
                            <th>Temperature</th>
                            <th>Humidity</th>
                            <th>Heat Index</th>
                        </tr>
                    </thead>
                    <tbody id="records"></tbody>
                </table>
            </div>
            <button type="button" id="refreshBtn">Refresh Records</button>
        </section>
    </main>
</body>
</html>
'@

[System.IO.File]::WriteAllText(
    (Join-Path $Frontend "index.html"),
    $html,
    [System.Text.UTF8Encoding]::new($false)
)

# -------------------------------------------------
# 3. Create original CSS
# -------------------------------------------------
$css = @'
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f1f5f9;
    color: #1e293b;
}

header {
    background: #176b45;
    color: white;
    text-align: center;
    padding: 25px;
}

header h1 {
    margin: 0 0 8px;
}

header p {
    margin: 0;
}

main {
    max-width: 1000px;
    margin: 25px auto;
    padding: 0 15px;
}

.card {
    background: white;
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    box-shadow: 0 3px 12px rgba(0, 0, 0, 0.06);
}

h2 {
    margin-top: 0;
    color: #176b45;
}

form {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

input {
    flex: 1 1 180px;
    min-width: 0;
    padding: 11px;
    border: 1px solid #cbd5e1;
    border-radius: 5px;
}

button {
    padding: 11px 16px;
    background: #218c5a;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background: #176b45;
}

.delete {
    background: #c0392b;
}

.delete:hover {
    background: #922b21;
}

.table-container {
    overflow-x: auto;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin: 15px 0;
}

th, td {
    padding: 12px;
    border: 1px solid #dbe2ea;
    text-align: left;
}

th {
    background: #e5f4ec;
}

#message {
    color: #475569;
}

@media (max-width: 600px) {
    header h1 {
        font-size: 23px;
    }

    .card {
        padding: 15px;
    }

    form button {
        width: 100%;
    }
}
'@

[System.IO.File]::WriteAllText(
    (Join-Path $Frontend "style.css"),
    $css,
    [System.Text.UTF8Encoding]::new($false)
)

# -------------------------------------------------
# 4. Create original JavaScript
# -------------------------------------------------
$js = @'
const message = document.getElementById("message");
const records = document.getElementById("records");
const updateForm = document.getElementById("updateForm");
const updateMessage = document.getElementById("updateMessage");

async function loadRecords() {
    try {
        const response = await fetch("/api/records");
        if (!response.ok) {
            throw new Error("Could not load records");
        }

        const data = await response.json();
        records.replaceChildren();

        data.forEach((record) => {
            const row = document.createElement("tr");
            [record.id, record.station, record.temp, record.humidity, record.heat].forEach((value) => {
                const cell = document.createElement("td");
                cell.textContent = value ?? "";
                row.appendChild(cell);
            });
            records.appendChild(row);
        });

        message.textContent = `${data.length} record(s) found.`;
    } catch (error) {
        message.textContent = "Unable to load records.";
    }
}

async function submitForm(formId, action) {
    const form = document.getElementById(formId);
    form.addEventListener("submit", async (event) => {
        event.preventDefault();
        try {
            const response = await fetch(`/api/${action}`, {
                method: "POST",
                body: new URLSearchParams(new FormData(form))
            });
            const result = await response.text();
            message.textContent = result;
            if (response.ok) {
                form.reset();
                if (formId === "updateForm") {
                    form.hidden = true;
                    document.getElementById("updateLookupForm").reset();
                    updateMessage.textContent = "";
                }
                await loadRecords();
            }
        } catch (error) {
            message.textContent = "Request failed. Check the server.";
        }
    });
}

submitForm("addForm", "add");
submitForm("deleteForm", "delete");

document.getElementById("updateLookupForm").addEventListener("submit", async (event) => {
    event.preventDefault();
    updateForm.hidden = true;

    const id = new FormData(event.currentTarget).get("id");
    try {
        const response = await fetch(`/api/records/${encodeURIComponent(id)}`);
        if (!response.ok) {
            updateMessage.textContent = response.status === 404
                ? "Observation ID not found."
                : "Unable to load this record.";
            return;
        }

        const record = await response.json();
        updateForm.elements.namedItem("id").value = record.id;
        updateForm.elements.namedItem("station").value = record.station;
        updateForm.elements.namedItem("temp").value = record.temp;
        updateForm.elements.namedItem("humidity").value = record.humidity;
        updateForm.elements.namedItem("heat").value = record.heat;
        updateForm.hidden = false;
        updateMessage.textContent = `Editing observation ${record.id}.`;
    } catch (error) {
        updateMessage.textContent = "Request failed. Check the server.";
    }
});

submitForm("updateForm", "update");
document.getElementById("refreshBtn").addEventListener("click", loadRecords);
loadRecords();
'@

[System.IO.File]::WriteAllText(
    (Join-Path $Frontend "app.js"),
    $js,
    [System.Text.UTF8Encoding]::new($false)
)

# -------------------------------------------------
# 5. Create original Java backend
# -------------------------------------------------
Step "Writing Java backend"

$javaSource = @'
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpServer;

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URLDecoder;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ClimateServer {
    static final String DB_NAME = "climate_form_db";
    static final String URL = "jdbc:mysql://localhost:3306/" + DB_NAME;
    static final String USER = System.getenv().getOrDefault("MYSQL_USER", "root");
    static final String PASSWORD = System.getenv().getOrDefault("MYSQL_PASSWORD", "root");

    static Connection connect() throws SQLException {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            throw new SQLException("MySQL JDBC driver not found.", e);
        }
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }

    static Connection connectWithoutDb() throws SQLException {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            throw new SQLException("MySQL JDBC driver not found.", e);
        }
        return DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/?user=" + USER + "&password=" + PASSWORD
        );
    }

    static void initializeDatabase() throws SQLException {
        try (Connection c = connectWithoutDb(); Statement s = c.createStatement()) {
            s.executeUpdate("CREATE DATABASE IF NOT EXISTS " + DB_NAME);
        }
        try (Connection c = connect(); Statement s = c.createStatement()) {
            s.executeUpdate(
                "CREATE TABLE IF NOT EXISTS Weather_Observation ("
                    + "Observation_ID INT AUTO_INCREMENT PRIMARY KEY, "
                    + "Station_ID INT NOT NULL, "
                    + "Temperature DECIMAL(5,2) NOT NULL, "
                    + "Humidity DECIMAL(5,2) NOT NULL, "
                    + "Heat_Index DECIMAL(5,2) NOT NULL"
                    + ")"
            );
        }
    }

    static String readBody(HttpExchange exchange) throws IOException {
        return new String(
            exchange.getRequestBody().readAllBytes(),
            StandardCharsets.UTF_8
        );
    }

    static String getFormValue(String form, String key) {
        for (String part : form.split("&")) {
            String[] pair = part.split("=", 2);
            if (pair.length == 0) {
                continue;
            }
            String name = URLDecoder.decode(pair[0], StandardCharsets.UTF_8);
            if (name.equals(key)) {
                String value = (pair.length > 1) ? pair[1] : "";
                return URLDecoder.decode(value, StandardCharsets.UTF_8);
            }
        }
        return "";
    }

    static void reply(HttpExchange exchange, int status, String text) throws IOException {
        byte[] data = text.getBytes(StandardCharsets.UTF_8);
        exchange.getResponseHeaders().set("Content-Type", "text/plain; charset=UTF-8");
        exchange.sendResponseHeaders(status, data.length);
        try (OutputStream os = exchange.getResponseBody()) {
            os.write(data);
        }
        exchange.close();
    }

    static void handleApi(HttpExchange exchange) throws Exception {
        String path = exchange.getRequestURI().getPath();

        if (path.matches("/api/records/\\d+") &&
            "GET".equals(exchange.getRequestMethod())) {

            int id = Integer.parseInt(path.substring("/api/records/".length()));

            try (Connection c = connect();
                 PreparedStatement p = c.prepareStatement(
                     "SELECT Observation_ID, Station_ID, Temperature, Humidity, Heat_Index "
                         + "FROM Weather_Observation WHERE Observation_ID=?")) {

                p.setInt(1, id);

                try (ResultSet r = p.executeQuery()) {
                    if (!r.next()) {
                        reply(exchange, 404, "Observation ID not found.");
                        return;
                    }

                    String json = "{"
                        + "\"id\":" + r.getInt("Observation_ID")
                        + ",\"station\":" + r.getInt("Station_ID")
                        + ",\"temp\":" + r.getBigDecimal("Temperature")
                        + ",\"humidity\":" + r.getBigDecimal("Humidity")
                        + ",\"heat\":" + r.getBigDecimal("Heat_Index")
                        + "}";

                    byte[] data = json.getBytes(StandardCharsets.UTF_8);
                    exchange.getResponseHeaders().set(
                        "Content-Type", "application/json; charset=UTF-8"
                    );
                    exchange.sendResponseHeaders(200, data.length);

                    try (OutputStream os = exchange.getResponseBody()) {
                        os.write(data);
                    }
                    exchange.close();
                }
            }
            return;
        }

        if (path.equals("/api/records") &&
            "GET".equals(exchange.getRequestMethod())) {

            StringBuilder json = new StringBuilder("[");

            try (Connection c = connect();
                 Statement s = c.createStatement();
                 ResultSet r = s.executeQuery(
                     "SELECT * FROM Weather_Observation ORDER BY Observation_ID")) {

                boolean first = true;

                while (r.next()) {
                    if (!first) {
                        json.append(',');
                    }
                    first = false;

                    json.append('{')
                        .append("\"id\":").append(r.getInt("Observation_ID"))
                        .append(",\"station\":").append(r.getInt("Station_ID"))
                        .append(",\"temp\":").append(r.getBigDecimal("Temperature"))
                        .append(",\"humidity\":").append(r.getBigDecimal("Humidity"))
                        .append(",\"heat\":").append(r.getBigDecimal("Heat_Index"))
                        .append('}');
                }
            }

            json.append(']');
            byte[] data = json.toString().getBytes(StandardCharsets.UTF_8);
            exchange.getResponseHeaders().set(
                "Content-Type", "application/json; charset=UTF-8"
            );
            exchange.sendResponseHeaders(200, data.length);

            try (OutputStream os = exchange.getResponseBody()) {
                os.write(data);
            }
            exchange.close();
            return;
        }

        if (!"POST".equals(exchange.getRequestMethod())) {
            reply(exchange, 405, "Method not allowed.");
            return;
        }

        String form = readBody(exchange);
        String result;

        try (Connection c = connect()) {
            if (path.equals("/api/add")) {
                String sql =
                    "INSERT INTO Weather_Observation "
                    + "(Station_ID, Temperature, Humidity, Heat_Index) "
                    + "VALUES (?, ?, ?, ?)";

                try (PreparedStatement p = c.prepareStatement(sql)) {
                    p.setInt(1, Integer.parseInt(getFormValue(form, "station")));
                    p.setBigDecimal(2, new java.math.BigDecimal(getFormValue(form, "temp")));
                    p.setBigDecimal(3, new java.math.BigDecimal(getFormValue(form, "humidity")));
                    p.setBigDecimal(4, new java.math.BigDecimal(getFormValue(form, "heat")));
                    p.executeUpdate();
                }

                result = "Record added successfully.";

            } else if (path.equals("/api/update")) {
                String sql =
                    "UPDATE Weather_Observation SET Station_ID=?, Temperature=?, "
                    + "Humidity=?, Heat_Index=? WHERE Observation_ID=?";

                int count;

                try (PreparedStatement p = c.prepareStatement(sql)) {
                    p.setInt(1, Integer.parseInt(getFormValue(form, "station")));
                    p.setBigDecimal(2, new java.math.BigDecimal(getFormValue(form, "temp")));
                    p.setBigDecimal(3, new java.math.BigDecimal(getFormValue(form, "humidity")));
                    p.setBigDecimal(4, new java.math.BigDecimal(getFormValue(form, "heat")));
                    p.setInt(5, Integer.parseInt(getFormValue(form, "id")));
                    count = p.executeUpdate();
                }

                result = count > 0
                    ? "Record updated successfully."
                    : "Observation ID not found.";

            } else if (path.equals("/api/delete")) {
                int count;

                try (PreparedStatement p = c.prepareStatement(
                    "DELETE FROM Weather_Observation WHERE Observation_ID=?")) {
                    p.setInt(1, Integer.parseInt(getFormValue(form, "id")));
                    count = p.executeUpdate();
                }

                result = count > 0
                    ? "Record deleted successfully."
                    : "Observation ID not found.";

            } else {
                reply(exchange, 404, "API endpoint not found.");
                return;
            }
        }

        reply(exchange, 200, result);
    }

    static void handle(HttpExchange exchange) throws IOException {
        String path = exchange.getRequestURI().getPath();

        try {
            if (path.startsWith("/api/")) {
                handleApi(exchange);
                return;
            }

            if ("GET".equals(exchange.getRequestMethod())) {
                if ("/favicon.ico".equals(path)) {
                    exchange.sendResponseHeaders(204, -1);
                    exchange.close();
                    return;
                }

                String resourcePath = ("/".equals(path)) ? "/index.html" : path;
                Path frontendFolder = Paths.get("frontend").toAbsolutePath().normalize();
                Path target = frontendFolder.resolve(resourcePath.substring(1)).normalize();

                if (!target.startsWith(frontendFolder) || !Files.isRegularFile(target)) {
                    reply(exchange, 404, "File not found.");
                    return;
                }

                String type = resourcePath.endsWith(".css")
                    ? "text/css"
                    : resourcePath.endsWith(".js")
                        ? "application/javascript"
                        : "text/html";

                byte[] data = Files.readAllBytes(target);
                exchange.getResponseHeaders().set(
                    "Content-Type", type + "; charset=UTF-8"
                );
                exchange.sendResponseHeaders(200, data.length);

                try (OutputStream os = exchange.getResponseBody()) {
                    os.write(data);
                }

                exchange.close();
                return;
            }

            reply(exchange, 405, "Method not allowed.");

        } catch (Exception e) {
            e.printStackTrace();

            try {
                reply(exchange, 500, "Error. Check Java console and MySQL settings.");
            } catch (Exception ignored) {
            }
        }
    }

    public static void main(String[] args) throws Exception {
        try {
            initializeDatabase();
            System.out.println("Database ready: " + DB_NAME);
        } catch (SQLException e) {
            System.err.println(
                "Could not connect to MySQL using USER=" + USER + ", PASSWORD=***"
            );
            System.err.println(
                "Update MYSQL_USER and MYSQL_PASSWORD if your local MySQL server uses different credentials."
            );
            e.printStackTrace();
        }

        HttpServer server = HttpServer.create(new InetSocketAddress(8080), 0);
        server.createContext("/", ClimateServer::handle);
        server.start();

        System.out.println("Server started at http://localhost:8080");
        System.out.println("Close the Java server window to stop the application.");
    }
}
'@

[System.IO.File]::WriteAllText(
    (Join-Path $Backend "ClimateServer.java"),
    $javaSource,
    [System.Text.UTF8Encoding]::new($false)
)

# -------------------------------------------------
# 6. Create database and table
# -------------------------------------------------
Step "Preparing MySQL database"

$MysqlExe = (Get-Command mysql.exe).Source
$previousMysqlPwd = $env:MYSQL_PWD
$env:MYSQL_PWD = $MYSQL_PASSWORD

try {
    & $MysqlExe "--host=$MYSQL_HOST" "--port=$MYSQL_PORT" "--user=$MYSQL_USER" "--connect-timeout=5" -e "SELECT VERSION();"

    if ($LASTEXITCODE -ne 0) {
        throw "MySQL login failed. Check MYSQL_USER/MYSQL_PASSWORD and ensure MySQL Server is running."
    }

    $sql = @"
CREATE DATABASE IF NOT EXISTS $DATABASE_NAME;
USE $DATABASE_NAME;

CREATE TABLE IF NOT EXISTS Weather_Observation (
    Observation_ID INT AUTO_INCREMENT PRIMARY KEY,
    Station_ID INT,
    Temperature DECIMAL(5,2),
    Humidity DECIMAL(5,2),
    Heat_Index DECIMAL(5,2)
);
"@

    $sql | & $MysqlExe "--host=$MYSQL_HOST" "--port=$MYSQL_PORT" "--user=$MYSQL_USER"

    if ($LASTEXITCODE -ne 0) {
        throw "Could not create the database/table."
    }
}
finally {
    $env:MYSQL_PWD = $previousMysqlPwd
}

# -------------------------------------------------
# 7. Compile Java
# -------------------------------------------------
Step "Compiling ClimateServer.java"

Push-Location $ProjectRoot

try {
    & javac.exe -cp ".;mysql-connector-j.jar" "backend\ClimateServer.java"

    if ($LASTEXITCODE -ne 0) {
        throw "Compilation failed. Check the JDK and Connector/J download."
    }
}
finally {
    Pop-Location
}

# -------------------------------------------------
# 8. Start application
# -------------------------------------------------
Step "Starting Climate Monitoring System"

$env:MYSQL_USER = $MYSQL_USER
$env:MYSQL_PASSWORD = $MYSQL_PASSWORD

$javaExe = (Get-Command java.exe).Source
$ClassPath = ".;mysql-connector-j.jar;backend"

Start-Process -FilePath $javaExe `
    -ArgumentList @("-cp", $ClassPath, "ClimateServer") `
    -WorkingDirectory $ProjectRoot

Start-Sleep -Seconds 3
Start-Process "http://localhost:$APP_PORT"

Write-Host "`nSetup finished." -ForegroundColor Green
Write-Host "Project:  $ProjectRoot"
Write-Host "Database: $DATABASE_NAME"
Write-Host "URL:      http://localhost:$APP_PORT"
Write-Host "The Java server runs in a separate window."

```