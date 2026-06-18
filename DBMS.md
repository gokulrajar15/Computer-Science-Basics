# DBMS (Database Management System)

---

## 📌 Index

1. [What is a DBMS?](#1-what-is-a-dbms)
2. [Why Do We Need a DBMS?](#2-why-do-we-need-a-dbms)
3. [Types of DBMS](#3-types-of-dbms)
4. [Database Models](#4-database-models)
5. [Keys in DBMS](#5-keys-in-dbms)
6. [SQL Basics](#6-sql-basics)
7. [Normalization](#7-normalization)
8. [Denormalization](#8-denormalization)
9. [Joins](#9-joins)
10. [ACID Properties](#10-acid-properties)
11. [Indexing](#11-indexing)
12. [Transactions & Concurrency Control](#12-transactions--concurrency-control)
13. [ER Model (Entity-Relationship)](#13-er-model-entity-relationship)

---

## 1. What is a DBMS?

A **Database Management System (DBMS)** is software that lets you **store, retrieve, update, and manage** data in a structured way. It acts as an **interface** between users/applications and the database.

**Think of it like this:**
- Without DBMS → Product info, user details, orders all in random Excel files (chaos!)
- With DBMS → Everything organized in structured tables, like Amazon's backend

**Popular DBMS examples:** MySQL, PostgreSQL, Oracle, MongoDB, SQL Server

```
Real-life analogy: An E-Commerce Store (like Amazon/Flipkart)

┌──────────────────────────────────────────────────────┐
│  ShopKart - Online Store Database                    │
│                                                      │
│  Products Table:                                     │
│  ┌─────┬──────────────────┬────────┬────────┐        │
│  │ ID  │ Product Name     │ Price  │ Stock  │        │
│  ├─────┼──────────────────┼────────┼────────┤        │
│  │ 1   │ iPhone 15        │ 79999  │ 50     │        │
│  │ 2   │ Nike Air Max     │ 8999   │ 120    │        │
│  │ 3   │ The Alchemist    │ 299    │ 500    │        │
│  └─────┴──────────────────┴────────┴────────┘        │
│                                                      │
│  Users Table:                                        │
│  ┌─────┬────────┬────────────────────┐               │
│  │ ID  │ Name   │ Email              │               │
│  ├─────┼────────┼────────────────────┤               │
│  │ 1   │ Rahul  │ rahul@email.com    │               │
│  │ 2   │ Priya  │ priya@email.com    │               │
│  └─────┴────────┴────────────────────┘               │
└──────────────────────────────────────────────────────┘
```

### 🎤 How to Explain in an Interview

> **Say this:** "A DBMS is software that helps us store, organize and manage data in a structured way. Instead of keeping data scattered in files, a DBMS keeps it in tables and gives us an easy way to add, read, update and delete that data safely. For example, an app like Amazon uses a DBMS to keep all its products, users and orders organized so anyone can search and update them instantly."

**One-liner to remember:** *A DBMS is the middleman between the user and the data — it stores data neatly and lets you access it easily and safely.*

---

## 2. Why Do We Need a DBMS?

Imagine running an online store **without** a DBMS:

| Problem Without DBMS | E-Commerce Example | Solution With DBMS |
|---|---|---|
| **Data Redundancy** | Customer "Rahul" is stored in orders.csv, users.csv, reviews.csv separately | Store Rahul once in Users table, reference by UserID |
| **Data Inconsistency** | Rahul's address is updated in orders.csv but not in users.csv | Single source of truth — update once, reflects everywhere |
| **No Security** | Any employee can see all customer credit card details | Role-based access: only payment team sees payment info |
| **No Backup** | Server crashes → all order history lost forever | Automatic backup & recovery |
| **Hard to Search** | "Find all orders by Rahul in last 30 days" → manually search files | One SQL query: `SELECT * FROM Orders WHERE UserID = 1 AND OrderDate > ...` |

### 🎤 How to Explain in an Interview

> **Say this:** "Without a DBMS, data gets duplicated, becomes inconsistent, is hard to secure and easy to lose. A DBMS solves all of this — it removes duplicate data, keeps a single source of truth, adds security with user roles, provides automatic backups, and lets us search huge amounts of data with one simple query."

**Remember 5 keywords:** *Redundancy, Inconsistency, Security, Backup, Easy Search.* — A DBMS fixes all five.

---

## 3. Types of DBMS

### 3.1 Relational DBMS (RDBMS)
Stores data in **tables** (rows and columns). Uses **SQL**.

```
Example: Products Table in an Online Store

┌───────────┬──────────────────┬────────┬────────┐
│ ProductID │ ProductName      │ Price  │ Stock  │
├───────────┼──────────────────┼────────┼────────┤
│ 101       │ iPhone 15        │ 79999  │ 50     │
│ 102       │ Samsung Galaxy   │ 59999  │ 80     │
│ 103       │ OnePlus 12       │ 49999  │ 120    │
└───────────┴──────────────────┴────────┴────────┘

Examples: MySQL, PostgreSQL, Oracle
```

### 3.2 NoSQL DBMS
Stores data in **documents, key-value pairs, or graphs**. No fixed schema.

```
Example: Product stored as JSON Document (MongoDB)

{
  "product_id": 101,
  "name": "iPhone 15",
  "price": 79999,
  "colors": ["Black", "Blue", "White"],
  "specs": {
    "ram": "8GB",
    "storage": "256GB"
  },
  "reviews": [
    { "user": "Rahul", "rating": 5, "comment": "Great phone!" }
  ]
}

→ Flexible! Each product can have different fields.
Examples: MongoDB, Redis, Cassandra
```

### 3.3 Hierarchical DBMS
Data organized in a **tree-like** structure (parent-child).

```
         Online Store
        /            \
  Electronics      Clothing
   /      \           |
Mobiles  Laptops    T-Shirts
  |        |          |
iPhone   MacBook    Nike Tee
```

### 3.4 Network DBMS
Like hierarchical, but a child can have **multiple parents**.

```
Example: A product "iPhone Case" belongs to BOTH "Accessories" and "Phone Cases"
→ Multiple parent categories pointing to the same product.
```

### 🎤 How to Explain in an Interview

> **Say this:** "There are mainly four types of DBMS. **Relational (RDBMS)** stores data in tables using SQL — like MySQL. **NoSQL** stores flexible data like JSON documents — like MongoDB. **Hierarchical** stores data in a tree, parent-to-child. **Network** is similar but a child can have multiple parents. In modern apps, RDBMS and NoSQL are the most commonly used."

**Remember:** *Relational = tables, NoSQL = flexible documents, Hierarchical = tree, Network = tree with multiple parents.*

---

## 4. Database Models

### 4.1 Relational Model (Most Common)

Data is stored in **relations (tables)**. Each table has:
- **Rows (Tuples)** → Each row is one record
- **Columns (Attributes)** → Each column is a property

```
Products Table:
┌───────────┬──────────────────┬──────────┬────────┬────────┐
│ ProductID │ ProductName      │ Category │ Price  │ Stock  │
├───────────┼──────────────────┼──────────┼────────┼────────┤
│ 1         │ iPhone 15        │ Mobiles  │ 79999  │ 50     │
│ 2         │ Nike Air Max     │ Shoes    │ 8999   │ 120    │
│ 3         │ The Alchemist    │ Books    │ 299    │ 500    │
└───────────┴──────────────────┴──────────┴────────┴────────┘

- Relation = Products (the table name)
- Tuple = Each row (e.g., {1, iPhone 15, Mobiles, 79999, 50})
- Attribute = Each column (e.g., ProductName, Price)
- Degree = Number of columns (5)
- Cardinality = Number of rows (3)
```

### 🎤 How to Explain in an Interview

> **Say this:** "The most widely used database model is the **Relational Model**, where data is stored in tables called relations. Each row is a record (called a tuple) and each column is a property (called an attribute). The number of columns is called the **degree** and the number of rows is called the **cardinality**."

**Quick vocab:** *Relation = table, Tuple = row, Attribute = column, Degree = column count, Cardinality = row count.*

---

## 5. Keys in DBMS

Keys **uniquely identify** records and create **relationships** between tables.

### 5.1 Primary Key
Uniquely identifies each row. **Cannot be NULL or duplicate.**

```sql
-- Each user gets a unique UserID
CREATE TABLE Users (
    UserID INT PRIMARY KEY,  -- This is the Primary Key
    Name VARCHAR(100),
    Email VARCHAR(100)
);
```

### 5.2 Foreign Key
A column that **references the Primary Key** of another table. Creates a link between tables.

```
-- Users table
┌────────┬────────┬──────────────────┐
│ UserID │ Name   │ Email            │  ← UserID is Primary Key
├────────┼────────┼──────────────────┤
│ 1      │ Rahul  │ rahul@email.com  │
│ 2      │ Priya  │ priya@email.com  │
└────────┴────────┴──────────────────┘

-- Orders table
┌─────────┬────────┬─────────────┬────────┐
│ OrderID │ UserID │ Product     │ Amount │  ← UserID is Foreign Key
├─────────┼────────┼─────────────┼────────┤
│ 501     │ 1      │ iPhone 15   │ 79999  │  (links to Users table)
│ 502     │ 2      │ Nike Shoes  │ 8999   │
│ 503     │ 1      │ Earphones   │ 1999   │  ← Rahul's 2nd order
└─────────┴────────┴─────────────┴────────┘
```

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    UserID INT,
    Product VARCHAR(100),
    Amount DECIMAL(10, 2),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
```

### 5.3 Candidate Key
All columns (or sets of columns) that **can** be a Primary Key.

> **In simple terms:** the list of "qualified candidates" — any of them could become the Primary Key, but only one gets the job.

```
Users Table: UserID, Email, Phone
- All three can uniquely identify a user
- All three are Candidate Keys
- We pick ONE as the Primary Key (e.g., UserID)
- The rest (Email, Phone) become Alternate Keys
```

### 5.4 Super Key
Any combination of columns that can uniquely identify a row.

> **In simple terms:** a Candidate Key **plus any extra columns**. It still identifies the row uniquely, just with more columns than needed.

```
Super Keys for Users:
{UserID}                    ✓
{UserID, Name}              ✓ (still unique, just extra columns)
{Email}                     ✓
{UserID, Email, Name}       ✓
{Phone}                     ✓
```

### 5.5 Composite Key
A Primary Key made from **two or more columns together**.

```sql
-- A user can review a product only once
-- So (UserID + ProductID) together form a unique key
CREATE TABLE Reviews (
    UserID INT,
    ProductID INT,
    Rating INT,
    Comment TEXT,
    PRIMARY KEY (UserID, ProductID)  -- Composite Key
);

-- UserID=1 + ProductID=101 → Only ONE review allowed
-- UserID=1 + ProductID=102 → Different product, so allowed
```

### Summary of Keys

```
┌──────────────────┬──────────────────────────────────────────────┐
│ Key Type         │ E-Commerce Example                           │
├──────────────────┼──────────────────────────────────────────────┤
│ Primary Key      │ UserID in Users table (unique per user)      │
│ Foreign Key      │ UserID in Orders table (links to Users)      │
│ Candidate Key    │ UserID, Email, Phone (all can be PK)         │
│ Super Key        │ {UserID}, {UserID, Name}, {Email} etc.       │
│ Composite Key    │ (UserID, ProductID) in Reviews table         │
│ Alternate Key    │ Email, Phone (not chosen as Primary Key)     │
└──────────────────┴──────────────────────────────────────────────┘
```

### 🎤 How to Explain in an Interview

> **Say this:** "Keys are used to uniquely identify rows and to connect tables. The **Primary Key** uniquely identifies each row and can't be null or duplicate. A **Foreign Key** points to the primary key of another table to create a relationship. **Candidate Keys** are all the columns that could be the primary key, and the ones we don't pick become **Alternate Keys**. A **Super Key** is any column combination that's unique, and a **Composite Key** is a primary key made of two or more columns together."

**Remember the relationship:** *Primary Key uniquely identifies a row → Foreign Key links to it → that's how two tables connect.*

---

## 6. SQL Basics

SQL (Structured Query Language) is the language used to talk to a relational database.

### 6.1 Types of SQL Commands

```
┌──────────┬──────────────────────┬───────────────────────────┐
│ Category │ Full Form            │ Commands                  │
├──────────┼──────────────────────┼───────────────────────────┤
│ DDL      │ Data Definition      │ CREATE, ALTER, DROP       │
│ DML      │ Data Manipulation    │ INSERT, UPDATE, DELETE    │
│ DQL      │ Data Query           │ SELECT                    │
│ DCL      │ Data Control         │ GRANT, REVOKE             │
│ TCL      │ Transaction Control  │ COMMIT, ROLLBACK,SAVEPOINT│
└──────────┴──────────────────────┴───────────────────────────┘
```

### 6.2 DDL – Create & Modify Tables

```sql
-- Create the Products table for our store
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(100),
    Category VARCHAR(50),
    Price DECIMAL(10, 2),
    Stock INT
);

-- Oops! We forgot to add a discount column
ALTER TABLE Products ADD Discount DECIMAL(5, 2);

-- Remove a table we no longer need
DROP TABLE Products;
```

### 6.3 DML – Insert, Update, Delete Data

```sql
-- Add products to the store
INSERT INTO Products (ProductID, ProductName, Category, Price, Stock)
VALUES (1, 'iPhone 15', 'Mobiles', 79999, 50);

INSERT INTO Products VALUES (2, 'Nike Air Max', 'Shoes', 8999, 120);
INSERT INTO Products VALUES (3, 'The Alchemist', 'Books', 299, 500);

-- Price drop! Update iPhone price
UPDATE Products
SET Price = 74999
WHERE ProductID = 1;

-- Remove a product that's discontinued
DELETE FROM Products
WHERE ProductID = 3;
```

### 6.4 DQL – Query (Read) Data

```sql
-- Get all products in the store
SELECT * FROM Products;

-- Get only product names and prices (for display on homepage)
SELECT ProductName, Price FROM Products;

-- Filter: Show only Mobile phones
SELECT * FROM Products WHERE Category = 'Mobiles';

-- Sort: Show products from cheapest to most expensive
SELECT * FROM Products ORDER BY Price ASC;

-- Sort: Show most expensive first
SELECT * FROM Products ORDER BY Price DESC;

-- Get unique categories (for filter sidebar)
SELECT DISTINCT Category FROM Products;

-- Aggregate functions
SELECT COUNT(*) FROM Products;                     -- Total products: 3
SELECT AVG(Price) FROM Products;                   -- Average price
SELECT MAX(Price) FROM Products;                   -- Most expensive
SELECT MIN(Price) FROM Products;                   -- Cheapest
SELECT Category, COUNT(*) FROM Products
GROUP BY Category;                                 -- Products per category
```

### 6.5 WHERE Clause Operators

```sql
-- Products above ₹10,000
SELECT * FROM Products WHERE Price > 10000;

-- Products between ₹5,000 and ₹50,000
SELECT * FROM Products WHERE Price BETWEEN 5000 AND 50000;

-- Products starting with "iPhone"
SELECT * FROM Products WHERE ProductName LIKE 'iPhone%';

-- Products ending with "Max"
SELECT * FROM Products WHERE ProductName LIKE '%Max';

-- Products in specific categories
SELECT * FROM Products WHERE Category IN ('Mobiles', 'Laptops');

-- Products with no discount set
SELECT * FROM Products WHERE Discount IS NULL;

-- Expensive mobiles
SELECT * FROM Products WHERE Category = 'Mobiles' AND Price > 50000;

-- Mobiles OR Laptops
SELECT * FROM Products WHERE Category = 'Mobiles' OR Category = 'Laptops';
```

### 🎤 How to Explain in an Interview

> **Say this:** "SQL is the language we use to talk to a relational database. Its commands are grouped into five categories: **DDL** (CREATE, ALTER, DROP) to define table structure, **DML** (INSERT, UPDATE, DELETE) to change data, **DQL** (SELECT) to read data, **DCL** (GRANT, REVOKE) for permissions, and **TCL** (COMMIT, ROLLBACK) for transactions."

**Remember 5 categories:** *DDL = structure, DML = data, DQL = read, DCL = permissions, TCL = transactions.*

---

## 7. Normalization

Normalization is the process of organizing data in a database to reduce redundancy (duplicate data) and avoid anomalies (update, insert, delete problems).

> **In simple terms:** split one big messy table into smaller related tables so each fact is stored **only once**.

### Why Normalize?

Normalized tables are:
1. Easier to understand
2. Easier to enhance and maintain
3. Protected against anomalies (update, delete, insert)

```
BAD (Unnormalized) — Storing everything in ONE table:
┌─────────┬────────┬─────────────┬──────────┬───────────────┬──────────────┐
│ OrderID │ User   │ Product     │ Price    │ UserAddress   │ UserPhone    │
├─────────┼────────┼─────────────┼──────────┼───────────────┼──────────────┤
│ 501     │ Rahul  │ iPhone 15   │ 79999    │ Mumbai        │ 9876543210   │
│ 502     │ Rahul  │ AirPods     │ 14999    │ Mumbai        │ 9876543210   │
│ 503     │ Priya  │ iPhone 15   │ 79999    │ Delhi         │ 8765432109   │
└─────────┴────────┴─────────────┴──────────┴───────────────┴──────────────┘

Problems:
- Rahul's address & phone stored twice (Redundancy)
- If Rahul moves to Delhi, must update multiple rows (Update Anomaly)
- If we delete Rahul's orders, we lose his phone & address (Delete Anomaly)
- iPhone 15 price stored twice — what if one row says 79999 and another 74999? (Inconsistency)
```

### 7.1 First Normal Form (1NF)

**Rule:** Every column must have **atomic (single) values**. No repeating groups.

```
❌ Violates 1NF:
┌────────┬────────┬───────────────────────┐
│ UserID │ Name   │ Orders                │
├────────┼────────┼───────────────────────┤
│ 1      │ Rahul  │ iPhone 15, AirPods    │  ← Multiple values in one cell!
└────────┴────────┴───────────────────────┘

✅ In 1NF: One value per cell
┌────────┬────────┬─────────────┐
│ UserID │ Name   │ Product     │
├────────┼────────┼─────────────┤
│ 1      │ Rahul  │ iPhone 15   │
│ 1      │ Rahul  │ AirPods     │
└────────┴────────┴─────────────┘
```

### 7.2 Second Normal Form (2NF)

**Rule:** Must be in 1NF + **No partial dependency** (every non-key column depends on the **whole** primary key).

```
❌ Violates 2NF (Composite Key: UserID + ProductID):
┌────────┬───────────┬──────────┬─────────────┐
│ UserID │ ProductID │ UserName │ ProductName │
├────────┼───────────┼──────────┼─────────────┤
│ 1      │ 101       │ Rahul    │ iPhone 15   │
└────────┴───────────┴──────────┴─────────────┘
- UserName depends ONLY on UserID (not ProductID) → Partial Dependency!
- ProductName depends ONLY on ProductID (not UserID) → Partial Dependency!

✅ In 2NF: Split into separate tables

Users:                   Products:                Orders:
┌────────┬────────┐     ┌───────────┬───────────┐ ┌────────┬───────────┐
│ UserID │ Name   │     │ ProductID │ Name      │ │ UserID │ ProductID │
├────────┼────────┤     ├───────────┼───────────┤ ├────────┼───────────┤
│ 1      │ Rahul  │     │ 101       │ iPhone 15 │ │ 1      │ 101       │
└────────┴────────┘     └───────────┴───────────┘ └────────┴───────────┘
```

### 7.3 Third Normal Form (3NF)

**Rule:** Must be in 2NF + **No transitive dependency** (non-key column should not depend on another non-key column).

```
❌ Violates 3NF:
┌─────────┬────────┬────────────┬──────────────┐
│ OrderID │ UserID │ CityID     │ CityName     │
├─────────┼────────┼────────────┼──────────────┤
│ 501     │ 1      │ C1         │ Mumbai       │
└─────────┴────────┴────────────┴──────────────┘
- CityName depends on CityID (not on OrderID) → Transitive Dependency!
- OrderID → CityID → CityName

✅ In 3NF: Split into two tables

Orders:                              Cities:
┌─────────┬────────┬────────┐       ┌────────┬──────────┐
│ OrderID │ UserID │ CityID │       │ CityID │ CityName │
├─────────┼────────┼────────┤       ├────────┼──────────┤
│ 501     │ 1      │ C1     │       │ C1     │ Mumbai   │
└─────────┴────────┴────────┘       └────────┴──────────┘
```

### 7.4 BCNF (Boyce-Codd Normal Form)

**Rule:** Must be in 3NF + For every dependency **X → Y**, X must be a **super key**.

```
A stricter version of 3NF.
If a non-candidate-key determines part of a candidate key,
it violates BCNF but not 3NF.

Example: If a seller can sell a product in only one warehouse,
but a warehouse can hold products from many sellers →
Seller → Warehouse, but Seller is not a super key → BCNF violation!
```

### Quick Summary

```
1NF → Atomic values (no "iPhone, AirPods" in one cell)
2NF → No partial dependency (whole key needed)
3NF → No transitive dependency (no non-key → non-key)
BCNF → Every determinant is a super key
```

### 🎤 How to Explain in an Interview

> **Say this:** "Normalization is the process of organizing data into multiple tables to remove duplicate data and avoid update, insert and delete problems. We do it in steps: **1NF** makes sure each cell holds only a single value, **2NF** removes partial dependencies so every column depends on the full key, and **3NF** removes transitive dependencies so no non-key column depends on another non-key column. **BCNF** is a stricter version of 3NF where every determinant must be a super key."

**Easy ladder to remember:** *1NF = atomic values, 2NF = full-key dependency, 3NF = no indirect dependency, BCNF = determinant must be a super key.*

---

## 8. Denormalization

Denormalization is the **opposite of normalization** — we **intentionally add redundancy** back into a database to **improve read performance**.

### Why Denormalize?

Normalization splits data into many tables. To read that data, we need **JOINs**, which can be **slow** on large datasets.

```
Normalized (3 tables, needs JOIN):

  Users table + Orders table + Products table
      ↓              ↓              ↓
  SELECT U.Name, O.OrderDate, P.ProductName
  FROM Users U
  JOIN Orders O ON U.UserID = O.UserID
  JOIN OrderItems OI ON O.OrderID = OI.OrderID
  JOIN Products P ON OI.ProductID = P.ProductID
  WHERE U.UserID = 1;

  → 3 JOINs = SLOW when tables have millions of rows!

Denormalized (1 table, no JOIN needed):

  ┌─────────┬────────┬─────────────┬─────────────┬────────┐
  │ OrderID │ User   │ UserEmail   │ Product     │ Price  │
  ├─────────┼────────┼─────────────┼─────────────┼────────┤
  │ 501     │ Rahul  │ rahul@...   │ iPhone 15   │ 79999  │
  │ 502     │ Priya  │ priya@...   │ Nike Shoes  │ 8999   │
  └─────────┴────────┴─────────────┴─────────────┴────────┘

  → No JOINs needed = FAST read!
  → But User data is duplicated (redundancy)
```

### Normalization vs Denormalization

```
┌──────────────────────┬─────────────────────┬─────────────────────┐
│ Aspect               │ Normalization       │ Denormalization     │
├──────────────────────┼─────────────────────┼─────────────────────┤
│ Goal                 │ Remove redundancy   │ Add redundancy      │
│ Read Speed           │ Slower (needs JOINs)│ Faster (no JOINs)   │
│ Write Speed          │ Faster (update once) │ Slower (update many)│
│ Storage              │ Less space          │ More space           │
│ Data Integrity       │ High                │ Risk of inconsistency│
│ Best For             │ Write-heavy apps    │ Read-heavy apps      │
└──────────────────────┴─────────────────────┴─────────────────────┘
```

### E-Commerce Example

```
Scenario: ShopKart's "Order History" page

User opens "My Orders" → needs: OrderID, Date, ProductName, Price, UserName

Normalized approach:
  → JOIN Orders + OrderItems + Products + Users
  → 4 tables joined = slow for 10 million orders

Denormalized approach:
  → Store a copy of ProductName and UserName directly in the Orders table
  → One simple SELECT = fast!

Denormalized Orders Table:
┌─────────┬────────┬─────────────┬────────┬────────────┐
│ OrderID │ User   │ Product     │ Price  │ OrderDate  │
├─────────┼────────┼─────────────┼────────┼────────────┤
│ 501     │ Rahul  │ iPhone 15   │ 79999  │ 2026-06-15 │
│ 502     │ Rahul  │ AirPods     │ 14999  │ 2026-06-16 │
│ 503     │ Priya  │ Nike Shoes  │ 8999   │ 2026-06-17 │
└─────────┴────────┴─────────────┴────────┴────────────┘

Query:
  SELECT * FROM Orders WHERE User = 'Rahul';
  → No JOINs, instant result!
```

### Common Denormalization Techniques

```
┌───────────────────────┬──────────────────────────────────────────────┐
│ Technique             │ E-Commerce Example                           │
├───────────────────────┼──────────────────────────────────────────────┤
│ Store derived data    │ Save TotalAmount in Orders instead of       │
│                       │ calculating SUM(Price) from OrderItems      │
│                       │                                              │
│ Duplicate columns     │ Store ProductName in Orders table so you    │
│                       │ don't need to JOIN with Products table      │
│                       │                                              │
│ Pre-computed tables   │ Create a DailySales summary table instead   │
│                       │ of running GROUP BY on millions of orders   │
│                       │                                              │
│ Caching/Materialized  │ Store "Top 10 Products" in a separate table │
│ Views                 │ updated every hour instead of querying live │
└───────────────────────┴──────────────────────────────────────────────┘
```

### When to Use

```
✅ Denormalize When:                      ❌ Don't Denormalize When:
- Read-heavy app (dashboards, reports)    - Write-heavy app (lots of updates)
- Complex JOINs are slowing queries       - Data consistency is critical
- Data rarely changes after insert        - Storage space is limited
- Real-time performance is needed         - Small dataset (JOINs are fast enough)

Real-world: Amazon product pages are denormalized
  → Product name, price, seller, rating all stored together
  → No JOINs needed to display the page = loads in milliseconds
```

### 🎤 How to Explain in an Interview

> **Say this:** "Denormalization is the opposite of normalization — we intentionally add some duplicate data back into the database to make reads faster. Normalization splits data into many tables, which means slow JOINs on big datasets. By storing some data together (like keeping the product name directly inside the orders table), we avoid JOINs and read data much faster. The trade-off is more storage and a risk of inconsistency, so it's best for read-heavy apps."

**One line:** *Normalization removes redundancy for clean writes; denormalization adds redundancy for fast reads.*

---

## 9. Joins

Joins combine rows from **two or more tables** based on a related column.

### Sample Tables

```
Users:                                    Orders:
┌────────┬────────┬───────────┐          ┌─────────┬────────┬─────────────┬────────┐
│ UserID │ Name   │ City      │          │ OrderID │ UserID │ Product     │ Amount │
├────────┼────────┼───────────┤          ├─────────┼────────┼─────────────┼────────┤
│ 1      │ Rahul  │ Mumbai    │          │ 501     │ 1      │ iPhone 15   │ 79999  │
│ 2      │ Priya  │ Delhi     │          │ 502     │ 2      │ Nike Shoes  │ 8999   │
│ 3      │ Amit   │ Bangalore │          │ 503     │ 5      │ Laptop      │ 55999  │
│ 4      │ Sara   │ Chennai   │          └─────────┴────────┴─────────────┴────────┘
└────────┴────────┴───────────┘
Note: UserID 5 in Orders doesn't exist in Users (maybe deleted account)
Note: UserID 3 (Amit) and 4 (Sara) haven't placed any orders yet
```

### 8.1 INNER JOIN
Returns only **matching rows** from both tables.

```sql
-- "Show me all orders with the user's name"
SELECT U.Name, O.Product, O.Amount
FROM Users U
INNER JOIN Orders O ON U.UserID = O.UserID;

Result:
┌────────┬─────────────┬────────┐
│ Name   │ Product     │ Amount │
├────────┼─────────────┼────────┤
│ Rahul  │ iPhone 15   │ 79999  │
│ Priya  │ Nike Shoes  │ 8999   │
└────────┴─────────────┴────────┘
-- Amit & Sara have no orders → excluded
-- Order 503 (UserID 5) has no matching user → excluded
```

### 8.2 LEFT JOIN (LEFT OUTER JOIN)
Returns **all rows from left table** + matching rows from right. NULL if no match.

```sql
-- "Show ALL users and their orders (even if they haven't ordered)"
SELECT U.Name, O.Product, O.Amount
FROM Users U
LEFT JOIN Orders O ON U.UserID = O.UserID;

Result:
┌────────┬─────────────┬────────┐
│ Name   │ Product     │ Amount │
├────────┼─────────────┼────────┤
│ Rahul  │ iPhone 15   │ 79999  │
│ Priya  │ Nike Shoes  │ 8999   │
│ Amit   │ NULL        │ NULL   │  ← No orders yet
│ Sara   │ NULL        │ NULL   │  ← No orders yet
└────────┴─────────────┴────────┘
-- Useful for: "Find users who haven't ordered anything"
-- SELECT * FROM Users U LEFT JOIN Orders O ON ... WHERE O.OrderID IS NULL;
```

### 8.3 RIGHT JOIN (RIGHT OUTER JOIN)
Returns **all rows from right table** + matching rows from left.

```sql
-- "Show ALL orders, even if the user account is deleted"
SELECT U.Name, O.Product, O.Amount
FROM Users U
RIGHT JOIN Orders O ON U.UserID = O.UserID;

Result:
┌────────┬─────────────┬────────┐
│ Name   │ Product     │ Amount │
├────────┼─────────────┼────────┤
│ Rahul  │ iPhone 15   │ 79999  │
│ Priya  │ Nike Shoes  │ 8999   │
│ NULL   │ Laptop      │ 55999  │  ← UserID 5 doesn't exist in Users
└────────┴─────────────┴────────┘
-- Useful for: "Find orphan orders (user deleted their account)"
```

### 8.4 FULL OUTER JOIN
Returns **all rows from both tables**. NULL where there's no match.

```sql
-- "Show everything — all users AND all orders"
SELECT U.Name, O.Product, O.Amount
FROM Users U
FULL OUTER JOIN Orders O ON U.UserID = O.UserID;

Result:
┌────────┬─────────────┬────────┐
│ Name   │ Product     │ Amount │
├────────┼─────────────┼────────┤
│ Rahul  │ iPhone 15   │ 79999  │
│ Priya  │ Nike Shoes  │ 8999   │
│ Amit   │ NULL        │ NULL   │  ← User with no orders
│ Sara   │ NULL        │ NULL   │  ← User with no orders
│ NULL   │ Laptop      │ 55999  │  ← Order with no user
└────────┴─────────────┴────────┘
```

### 8.5 CROSS JOIN
Returns **every combination** of rows (Cartesian Product).

```sql
-- "Show every possible user-product combination"
-- Useful for generating a recommendation matrix
SELECT U.Name, P.ProductName
FROM Users U
CROSS JOIN Products P;

-- If Users has 4 rows and Products has 3 rows
-- Result has 4 × 3 = 12 rows (every user paired with every product)
```

### 8.6 SELF JOIN
A table joins **with itself**. Useful for hierarchical data.

```sql
-- Product categories: find each category and its parent category
Categories:
┌──────────┬──────────────┬──────────┐
│ CatID    │ CatName      │ ParentID │
├──────────┼──────────────┼──────────┤
│ 1        │ Electronics  │ NULL     │  ← Top-level (no parent)
│ 2        │ Mobiles      │ 1        │  ← Under Electronics
│ 3        │ Laptops      │ 1        │  ← Under Electronics
│ 4        │ Gaming       │ 3        │  ← Under Laptops
└──────────┴──────────────┴──────────┘

SELECT C.CatName AS Category, P.CatName AS ParentCategory
FROM Categories C
LEFT JOIN Categories P ON C.ParentID = P.CatID;

Result:
┌──────────────┬────────────────┐
│ Category     │ ParentCategory │
├──────────────┼────────────────┤
│ Electronics  │ NULL           │
│ Mobiles      │ Electronics    │
│ Laptops      │ Electronics    │
│ Gaming       │ Laptops        │
└──────────────┴────────────────┘
```

### Visual Summary of Joins

```
INNER JOIN:       LEFT JOIN:        RIGHT JOIN:      FULL OUTER JOIN:
  ┌───┐             ┌───┐              ┌───┐            ┌───┐
 ╱ ╲ ╱ ╲           ╱███╲╱ ╲           ╱ ╲╱███╲         ╱███╲╱███╲
│   █   │         │█████│   │         │   │█████│       │█████│█████│
 ╲ ╱ ╲ ╱           ╲███╱╲ ╱           ╲ ╱╲███╱         ╲███╱╲███╱
  └───┘             └───┘              └───┘            └───┘
Only matching     All Users +       All Orders +     All from both
 Users+Orders     their orders      their users      tables
```

### 🎤 How to Explain in an Interview

> **Say this:** "A JOIN combines rows from two or more tables based on a related column. An **INNER JOIN** returns only the matching rows in both tables. A **LEFT JOIN** returns all rows from the left table plus matches from the right, with NULLs where there's no match. A **RIGHT JOIN** does the opposite. A **FULL OUTER JOIN** returns everything from both tables. A **CROSS JOIN** gives every combination, and a **SELF JOIN** joins a table with itself — useful for hierarchical data like categories."

**Remember:** *INNER = only matches, LEFT = all left, RIGHT = all right, FULL = everything, CROSS = all combinations, SELF = table with itself.*

---

## 10. ACID Properties

ACID ensures **reliable transactions** in a database. Every transaction must follow these 4 rules.

> **In simple terms:** ACID is a set of guarantees that keeps your data **safe and correct**, even when something fails (crash, error) or many users act at once.

### 10.1 Atomicity – "All or Nothing"

A transaction either **completes fully** or **doesn't happen at all**.

```
Example: User places an order on ShopKart

Step 1: Deduct ₹79,999 from user's wallet  ──→  Wallet: ₹1,00,000 → ₹20,001
Step 2: Reduce product stock by 1           ──→  iPhone Stock: 50 → 49
Step 3: Create order record                 ──→  Order #501 created

If Step 3 fails after Step 1 & 2:
→ ROLLBACK everything!
→ Wallet goes back to ₹1,00,000
→ Stock goes back to 50
→ No partial order exists. Money doesn't disappear.
```

### 10.2 Consistency – "Valid State Only"

Database must go from one **valid state to another**. All rules/constraints are maintained.

```
Rule: Stock cannot go below 0

iPhone Stock = 1 (last piece!)
User A orders 1 iPhone → Stock = 0 ✓ (allowed)
User B tries to order 1 iPhone → Stock would become -1
→ Violation! Transaction is REJECTED.
→ User B sees "Out of Stock" message.
→ Database stays consistent.
```

### 10.3 Isolation – "No Interference"

Multiple transactions running **at the same time** shouldn't affect each other.

```
Flash Sale! Only 1 iPhone left in stock.

User Rahul: Clicks "Buy Now" (reads stock = 1)
User Priya: Clicks "Buy Now" (reads stock = 1)

Without Isolation:
  Both see stock=1 → Both orders succeed → Stock = -1 (IMPOSSIBLE!)

With Isolation:
  Rahul's transaction completes first → Stock = 0
  Priya's transaction checks → Stock = 0 → "Out of Stock!"
  Only ONE person gets the phone ✓
```

### 10.4 Durability – "Changes Are Permanent"

Once a transaction is **committed**, the data is saved **permanently**, even if the system crashes.

```
User places order → Payment successful → COMMIT
                                           ↓
                    Server crashes right after commit
                                           ↓
                    Server restarts → Order is STILL in database ✓
                    → User gets confirmation email
                    → Delivery will happen as expected
```

### Summary

```
┌─────────────┬───────────────────────────────────────────────┐
│ Property    │ E-Commerce Meaning                            │
├─────────────┼───────────────────────────────────────────────┤
│ Atomicity   │ Order either fully placed or not at all       │
│ Consistency │ Stock never goes negative                     │
│ Isolation   │ Two users can't buy the last item             │
│ Durability  │ Completed orders survive server crashes       │
└─────────────┴───────────────────────────────────────────────┘
```

---

## 11. Indexing

An index is like a **book's index** — it helps the database find rows **faster** without scanning the entire table.

> **In simple terms:** instead of reading every row to find data, the database keeps a sorted "shortcut list" that jumps straight to the right row.

### Without Index vs With Index

```
Without Index (Full Table Scan):
  "Find all orders by UserID 5001 from 10 million orders"
  → Scans row 1, row 2, row 3, ... row 10,000,000  (VERY SLOW)

With Index on UserID:
  → Directly jumps to UserID 5001's orders using B-Tree  (FAST!)
```

### Creating an Index

```sql
-- Users frequently search products by name
CREATE INDEX idx_product_name ON Products(ProductName);

-- Now this query is much faster:
SELECT * FROM Products WHERE ProductName = 'iPhone 15';

-- Users also filter by category
CREATE INDEX idx_product_category ON Products(Category);

-- Drop an index
DROP INDEX idx_product_name;
```

### Types of Indexes

```
┌─────────────────────┬────────────────────────────────────────────┐
│ Type                │ E-Commerce Example                         │
├─────────────────────┼────────────────────────────────────────────┤
│ Primary Index       │ Auto-created on ProductID (Primary Key)    │
│ Secondary Index     │ Manually created on ProductName, Category  │
│ Clustered Index     │ Products sorted by ProductID on disk       │
│                     │ (only ONE per table)                       │
│ Non-Clustered Index │ Separate lookup for ProductName searches   │
│                     │ (can have MANY per table)                  │
└─────────────────────┴────────────────────────────────────────────┘
```

### When to Use / Not Use

```
✅ Use Index When:                        ❌ Avoid Index When:
- ProductName (searched frequently)       - "TermsAccepted" (only true/false)
- UserID in Orders (used in JOINs)        - Table with only 50 rows
- Price (used in ORDER BY / filtering)    - Columns updated very frequently
```

### 🎤 How to Explain in an Interview

> **Say this:** "An index is like the index at the back of a book — it helps the database find rows quickly without scanning the whole table. Without an index, the database does a full table scan; with an index it jumps straight to the data using a B-Tree. Indexes make reads much faster, but they slow down writes and take extra storage, so we add them to columns we search or filter on often, not to columns with very few values or that change constantly."

**One line:** *An index trades a little extra storage and slower writes for much faster searches.*

---

## 12. Transactions & Concurrency Control

### 12.1 What is a Transaction?

A transaction is a **sequence of operations** treated as a **single unit**.

> **In simple terms:** A transaction groups several steps so they **all succeed together or all fail together** — never halfway.

```sql
-- Example: User places an order (all 3 steps must succeed or none)
BEGIN TRANSACTION;
    -- Step 1: Deduct money from user's wallet
    UPDATE Wallets SET Balance = Balance - 79999 WHERE UserID = 1;

    -- Step 2: Reduce product stock
    UPDATE Products SET Stock = Stock - 1 WHERE ProductID = 101;

    -- Step 3: Create the order
    INSERT INTO Orders (OrderID, UserID, ProductID, Amount)
    VALUES (501, 1, 101, 79999);
COMMIT;

-- If anything goes wrong at any step:
ROLLBACK;  -- Undo ALL changes, as if nothing happened
```

### 12.2 Transaction States

```
        ┌──────────┐
        │  Active  │ ← User clicks "Place Order"
        └────┬─────┘
             │
     ┌───────┴────────┐
     │                 │
┌────▼──────┐   ┌─────▼─────┐
│ Partially │   │  Failed   │ ← Payment gateway timeout
│ Committed │   └─────┬─────┘
└────┬──────┘         │
     │           ┌────▼─────┐
┌────▼──────┐    │ Aborted  │ ← ROLLBACK (money returned)
│ Committed │    └──────────┘
└───────────┘ ← COMMIT (order confirmed!)
```

### 12.3 Concurrency Problems

Concurrency means **many transactions running at the same time**. When they touch the same data, these problems can occur:

```
1. Dirty Read:
   T1 reduces iPhone stock to 0 → T2 reads stock=0 ("Out of Stock!") → T1 rolls back
   T2 showed "Out of Stock" but the iPhone was actually available!

2. Lost Update:
   T1 reads stock=10 → T2 reads stock=10
   T1 writes stock=9 (1 sold) → T2 writes stock=9 (1 sold)
   Two iPhones were sold, but stock only reduced by 1! T1's update is LOST!

3. Phantom Read:
   T1 counts all orders today = 50 → T2 inserts a new order → T1 counts again = 51
   T1 sees a "phantom" order that wasn't there during its first count!
```

### 12.4 Concurrency Control Methods

```
┌──────────────────┬──────────────────────────────────────────────┐
│ Method           │ E-Commerce Example                           │
├──────────────────┼──────────────────────────────────────────────┤
│ Lock-Based       │ Lock the iPhone row when someone is buying   │
│                  │ (Shared Lock = viewing, Exclusive = buying)  │
│ Timestamp-Based  │ First user's transaction gets priority       │
│ MVCC             │ Each user sees their own snapshot of stock   │
│                  │ (used by PostgreSQL)                         │
└──────────────────┴──────────────────────────────────────────────┘
```

### 🎤 How to Explain in an Interview

> **Say this:** "A transaction is a group of operations treated as a single unit — they all succeed together or all fail together, using COMMIT to save and ROLLBACK to undo. When many transactions run at the same time, problems can happen like **dirty reads** (reading uncommitted data), **lost updates** (one update overwrites another), and **phantom reads** (new rows appear mid-transaction). To prevent these, databases use concurrency control methods like **locking**, **timestamp ordering**, and **MVCC**, where each user sees their own snapshot of the data."

**Remember:** *Transaction = all-or-nothing unit; concurrency control (locks/timestamps/MVCC) keeps simultaneous transactions from corrupting data.*

---

## 13. ER Model (Entity-Relationship)

The ER model is a **visual diagram** to design a database before creating tables.

### 13.1 Components

```
┌──────────────────┬────────────┬──────────────────────────────────┐
│ Component        │ Symbol     │ E-Commerce Example               │
├──────────────────┼────────────┼──────────────────────────────────┤
│ Entity           │ Rectangle  │ User, Product, Order             │
│ Attribute        │ Oval       │ UserName, Price, OrderDate       │
│ Relationship     │ Diamond    │ "Places" (User places Order)     │
│ Primary Key Attr │ Underlined │ UserID, ProductID, OrderID       │
└──────────────────┴────────────┴──────────────────────────────────┘
```

### 13.2 Cardinality (Relationships)

Cardinality describes **how many rows of one table relate to rows of another**.

```
1:1 (One-to-One):
  One user has ONE wallet. One wallet belongs to ONE user.
  [User] ──1────1── [Wallet]

1:N (One-to-Many):
  One user places MANY orders. One order belongs to ONE user.
  [User] ──1────N── [Order]

M:N (Many-to-Many):
  One order has MANY products. One product appears in MANY orders.
  [Order] ──M────N── [Product]
  → This creates a junction table: OrderItems(OrderID, ProductID, Quantity)
```

### 13.3 ER Diagram Example — E-Commerce Store

```
  ┌─────────────┐                              ┌──────────────┐
  │    User     │        ┌───────────┐         │   Product    │
  │             │        │  Places   │         │              │
  │  UserID     │──1──N──│  Order    │──M──N───│  ProductID   │
  │  Name       │        │           │         │  ProductName │
  │  Email      │        │  OrderID  │         │  Price       │
  │  Phone      │        │  Date     │         │  Stock       │
  └─────────────┘        │  Total    │         │  Category    │
                         └───────────┘         └──────────────┘
                              │
                         ┌────┴────┐
                         │ Payment │
                         │         │
                         │ PayID   │
                         │ Method  │
                         │ Status  │
                         └─────────┘

Converts to Tables:
  Users(UserID, Name, Email, Phone)
  Products(ProductID, ProductName, Price, Stock, Category)
  Orders(OrderID, UserID, OrderDate, Total)
  OrderItems(OrderID, ProductID, Quantity, Price)  ← Junction table
  Payments(PayID, OrderID, Method, Status)
```

### 🎤 How to Explain in an Interview

> **Say this:** "The ER model is a visual way to design a database before we actually build the tables. It has three main parts: **entities** (real-world things like User, Product, Order shown as rectangles), **attributes** (their properties like Name or Price shown as ovals), and **relationships** (how entities connect, like a User *places* an Order, shown as diamonds). We also define **cardinality** \u2014 whether a relationship is one-to-one, one-to-many, or many-to-many. A many-to-many relationship is broken into a junction table. Once the diagram is ready, each entity becomes a table."

**Remember:** *Entity = rectangle, Attribute = oval, Relationship = diamond; cardinality (1:1, 1:N, M:N) tells how they connect, and M:N needs a junction table.*

---

## Quick Revision Cheat Sheet

```
DBMS          → Software to manage databases (e.g., MySQL for ShopKart)
RDBMS         → Stores data in tables (Users, Products, Orders)
SQL           → Language to query databases
DDL           → CREATE, ALTER, DROP (define table structure)
DML           → INSERT, UPDATE, DELETE (manage product/order data)
DQL           → SELECT (search products, view orders)
Primary Key   → UserID, ProductID (unique identifier per row)
Foreign Key   → UserID in Orders table (links order to user)
1NF           → No "iPhone, AirPods" in one cell
2NF           → No partial dependencies
3NF           → No transitive dependencies (CityID → CityName)
INNER JOIN    → Only users who have orders
LEFT JOIN     → All users, even those with no orders
ACID          → Atomicity, Consistency, Isolation, Durability
Index         → Speed up product search by name/category
Transaction   → Place order = deduct money + reduce stock + create order
ER Diagram    → Visual design: User → Places → Order → Contains → Product
```
