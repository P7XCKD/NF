```powershell
# XP8 - Climate Monitoring System
# Run in a normal PowerShell window. No administrator privileges requested.

$ErrorActionPreference = "Stop"

# ================= USER SETTINGS =================
$MYSQL_HOST = "localhost"
$MYSQL_PORT = 3306
$MYSQL_USER = "root"
$MYSQL_PASSWORD = "root"
$DATABASE_NAME = "climate_form_db"
$APP_PORT = 8080

# The supplied MySQL CDN URL is tried first.
$CONNECTOR_VERSION = "26.10.0"
$MAVEN_FALLBACK_VERSION = "9.5.0"
# =================================================

function Step($message) {
    Write-Host "`n==== $message ====" -ForegroundColor Cyan
}

# Check required commands
if (-not (Get-Command mysql.exe -ErrorAction SilentlyContinue)) {
    throw "mysql.exe not found in PATH. Add the MySQL Server bin folder to PATH."
}

if (-not (Get-Command javac.exe -ErrorAction SilentlyContinue)) {
    throw "javac.exe not found. Install a JDK and add its bin folder to PATH."
}

if (-not (Get-Command java.exe -ErrorAction SilentlyContinue)) {
    throw "java.exe not found in PATH."
}

$ProjectRoot = Join-Path (Get-Location) "climate-app"
$Backend = Join-Path $ProjectRoot "backend"
$Frontend = Join-Path $ProjectRoot "frontend"
$Lib = Join-Path $ProjectRoot "lib"

New-Item -ItemType Directory -Force -Path $Backend, $Frontend, $Lib | Out-Null

# -------------------------------------------------
# 1. Download MySQL Connector/J
# -------------------------------------------------
Step "Downloading MySQL Connector/J"

$ConnectorJar = $null
$CdnArchive = Join-Path $ProjectRoot "connector.tar.gz"
$ExtractFolder = Join-Path $ProjectRoot "connector-extracted"

# Try the CDN URL supplied by you first.
try {
    $CdnUrl = "https://cdn.mysql.com//Downloads/Connector-J/mysql-connector-j-$CONNECTOR_VERSION.tar.gz"

    Write-Host "Trying MySQL CDN: $CdnUrl"
    Invoke-WebRequest -Uri $CdnUrl -OutFile $CdnArchive

    if ((Get-Item $CdnArchive).Length -lt 100000) {
        throw "Downloaded archive is unexpectedly small."
    }

    if (-not (Get-Command tar.exe -ErrorAction SilentlyContinue)) {
        throw "tar.exe is unavailable on this computer."
    }

    New-Item -ItemType Directory -Force -Path $ExtractFolder | Out-Null

    & tar.exe -xzf $CdnArchive -C $ExtractFolder

    if ($LASTEXITCODE -ne 0) {
        throw "Could not extract the downloaded archive."
    }

    $FoundJar = Get-ChildItem $ExtractFolder -Filter "mysql-connector-j-*.jar" -Recurse |
        Select-Object -First 1

    if (-not $FoundJar) {
        throw "No JDBC JAR was found in the extracted archive."
    }

    $ConnectorJar = Join-Path $Lib $FoundJar.Name
    Copy-Item $FoundJar.FullName $ConnectorJar -Force

    Write-Host "MySQL CDN download succeeded." -ForegroundColor Green
}
catch {
    Write-Warning "MySQL CDN download failed: $($_.Exception.Message)"
}

# If CDN download failed, try Maven Central.
if (-not $ConnectorJar -or -not (Test-Path $ConnectorJar)) {
    Step "Trying Maven Central fallback"

    $ConnectorJar = Join-Path $Lib "mysql-connector-j-$MAVEN_FALLBACK_VERSION.jar"
    $MavenUrl = "https://repo.maven.apache.org/maven2/com/mysql/mysql-connector-j/$MAVEN_FALLBACK_VERSION/mysql-connector-j-$MAVEN_FALLBACK_VERSION.jar"

    try {
        Invoke-WebRequest -Uri $MavenUrl -OutFile $ConnectorJar

        if ((Get-Item $ConnectorJar).Length -lt 100000) {
            throw "Downloaded JAR is unexpectedly small."
        }

        Write-Host "Maven Central download succeeded." -ForegroundColor Green
    }
    catch {
        throw "Both Connector/J downloads failed. Check internet access or obtain the JDBC JAR from an approved source. Details: $($_.Exception.Message)"
    }
}

Write-Host "Using JDBC driver: $ConnectorJar"

# -------------------------------------------------
# 2. Create frontend
# -------------------------------------------------
Step "Creating frontend"

@'
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
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
  <section>
    <h2>Add Weather Record</h2>
    <form id="addForm">
      <input name="station" type="number" placeholder="Station ID" required>
      <input name="temp" type="number" step="0.01" placeholder="Temperature" required>
      <input name="humidity" type="number" min="0" max="100" step="0.01" placeholder="Humidity (%)" required>
      <input name="heat" type="number" step="0.01" placeholder="Heat Index" required>
      <button>Add Record</button>
    </form>
  </section>

  <section>
    <h2>Update Weather Record</h2>
    <form id="lookupForm">
      <input name="id" type="number" min="1" placeholder="Observation ID" required>
      <button>Load Record</button>
    </form>
    <p id="updateMessage"></p>
    <form id="updateForm" hidden>
      <input name="id" type="hidden">
      <input name="station" type="number" placeholder="Station ID" required>
      <input name="temp" type="number" step="0.01" placeholder="Temperature" required>
      <input name="humidity" type="number" min="0" max="100" step="0.01" placeholder="Humidity (%)" required>
      <input name="heat" type="number" step="0.01" placeholder="Heat Index" required>
      <button>Update Record</button>
    </form>
  </section>

  <section>
    <h2>Delete Weather Record</h2>
    <form id="deleteForm">
      <input name="id" type="number" min="1" placeholder="Observation ID" required>
      <button class="delete">Delete Record</button>
    </form>
  </section>

  <section>
    <h2>Weather Records</h2>
    <p id="message">Loading records...</p>
    <div class="table-container">
      <table>
        <thead>
          <tr><th>ID</th><th>Station</th><th>Temperature</th><th>Humidity</th><th>Heat Index</th></tr>
        </thead>
        <tbody id="records"></tbody>
      </table>
    </div>
    <button type="button" id="refreshBtn">Refresh Records</button>
  </section>
</main>
</body>
</html>
'@ | Set-Content -Encoding UTF8 (Join-Path $Frontend "index.html")

@'
* { box-sizing: border-box; }
body { margin: 0; font-family: Arial, sans-serif; background: #f1f5f9; color: #1e293b; }
header { background: #176b45; color: white; text-align: center; padding: 24px; }
header h1 { margin: 0 0 8px; }
main { max-width: 1000px; margin: 24px auto; padding: 0 15px; }
section { background: white; padding: 20px; margin-bottom: 18px; border-radius: 10px; box-shadow: 0 3px 12px #0001; }
h2 { margin-top: 0; color: #176b45; }
form { display: flex; flex-wrap: wrap; gap: 10px; }
input { flex: 1 1 170px; min-width: 0; padding: 11px; border: 1px solid #cbd5e1; border-radius: 5px; }
button { padding: 11px 16px; background: #218c5a; color: white; border: 0; border-radius: 5px; cursor: pointer; }
button:hover { background: #176b45; }
.delete { background: #c0392b; }
.table-container { overflow-x: auto; }
table { width: 100%; border-collapse: collapse; margin: 14px 0; }
th, td { padding: 10px; border: 1px solid #dbe2ea; text-align: left; }
th { background: #e5f4ec; }
@media (max-width: 600px) {
  header h1 { font-size: 22px; }
  section { padding: 14px; }
  form button { width: 100%; }
}
'@ | Set-Content -Encoding UTF8 (Join-Path $Frontend "style.css")

@'
const message = document.querySelector("#message");
const records = document.querySelector("#records");
const updateForm = document.querySelector("#updateForm");
const updateMessage = document.querySelector("#updateMessage");

async function loadRecords() {
  try {
    const response = await fetch("/api/records");
    if (!response.ok) throw new Error();
    const data = await response.json();

    records.replaceChildren();

    data.forEach(item => {
      const tr = document.createElement("tr");

      [item.id, item.station, item.temp, item.humidity, item.heat].forEach(value => {
        const td = document.createElement("td");
        td.textContent = value ?? "";
        tr.appendChild(td);
      });

      records.appendChild(tr);
    });

    message.textContent = `${data.length} record(s) found.`;
  } catch {
    message.textContent = "Unable to load records. Check Java and MySQL.";
  }
}

function bindForm(formId, endpoint) {
  const form = document.getElementById(formId);

  form.addEventListener("submit", async event => {
    event.preventDefault();

    try {
      const response = await fetch("/api/" + endpoint, {
        method: "POST",
        body: new URLSearchParams(new FormData(form))
      });

      const result = await response.text();
      message.textContent = result;

      if (response.ok) {
        form.reset();

        if (formId === "updateForm") {
          updateForm.hidden = true;
          updateMessage.textContent = "";
        }

        await loadRecords();
      }
    } catch {
      message.textContent = "Request failed. Check the server.";
    }
  });
}

bindForm("addForm", "add");
bindForm("updateForm", "update");
bindForm("deleteForm", "delete");

document.querySelector("#refreshBtn").addEventListener("click", loadRecords);

document.querySelector("#lookupForm").addEventListener("submit", async event => {
  event.preventDefault();
  updateForm.hidden = true;

  const id = new FormData(event.currentTarget).get("id");

  try {
    const response = await fetch("/api/records/" + encodeURIComponent(id));

    if (!response.ok) {
      updateMessage.textContent = "Observation ID not found.";
      return;
    }

    const item = await response.json();

    Object.entries({
      id: item.id,
      station: item.station,
      temp: item.temp,
      humidity: item.humidity,
      heat: item.heat
    }).forEach(([key, value]) => {
      updateForm.elements.namedItem(key).value = value;
    });

    updateForm.hidden = false;
    updateMessage.textContent = "Editing observation " + item.id + ".";
  } catch {
    updateMessage.textContent = "Could not load record.";
  }
});

loadRecords();
'@ | Set-Content -Encoding UTF8 (Join-Path $Frontend "app.js")

# -------------------------------------------------
# 3. Create Java backend
# -------------------------------------------------
Step "Creating Java JDBC backend"

@'
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpServer;
import java.io.*;
import java.net.*;
import java.nio.charset.StandardCharsets;
import java.nio.file.*;
import java.sql.*;
import java.math.BigDecimal;

public class ClimateServer {
    static String db = System.getenv().getOrDefault("MYSQL_DATABASE", "climate_form_db");
    static String host = System.getenv().getOrDefault("MYSQL_HOST", "localhost");
    static String port = System.getenv().getOrDefault("MYSQL_PORT", "3306");
    static String user = System.getenv().getOrDefault("MYSQL_USER", "root");
    static String pass = System.getenv().getOrDefault("MYSQL_PASSWORD", "root");

    static Connection connect() throws SQLException {
        return DriverManager.getConnection(
            "jdbc:mysql://" + host + ":" + port + "/" + db, user, pass
        );
    }

    static String val(String body, String key) {
        for (String part : body.split("&")) {
            String[] pair = part.split("=", 2);
            if (URLDecoder.decode(pair[0], StandardCharsets.UTF_8).equals(key)) {
                return URLDecoder.decode(pair.length > 1 ? pair[1] : "", StandardCharsets.UTF_8);
            }
        }
        return "";
    }

    static void send(HttpExchange x, int status, String body, String type) throws IOException {
        byte[] bytes = body.getBytes(StandardCharsets.UTF_8);
        x.getResponseHeaders().set("Content-Type", type + "; charset=UTF-8");
        x.sendResponseHeaders(status, bytes.length);
        try (OutputStream out = x.getResponseBody()) {
            out.write(bytes);
        }
        x.close();
    }

    static void text(HttpExchange x, int status, String body) throws IOException {
        send(x, status, body, "text/plain");
    }

    static void json(HttpExchange x, int status, String body) throws IOException {
        send(x, status, body, "application/json");
    }

    static String record(ResultSet r) throws SQLException {
        return "{\"id\":" + r.getInt("Observation_ID")
            + ",\"station\":" + r.getInt("Station_ID")
            + ",\"temp\":" + r.getBigDecimal("Temperature")
            + ",\"humidity\":" + r.getBigDecimal("Humidity")
            + ",\"heat\":" + r.getBigDecimal("Heat_Index") + "}";
    }

    static void api(HttpExchange x) throws Exception {
        String path = x.getRequestURI().getPath();
        String method = x.getRequestMethod();

        if (method.equals("GET") && path.equals("/api/records")) {
            StringBuilder result = new StringBuilder("[");
            try (Connection c = connect();
                 Statement s = c.createStatement();
                 ResultSet r = s.executeQuery(
                     "SELECT * FROM Weather_Observation ORDER BY Observation_ID")) {
                boolean first = true;
                while (r.next()) {
                    if (!first) result.append(",");
                    first = false;
                    result.append(record(r));
                }
            }
            json(x, 200, result.append("]").toString());
            return;
        }

        if (method.equals("GET") && path.matches("/api/records/\\d+")) {
            try (Connection c = connect();
                 PreparedStatement s = c.prepareStatement(
                     "SELECT * FROM Weather_Observation WHERE Observation_ID=?")) {
                s.setInt(1, Integer.parseInt(path.substring("/api/records/".length())));
                try (ResultSet r = s.executeQuery()) {
                    if (!r.next()) text(x, 404, "Observation ID not found.");
                    else json(x, 200, record(r));
                }
            }
            return;
        }

        if (!method.equals("POST")) {
            text(x, 405, "Method not allowed.");
            return;
        }

        String body = new String(x.getRequestBody().readAllBytes(), StandardCharsets.UTF_8);
        String result;

        try (Connection c = connect()) {
            if (path.equals("/api/add")) {
                try (PreparedStatement s = c.prepareStatement(
                    "INSERT INTO Weather_Observation(Station_ID,Temperature,Humidity,Heat_Index) VALUES(?,?,?,?)")) {
                    s.setInt(1, Integer.parseInt(val(body, "station")));
                    s.setBigDecimal(2, new BigDecimal(val(body, "temp")));
                    s.setBigDecimal(3, new BigDecimal(val(body, "humidity")));
                    s.setBigDecimal(4, new BigDecimal(val(body, "heat")));
                    s.executeUpdate();
                }
                result = "Record added successfully.";
            } else if (path.equals("/api/update")) {
                int count;
                try (PreparedStatement s = c.prepareStatement(
                    "UPDATE Weather_Observation SET Station_ID=?,Temperature=?,Humidity=?,Heat_Index=? WHERE Observation_ID=?")) {
                    s.setInt(1, Integer.parseInt(val(body, "station")));
                    s.setBigDecimal(2, new BigDecimal(val(body, "temp")));
                    s.setBigDecimal(3, new BigDecimal(val(body, "humidity")));
                    s.setBigDecimal(4, new BigDecimal(val(body, "heat")));
                    s.setInt(5, Integer.parseInt(val(body, "id")));
                    count = s.executeUpdate();
                }
                result = count > 0 ? "Record updated successfully." : "Observation ID not found.";
            } else if (path.equals("/api/delete")) {
                int count;
                try (PreparedStatement s = c.prepareStatement(
                    "DELETE FROM Weather_Observation WHERE Observation_ID=?")) {
                    s.setInt(1, Integer.parseInt(val(body, "id")));
                    count = s.executeUpdate();
                }
                result = count > 0 ? "Record deleted successfully." : "Observation ID not found.";
            } else {
                text(x, 404, "API endpoint not found.");
                return;
            }
        }

        text(x, 200, result);
    }

    static void handle(HttpExchange x) throws IOException {
        try {
            String path = x.getRequestURI().getPath();

            if (path.startsWith("/api/")) {
                api(x);
                return;
            }

            if (!x.getRequestMethod().equals("GET")) {
                text(x, 405, "Method not allowed.");
                return;
            }

            String relative = path.equals("/") ? "index.html" : path.substring(1);
            Path root = Paths.get("frontend").toAbsolutePath().normalize();
            Path file = root.resolve(relative).normalize();

            if (!file.startsWith(root) || !Files.isRegularFile(file)) {
                text(x, 404, "File not found.");
                return;
            }

            String type = relative.endsWith(".css") ? "text/css"
                : relative.endsWith(".js") ? "application/javascript" : "text/html";

            send(x, 200, Files.readString(file), type);
        } catch (Exception e) {
            e.printStackTrace();
            try {
                text(x, 500, "Server error. Check the Java console and MySQL settings.");
            } catch (Exception ignored) {}
        }
    }

    public static void main(String[] args) throws Exception {
        try (Connection c = connect(); Statement s = c.createStatement()) {
            s.executeUpdate(
                "CREATE TABLE IF NOT EXISTS Weather_Observation (" +
                "Observation_ID INT AUTO_INCREMENT PRIMARY KEY," +
                "Station_ID INT NOT NULL," +
                "Temperature DECIMAL(5,2) NOT NULL," +
                "Humidity DECIMAL(5,2) NOT NULL," +
                "Heat_Index DECIMAL(5,2) NOT NULL)"
            );
        }

        int appPort = Integer.parseInt(System.getenv().getOrDefault("APP_PORT", "8080"));
        HttpServer server = HttpServer.create(new InetSocketAddress(appPort), 0);
        server.createContext("/", ClimateServer::handle);
        server.start();

        System.out.println("Climate Monitoring System running at http://localhost:" + appPort);
        System.out.println("Close this window to stop the server.");
    }
}
'@ | Set-Content -Encoding UTF8 (Join-Path $Backend "ClimateServer.java")

# Remove UTF-8 BOM to keep javac compatibility on Windows.
$JavaFile = Join-Path $Backend "ClimateServer.java"
$JavaText = Get-Content -Raw $JavaFile
[System.IO.File]::WriteAllText($JavaFile, $JavaText, [System.Text.UTF8Encoding]::new($false))

# -------------------------------------------------
# 4. Create database and sample rows
# -------------------------------------------------
Step "Checking MySQL and creating database"

$MysqlExe = (Get-Command mysql.exe).Source
$PreviousMysqlPwd = $env:MYSQL_PWD
$env:MYSQL_PWD = $MYSQL_PASSWORD

try {
    & $MysqlExe "--host=$MYSQL_HOST" "--port=$MYSQL_PORT" "--user=$MYSQL_USER" "--connect-timeout=5" -e "SELECT VERSION();"

    if ($LASTEXITCODE -ne 0) {
        throw "MySQL login failed. Check the username/password settings and ensure MySQL Server is running."
    }

    "CREATE DATABASE IF NOT EXISTS $DATABASE_NAME;" |
        & $MysqlExe "--host=$MYSQL_HOST" "--port=$MYSQL_PORT" "--user=$MYSQL_USER"

    if ($LASTEXITCODE -ne 0) {
        throw "Could not create database $DATABASE_NAME."
    }

    $Sql = @"
USE $DATABASE_NAME;

CREATE TABLE IF NOT EXISTS Weather_Observation (
    Observation_ID INT AUTO_INCREMENT PRIMARY KEY,
    Station_ID INT NOT NULL,
    Temperature DECIMAL(5,2) NOT NULL,
    Humidity DECIMAL(5,2) NOT NULL,
    Heat_Index DECIMAL(5,2) NOT NULL
);

INSERT INTO Weather_Observation (Station_ID, Temperature, Humidity, Heat_Index)
SELECT 101, 29.50, 70.00, 33.20
WHERE NOT EXISTS (SELECT 1 FROM Weather_Observation WHERE Station_ID = 101);

INSERT INTO Weather_Observation (Station_ID, Temperature, Humidity, Heat_Index)
SELECT 102, 31.20, 64.00, 35.10
WHERE NOT EXISTS (SELECT 1 FROM Weather_Observation WHERE Station_ID = 102);

INSERT INTO Weather_Observation (Station_ID, Temperature, Humidity, Heat_Index)
SELECT 103, 27.80, 82.00, 30.40
WHERE NOT EXISTS (SELECT 1 FROM Weather_Observation WHERE Station_ID = 103);

SELECT * FROM Weather_Observation;
"@

    $Sql | & $MysqlExe "--host=$MYSQL_HOST" "--port=$MYSQL_PORT" "--user=$MYSQL_USER"

    if ($LASTEXITCODE -ne 0) {
        throw "Database initialization failed."
    }
}
finally {
    $env:MYSQL_PWD = $PreviousMysqlPwd
}

# -------------------------------------------------
# 5. Compile and launch
# -------------------------------------------------
Step "Compiling Java backend"

Push-Location $ProjectRoot
try {
    & javac.exe -cp $ConnectorJar backend\ClimateServer.java

    if ($LASTEXITCODE -ne 0) {
        throw "Java compilation failed."
    }
}
finally {
    Pop-Location
}

Step "Starting application"

$env:MYSQL_HOST = $MYSQL_HOST
$env:MYSQL_PORT = "$MYSQL_PORT"
$env:MYSQL_USER = $MYSQL_USER
$env:MYSQL_PASSWORD = $MYSQL_PASSWORD
$env:MYSQL_DATABASE = $DATABASE_NAME
$env:APP_PORT = "$APP_PORT"

$ClassPath = "$ConnectorJar;$Backend"

Start-Process -FilePath (Get-Command java.exe).Source `
    -ArgumentList @("-cp", "`"$ClassPath`"", "ClimateServer") `
    -WorkingDirectory $ProjectRoot

Start-Sleep -Seconds 3
Start-Process "http://localhost:$APP_PORT"

Write-Host "`nSetup complete." -ForegroundColor Green
Write-Host "Project:  $ProjectRoot"
Write-Host "Database: $DATABASE_NAME"
Write-Host "Web app:  http://localhost:$APP_PORT"
Write-Host "The Java server runs in a separate window."


```