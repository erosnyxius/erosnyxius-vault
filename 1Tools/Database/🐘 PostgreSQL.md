`Database`

An organized collection of structured information, or data, typically stored electronically in a computer system

`DBMS`
A database is usually controlled by a database management system (DBMS)

![[DBMS.jpg]]

`RDBMS`
A type of database management system that stores data in a structured format using rows and columns (tabular)

![[DMBS-RDBMS.webp]]

`SQL`
Structured Query Language is a standard language for storing, manipulating and retrieving data in databases
### `📘 Phase 1 — Fundamentals`

#### Database vs Schema vs Table
* **Database**: Top-level container that holds schemas.
* **Schema**: Namespace within a database that groups tables and other objects.
* **Table**: Stores actual data in rows and columns inside a schema.

```
PostgreSQL Server
└── Database (e.g., mydb)
    └── Schema (e.g., public, hr)
        └── Table (e.g., employees, orders)
```

#### `List & Create Database`

- To Write Query → Go To Databases → Choose Your Database
- Click "Query Tool"
- Uppercase or Lowercase It Does Not Matter Just Ensure  ';' 

1. List down **existing Databases**
```sql
SELECT datname FROM pg_database;
```

```cmd
\l

Clear Screen
\! cls

আসলে \! দিয়ে Terminal Command Use করা যায় যার জন্য যেটা !!!
\! clear 
\! ls 
... 
```

2. Creating a **new Database**
```sql
CREATE DATABASE <db_name>;
```

Or Use pgAdmin 

3. **Change Database** CLI & Connection Info
```cmd
\c <db_name>;

\conninfo
```

4. Delete a **Database**
```sql
DROP DATABASE <db_name>;
```

#### `Table Creating, Data Inserting, Data Updating & Data Deleting`

**Creating a Table**
```sql
CREATE TABLE table_name (
    col_name DATA_TYPE [CONSTRAINTS],
    col_name DATA_TYPE [CONSTRAINTS],
    col_name DATA_TYPE [CONSTRAINTS],
    ...
);
-- Column Name Capital Wise লিখতে গেলে বা Select করতে "" Use করবো
-- String এর জন্য '' Use করবো
```

After Execution → Return Successful ! 
Verify → Schemas → Public → Tables → TableName → Columns!

```cmd
\c <db_name>;

\d table_name;

\dt = Shows All Tables !
```

**Inserting Data Into A Table**

```sql
INSERT INTO table_name (col_name, col_name, col_name) VALUES 
(value1, value2, value3);
```

**Reading Data From A Table**

```sql
SELECT * FROM table_name; -- (FOR ALL COLUMN)

SELECT col_name,col_name FROM table_name; -- (SPECIFIC)
```

**Updating Data From A Table**

```sql
UPDATE table_name
	SET column_name1 = Value1, column_name2 = Value2..  
	WHERE CONDITION;
```

**Deleting Data From A Table**

```sql
DELETE FROM table_name
WHERE CONDITION;
```

**Deleting A Table**

```sql
DROP TABLE IF EXISTS table_name;
```

**Delete All Data But Keep The Table Structure**

```sql
TRUNCATE TABLE table_name;
```

**To Delete A  Specific Column From A Table**

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

### `📘 Phase 2 — Data Types and Constraint`

`Data Types`

Data Type is an attribute that specifies the type of data
- Numeric - INT, DOUBLE, FLOAT, DECIMAL
- String - VARCHAR, VARCHAR(LIMIT) 
- Date - DATE
- Boolean - BOOLEAN (TRUE, FALSE)

`Constraint`

**A constraint in PostgreSQL is a rule applied to a column** 
#### PRIMARY KEY
* **Syntax:** `column_name DATA_TYPE PRIMARY KEY`
* **Purpose:** Unique identifier for each row.
* **Notes:**
  * Automatically `NOT NULL + UNIQUE`.
  * Only **one PK per table**.
* **When to use:** IDs (`id`, `user_id`)

```sql
-- যখন Unique হবে প্রত্যেক Row তখন PRIMARY KEY Use করবো !!
CREATE TABLE users (
    id SERIAL PRIMARY KEY,  
    username VARCHAR(50)
);
```

(AUTO_INCREMENT = Serially ID Maintain করার জন্য SERIAL)

#### NOT NULL
* **Syntax:** `column_name DATA_TYPE NOT NULL`
* **Purpose:** Value must always be provided.
* **When to use:** Required fields (`username`, `email`)

```sql 
-- যখন Data Required তখন NOT NULL Use করবো !!
CREATE TABLE accounts (
    username VARCHAR(50) NOT NULL,  -- must always have a value
    email VARCHAR(255) NOT NULL
);
```

#### UNIQUE
* **Syntax:** `column_name DATA_TYPE UNIQUE`
* **Purpose:** No duplicate values allowed.
* **When to use:** Emails, usernames
* **Tip:** Can combine with `NOT NULL` for extra safety.

```sql
-- যখন Duplicate Data Allow না তখন UNIQUE Use করবো !!
CREATE TABLE users (
    email VARCHAR(255) UNIQUE,           
    username VARCHAR(50) NOT NULL UNIQUE 
);

-- একই Column এর জন্য Multiple Constrain Use করা যাবে ! 
```

#### DEFAULT
* **Syntax:** `column_name DATA_TYPE DEFAULT value`
* **Purpose:** If no value is provided, DB assigns this.
* **When to use:** Booleans, numeric counters, arrays, timestamps.

```sql
-- যখন Default Data Required তখন DEFAULT Use করবো !!
CREATE TABLE users (
    is_verified BOOLEAN DEFAULT false,                          
    created_at TIMESTAMPTZ DEFAULT NOW()            
);
```

#### CHECK
* **Syntax:** `column_name DATA_TYPE CHECK(condition)`
* **Purpose:** Validate values before inserting.
* **When to use:** Age >= 0, price >= 0, enum-like numbers.

```sql
-- যখন Condition Check করার দরকার তখন CHECK() Use করবো !!
CREATE TABLE users (
    age INT CHECK (age >= 0),                 -- Age Must Be Positive
    price NUMERIC(10,2) CHECK (price >= 0)    -- Price Must Be >= 0
);
```

#### FOREIGN KEY
* **Syntax:** `column_name DATA_TYPE REFERENCES other_table(column)`
* **Purpose:** Link to another table, maintain relational integrity.
* **Optional:** `ON DELETE CASCADE` → delete dependent rows automatically.
* **When to use:** Relations like `user_id` in posts, orders, comments.

```sql
-- যখন একটা Table Column এর সাথে অন্য Table এর Column Link করার দরকার তখন REFERENCES Use করবো !!
CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id) ON DELETE CASCADE,  -- link to users table
    title TEXT NOT NULL
);
```

#### UUID
* **Syntax:** `column_name UUID DEFAULT uuid_generate_v4()`
* **Purpose:** Unique ID, globally safe.
* **When to use:** Public APIs, distributed systems, secure IDs.

```sql
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- UUID Generate করা একদম Specific User এর জন্য ! 

CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),    ID
    username VARCHAR(50) NOT NULL
);
```

#### ENUM
* **Purpose:** Only allow predefined values.
* **When to use:** Statuses, roles, types.

```sql
CREATE TYPE user_status AS ENUM ('active', 'inactive', 'banned');

CREATE TABLE users (
    username VARCHAR(50) NOT NULL,
    status user_status DEFAULT 'active'
);
```

#### ARRAY
* **Syntax:** `column_name DATA_TYPE[] DEFAULT ARRAY[...]`
* **Purpose:** Store lists directly in a column.
* **When to use:** Tags, roles, categories.

```sql
-- যখন List আকারে Store করার দরকার তখন Array Use করবো !!
CREATE TABLE users (
    username VARCHAR(50) NOT NULL,
    roles TEXT[] DEFAULT ARRAY['user'],   -- store list of roles
    tags TEXT[] DEFAULT ARRAY['new']      -- store list of tags
);
```

#### Timestamps
* Always track `created_at` and `updated_at`
* **Syntax:**
```sql
-- যখন Current Date Store করার দরকার TIMESTAMPTZ DEFAULT NOW() করবো!!
created_at TIMESTAMPTZ DEFAULT NOW()
updated_at TIMESTAMPTZ DEFAULT NOW()
```


#### Task - 1 (Simple Clean Pic)
![[Task -1.png]]

**Condition**
ID = Unique PRIMARY KEY তাই রাখবো আবার Serial Maintain হচ্ছে তাই AUTO_INCREMENT করবো ! 
EMAIL = Unique PRIMARY KEY + No Duplicates
OVERALL No Column Should Not Be Null 
Salary = Use DEFAULT VALUE 
Hire Date = Use Date Data Type 

| Feature          | PRIMARY KEY       | UNIQUE             |
| ---------------- | ----------------- | ------------------ |
| Uniqueness       | ✅ Yes             | ✅ Yes              |
| Allows NULL      | ❌ No              | ✅ Yes (1 or more)  |
| Count per table  | 1 only            | Multiple allowed   |
| Purpose          | Identify a record | Enforce uniqueness |

**Solution**

Creating Employee Table

```sql
CREATE TABLE "Employees"
(
	"Employee ID" SERIAL PRIMARY KEY,
	"FirstName" VARCHAR(50) NOT NULL,
	"LastName" VARCHAR(50) NOT NULL,
	"Email" VARCHAR(50) NOT NULL UNIQUE,
	"Dept." VARCHAR(50),
	"Salary" DECIMAL(10,2) DEFAULT 30000.00,
	"HireDate" DATE NOT NULL DEFAULT CURRENT_DATE
);
-- দেখার জন্য Use pgAdmin or \c db_name; তারপর \d table_name;
```

To Delete All Rows And Reset The `Employee ID` Counter 

```sql
TRUNCATE TABLE "Employees" RESTART IDENTITY;
```

Final Code To Insert Data Into Employees Table

```sql
INSERT INTO "Employees" ("Employee ID", "FirstName", "LastName", "Email", "Dept.", "Salary", "HireDate")
VALUES
(1, 'Mahtabul', 'Shourav', 'mahtabulsourav@gmail.com', 'AI', 40000.00, '2025-04-23'),
(2, 'Ayesha', 'Khan', 'ayesha.khan@gmail.com', 'Data', 42000.00, '2025-03-15'),
(3, 'Rafi', 'Hossain', 'rafi.hossain@gmail.com', 'Web', 38500.00, '2025-01-10'),
(4, 'Nusrat', 'Jahan', 'nusrat.jahan@gmail.com', 'AI', 41000.00, '2025-06-01'),
(5, 'Farhan', 'Islam', 'farhan.islam@gmail.com', 'Cloud', 43000.00, '2025-02-20'),
(6, 'Mehedi', 'Hasan', 'mehedi.hasan@gmail.com', 'DevOps', 39500.00, '2025-04-12'),
(7, 'Tania', 'Ahmed', 'tania.ahmed@gmail.com', 'UI/UX', 37000.00, '2025-05-05'),
(8, 'Asif', 'Rahman', 'asif.rahman@gmail.com', 'Security', 45000.00, '2025-01-25'),
(9, 'Sadia', 'Nahar', 'sadia.nahar@gmail.com', 'ML', 40500.00, '2025-03-30'),
(10, 'Junaid', 'Alam', 'junaid.alam@gmail.com', 'AI', 44000.00, '2025-06-10');
```
### 📘 Phase 3 — Data Refining

#### Clauses
- WHERE
- DISTINCT
- ORDER BY
- LIMIT
- LIKE

| **Clause** | **Used For**                     | **Used In**                  |
| ---------- | -------------------------------- | ---------------------------- |
| `WHERE`    | Filter rows based on condition   | `SELECT`, `UPDATE`, `DELETE` |
| `DISTINCT` | Remove duplicate values          | `SELECT`                     |
| `ORDER BY` | Sort results (ASC/DESC)          | `SELECT`                     |
| `LIMIT`    | Restrict number of returned rows | `SELECT`                     |
| `LIKE`     | Pattern matching in text         | `WHERE`                      |

#### WHERE

```sql
-- Fetch Specific Rows
-- SELECT * FROM table_name
-- WHERE condition;


-- একজনের Details বের করা PRIMARY KEY = Value Use করে
-- SELECT * FROM employees
-- WHERE emp_id = 5;


-- Specific Details বের করা Specific_Column = Value করে
-- SELECT * FROM employees
-- WHERE dept = 'AI';

-- Condition Operator Use করে
-- SELECT * FROM employees
-- WHERE salary >= 40000;


-- দুইটা Condition থাকলে Logical Operator Use করবো

-- OR
-- SELECT * FROM employees
-- WHERE dept = 'AI' or dept = 'ML';

-- SELECT * FROM table_name
-- WHERE Condition1 or Condition2

-- AND
-- SELECT * FROM employees
-- WHERE dept = 'AI' and salary > 42000;

-- SELECT * FROM table_name
-- WHERE Condition1 and Condition2

-- NOT
-- SELECT * FROM employees
-- WHERE not dept = 'AI';

-- SELECT * FROM table_name
-- WHERE not Condition


-- যদি তিনটা বা তার বেশি Conditions থাকে তখন In, Not In Use করবো
SELECT * FROM employees
WHERE dept IN ('AI', 'ML', 'Cloud');
-- https://youtu.be/cnzka7kF5Zk?t=5282
```