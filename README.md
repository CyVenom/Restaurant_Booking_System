# Restaurant Booking System

## Description

The Restaurant Booking System is a web-based application designed to manage restaurant reservations efficiently. It allows customers to create accounts, book tables, and view their reservations. The system also provides login tracking through a login audit trail.

---

## Database Setup

### SQL Commands to Create Database and User

```sql
CREATE DATABASE RestaurantBookingSystem;
CREATE LOGIN AppUser WITH PASSWORD = 'StrongPassword123';
USE RestaurantBookingSystem;

CREATE USER AppUser FOR LOGIN AppUser;
EXEC sp_addrolemember 'db_owner', 'AppUser';
```

### SQL Commands to Create Tables

#### Customers Table

```sql
CREATE TABLE Customers (
    CustomerID INT IDENTITY(1,1) PRIMARY KEY,
    Username NVARCHAR(50) NOT NULL UNIQUE,
    FullName NVARCHAR(100) NOT NULL,
    Email NVARCHAR(100) NOT NULL UNIQUE,
    Password NVARCHAR(255) NOT NULL,
    CreatedAt DATETIME DEFAULT GETDATE()
);
```

#### Reservations Table

```sql
CREATE TABLE Reservations (
    ReservationID INT IDENTITY(1,1) PRIMARY KEY,
    CustomerID INT NOT NULL FOREIGN KEY REFERENCES Customers(CustomerID),
    ReservationDate DATE NOT NULL,
    ReservationTime TIME NOT NULL,
    NumberOfGuests INT NOT NULL,
    CreatedAt DATETIME DEFAULT GETDATE()
);
```

#### Login Audit Trail Table

```sql
CREATE TABLE LoginAuditTrail (
    LoginID INT IDENTITY(1,1) PRIMARY KEY,
    LoginTime DATETIME NOT NULL
);
```

---

## Server Code (Node.js with Express)

### Install Dependencies

Run the following commands to install required dependencies:

```bash
npm install express body-parser mssql bcryptjs dotenv
npm install -g nodemon
```

### Running the Server

To start the server:

- For production:
  ```bash
  npm start
  ```
- For development:
  ```bash
  npm run dev
  ```

**Note:** Use only one terminal and run either `npm start` or `npm run dev` depending on the environment. Running both commands is not necessary.

---

## Environment Variables

Create a `.env` file in the root directory with the following configuration:

```
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_SERVER=your_db_server
DB_DATABASE=RestaurantBookingSystem2
DB_PORT=1433
```

### Tip: Check SQL Server Name

Before configuring the `.env` file, verify your SQL Server name using the following command in SQL Server Management Studio (SSMS):

```sql
SELECT @@SERVERNAME AS ServerName;
```

---

## Technologies Used

- HTML
- CSS
- JavaScript
- Node.js
- Express.js
- Microsoft SQL Server

---

## Contact Information

For support or feedback, reach out to:

| Name                      | Student ID | Email Address                                                         |
| ------------------------- | ---------- | --------------------------------------------------------------------- |
| Jerry Jeremiah Rao        | 1201101725 | [1201101725@student.mmu.edu.my](mailto:1201101725@student.mmu.edu.my) |
| Sashvin Nair Suresh Kumar | 1211103437 | [1211103437@student.mmu.edu.my](mailto:1211103437@student.mmu.edu.my) |
| 
