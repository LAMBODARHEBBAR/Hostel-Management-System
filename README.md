# Hostel Management System

A simple **Hostel Management System** built using **C++** and **MySQL**. The application allows users to reserve hostel beds, check bed availability, and manage hostel information through a console-based interface. The system uses **MySQL database connectivity** to store and update hostel data.

---

## 📸 Screenshot
<img width="638" height="483" alt="Image" src="https://github.com/user-attachments/assets/9e80bf61-3331-483e-a831-5481d21f12d9" />

---

## 🚀 Features

* ✅ Connects C++ application with MySQL database
* ✅ Stores hostel information in MySQL
* ✅ Displays available hostel beds
* ✅ Reserve a hostel bed for a student
* ✅ Automatically decreases available bed count after reservation
* ✅ Displays hostel fee after successful reservation
* ✅ Handles unavailable beds
* ✅ Handles invalid menu input
* ✅ Console-based user interface
* ✅ Uses MySQL C API for database connectivity

---

## 🛠️ Technologies Used

* C++
* MySQL
* MySQL Server
* MySQL C API
* MySQL WorkBench
* GCC / G++
* Windows API
* Visual Studio Code


---

## 📂 Project Structure

```text
Hostel-Management/
│
├── main.cpp
├── main.exe
├── libmysql.dll
├── HostelManagement.png
└── README.md
```



---

## 🗄️ Database Setup

The application uses a MySQL database named `mydb`.

### Create the database

Open **MySQL Workbench** or the **MySQL Command Line Client** and execute:

```sql
CREATE DATABASE mydb;

USE mydb;
```

### Create the hostel table

```sql
CREATE TABLE hostel (
    Name VARCHAR(50),
    Bed INT,
    Fee INT
);
```

### Insert initial hostel information

```sql
INSERT INTO hostel (Name, Bed, Fee)
VALUES ('3star', 2, 5000);
```

The database will contain information similar to:

| Name  | Bed |  Fee |
| ----- | --: | ---: |
| 3star |   2 | 5000 |

---

## ⚙️ MySQL Configuration

The C++ program connects to MySQL using the following configuration:

```cpp
const char* HOST = "localhost";
const char* USER = "root";
const char* PW = "Your Password";
const char* DB = "mydb";
```

Change:

```cpp
"Your Password"
```

to the password created for the MySQL `root` user.



---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/LAMBODARHEBBAR/Hostel-Management-System.git
```

### 2. Navigate to the project folder

```bash
cd Hostel-Management
```

### 3. Make sure MySQL Server is running

Start your **MySQL Server** before running the application.

The program expects:

```text
Host     : localhost
Username : root
Database : mydb
Port     : 3306
```

### 4. Compile the program

On Windows using MinGW/MSYS2 `g++`:

```powershell
g++ main.cpp -I"C:\Program Files\MySQL\MySQL Server 26.7\include" -L"C:\Program Files\MySQL\MySQL Server 26.7\lib" -lmysql -o main.exe
```

> If your MySQL installation is located in a different folder, change the `include` and `lib` paths accordingly.

### 5. Make sure `libmysql.dll` is available

The MySQL DLL must be accessible when running the program.

For example:

```text
Hostel-Management/
│
├── main.exe
├── libmysql.dll
└── main.cpp
```

### 6. Run the application

```powershell
.\main.exe
```

---

## 📖 How It Works

1. The program initializes a MySQL connection.
2. It connects to the `mydb` database using the MySQL `root` user.
3. Hostel information is inserted into the `hostel` table.
4. The application displays the Hostel Management System menu.
5. The user can choose:

   * **Reserve Bed**
   * **Exit**
6. When **Reserve Bed** is selected, the program asks for the student's name.
7. The program retrieves the current number of available beds from MySQL.
8. If a bed is available:

   * The available bed count is decreased by one.
   * The updated value is stored in MySQL.
   * A successful reservation message is displayed.
   * The hostel fee is displayed.
9. If no beds are available, the program displays:

```text
Sorry! No Bed Available
```

---

## 🖥️ Application Flow

```text
Start
  │
  ▼
Initialize MySQL Connection
  │
  ▼
Connect to mydb
  │
  ├── Connection Failed ──► Display Error
  │
  ▼
Display Hostel Management Menu
  │
  ├── 1. Reserve Bed
  │       │
  │       ▼
  │   Enter Student Name
  │       │
  │       ▼
  │   Check Available Beds
  │       │
  │       ├── Beds Available
  │       │       │
  │       │       ▼
  │       │   Decrease Bed Count
  │       │       │
  │       │       ▼
  │       │   Update MySQL
  │       │       │
  │       │       ▼
  │       │   Reservation Successful
  │       │
  │       └── No Beds
  │               │
  │               ▼
  │         No Bed Available
  │
  └── 2. Exit
          │
          ▼
         End
```

---

## 🧩 C++ Concepts Practiced

* Classes and Objects
* Constructors
* Private and Public Access Specifiers
* Getter Functions
* Strings
* `stringstream`
* Loops
* Conditional Statements
* User Input
* Functions
* MySQL Database Connectivity
* SQL Queries
* `MYSQL` connection
* `MYSQL_RES`
* `MYSQL_ROW`
* `mysql_query()`
* `mysql_store_result()`
* `mysql_fetch_row()`
* `mysql_free_result()`
* `mysql_close()`
* Windows `Sleep()`
* Console-based Menu System

---

## 🗃️ SQL Operations Used

The application demonstrates several basic SQL operations.

### INSERT

Hostel information is inserted into the database:

```sql
INSERT INTO hostel(Name, Bed, Fee)
VALUES ('3star', '2', '5000');
```

### SELECT

The application checks the available beds:

```sql
SELECT Bed
FROM hostel
WHERE Name = '3star';
```

### UPDATE

After reserving a bed, the available bed count is updated:

```sql
UPDATE hostel
SET Bed = '1'
WHERE Name = '3star';
```

---

## 🔐 Database Connectivity

The program uses the **MySQL C API** to communicate with the MySQL Server.

The connection is established using:

```cpp
mysql_real_connect(
    conn,
    HOST,
    USER,
    PW,
    DB,
    3306,
    NULL,
    0
);
```

The application then sends SQL commands using:

```cpp
mysql_query(conn, query);
```

The result of a `SELECT` query is obtained using:

```cpp
mysql_store_result(conn);
```

and individual rows are accessed using:

```cpp
mysql_fetch_row(res);
```

---




