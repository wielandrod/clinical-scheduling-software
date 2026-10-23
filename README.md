# ACME Vet Clinic | Clinical Scheduling System

A full-stack web application designed to manage employee scheduling, staffing, and time-off requests for a 24-hour mock veterinary clinic.

## Tech Stack

- **Frontend:** React, Vite
- **Backend:** Java, Spring Boot, Maven
- **Database:** PostgreSQL, JDBC
- **Architecture:** RESTful APIs, service-layer database access

## Key Features

- **Automated Scheduling:** Generates 14-day schedules while enforcing minimum rest periods, staff coverage, and weekly shift restrictions.
- **Employee Management:** Supports administrator-controlled doctor and technician account creation, password resets, and removal.
- **Shift & Time-Off Requests:** Processes employee requests with immediate approval or denial based on scheduling constraints and available leave balances.
- **Role-Based Access:** Provides separate administrator and employee interfaces for managing and viewing schedules.
- **Schedule Visualization:** Displays assigned shifts, working hours, and coworkers across a two-week period.

## My Contributions

As part of this collaborative university software engineering/database design project, I contributed primarily to backend development and database architecture.

- Designed the entity-relationship diagram and relational database schema, including SQL data definitions.
- Implemented JDBC-backed database service functions for retrieving and processing scheduling requests.
- Developed RESTful API endpoints in Spring Boot for employee time-off and work-shift request information.

## Application Startup

### Prerequisites

- **JDK 25**, with `JAVA_HOME` pointing to the JDK installation.
- **Node.js 20 or later** and **npm**.
- Access to the configured **PostgreSQL database**.
- An internet connection to download dependencies on the first run.

Maven is included through the Maven Wrapper; a separate Maven installation is unnecessary.

### 1. Configure the Database

The database connection is configured in:

```text
backend/src/main/resources/application.properties
```

Ensure the configured database is reachable and the connection details are correct. If using a different database, update these properties:

```properties
spring.datasource.url=jdbc:postgresql://HOST:5432/DATABASE
spring.datasource.username=USERNAME
spring.datasource.password=PASSWORD
```

For a new, empty database, run `SubmissionMaterials/TableCreation.sql` using a PostgreSQL client. The script creates the tables but does not create accounts. Create the initial administrator account with:

```sql
INSERT INTO employees (ename, euser, epass, etype)
VALUES ('Administrator', 'admin', 'admin', 'Admin');
```

Skip initialization if the database already contains the application tables and administrator account.

### 2. Install Frontend Dependencies

From the project root—the directory containing `pom.xml`—run:

```sh
npm --prefix frontend install
```

### 3. Start the Backend

Open a terminal in the project root.

**Windows PowerShell:**

```powershell
.\mvnw.cmd spring-boot:run
```

**macOS/Linux:**

```sh
./mvnw spring-boot:run
```

Wait for Spring Boot to finish starting. The backend runs at `http://localhost:8080`. Keep this terminal open.

### 4. Start the Frontend

Open a second terminal in the project root and run:

```sh
npm run dev:frontend
```

Open **http://localhost:3000** in a browser.

The frontend forwards `/api` requests to the backend on port `8080`. If port `3000` is occupied, use the frontend address printed in the terminal.

### 5. Sign In

For a newly initialized database, use:

- **Username:** `admin`
- **Password:** `admin`

The administrator must change this password on the first login. For an existing database, use its current account credentials.

### Stopping the Application

Press **Ctrl+C** in both terminals.

### Troubleshooting

- **Java compilation errors:** Check that `java -version` reports JDK 25 and that `JAVA_HOME` points to the same installation.
- **Database connection errors:** Verify the PostgreSQL host, credentials, and network access.
- **Missing table errors:** Initialize the database using `SubmissionMaterials/TableCreation.sql`.
- **Login or API errors:** Confirm that the backend is running on port `8080` and can access the database.
  
## Documentation

See the project's user manual for application workflows, employee roles, and scheduling constraints.
