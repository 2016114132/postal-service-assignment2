# Postal Service System Assignment #2

This project was built with **Node.js**, **TypeScript**, and **PostgreSQL**. It allows you to manage packages, calculate shipping costs, and track package statuses.

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/2016114132/postal-service-assignment2.git
```

```bash
cd postal-service-assignment2
```

### 2. Install Dependencies

```bash
npm install
```

---

## PostgreSQL Database Setup

### A. Install PostgreSQL

Follow the instructions for your OS:

- **Linux**:  
  ```bash
  sudo apt install postgresql
  ```

- **macOS (Homebrew)**:  
  ```bash
  brew install postgresql@17
  ```

Then verify the installation:
```bash
psql --version
```

### B. Create Database and User

Login to PostgreSQL:

- **Linux**:  
  ```bash
  sudo -u postgres psql
  ```

- **macOS**:  
  ```bash
  psql -U postgres
  ```

Then run the following commands:

- Create a new database
  ```sql
  CREATE DATABASE "postal-service2-db";
  ```
- Create a new user/role (Skip this step if already exists)
  ```sql
  CREATE ROLE developer WITH LOGIN PASSWORD 'root';
  ```

- Grant privileges
  ```sql
  ALTER DATABASE "postal-service2-db" OWNER TO developer;
  ```
  ```sql
  GRANT CREATE ON DATABASE "postal-service2-db" TO developer;
  ```

Exit with:
```sql
\q
```

---

### ✅ C. Create the Packages Table

Login with the new user:
```bash
psql --host=localhost --dbname=postal-service2-db --username=developer
```

Then run:
```sql
CREATE TABLE packages (
    "ID" SERIAL PRIMARY KEY,
    "SenderName" VARCHAR(255),
    "ReceiverName" VARCHAR(255),
    "SenderAddress" VARCHAR(255),
    "ReceiverAddress" VARCHAR(255),
    "Weight" DECIMAL(10,2),
    "CostPerUnitWeight" DECIMAL(10,2),
    "Status" VARCHAR(255),
    "TrackingNumber" VARCHAR(255),
    "FlatFee" DECIMAL(10,2),
    "ShippingMethod" VARCHAR(255)
);
```

Exit with:
```sql
\q
```

## Running the App
**Note:** Make sure you are inside the application's folder.

Start the application:
```bash
npm start
```

Then open:  
[http://localhost:3000](http://localhost:3000)

---
