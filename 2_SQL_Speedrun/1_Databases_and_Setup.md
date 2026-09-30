# 1. Databases and Setup

> **Starting point.** No prior SQL needed. By the end of this file you'll
> have a running PostgreSQL database with 4 tables and seed data — ready
> for every lesson that follows.

---

## 🎯 What Is a Database?

A **database** is an organized collection of data — stored and managed
so it can be easily accessed, updated, and analyzed.

Think of a warehouse:

| Warehouse | Database |
|:---|:---|
| Stores physical products | Stores data |
| Organized by aisles, shelves, bins | Organized by databases, schemas, tables |
| You go get what you need | You query what you need |

A database is not just a file. It's a **system** — it enforces rules,
prevents corruption, allows many users at once, and searches millions of
rows in milliseconds.

---

## 🗂️ Two Families of Databases

### RDBMS — Relational Database Management System

Also called **SQL databases**.

- Data is **structured** into tables
- Tables are **related** to each other via keys
- Enforces **consistency** — no orphan rows, no illegal duplicates
- Best for: banking, transactions, anything where accuracy matters

**Examples:** PostgreSQL, MySQL, Oracle, SQL Server

### NoSQL — Non-Relational Database

- Data is **unstructured** or semi-structured
- Everything lives in one collection — no strict relations
- Easy to **scale horizontally**
- Weaker transaction guarantees
- Best for: real-time feeds, flexible schemas, scale-first systems

**Examples:** MongoDB, Cassandra

### Side by Side

| Aspect | RDBMS | NoSQL |
|:---|:---|:---|
| Structure | Tables, rows, columns | Documents, key-value, graph |
| Schema | Fixed, defined upfront | Flexible, dynamic |
| Scaling | Vertical (bigger machine) | Horizontal (more machines) |
| Transactions | Strong (ACID) | Weaker |
| Best for | Banking, structured data | Scale-first systems |

**Neither is better.** Each fits a different problem.

For this module we use **PostgreSQL** — free, modern, open source, and
the industry standard for data engineering.

---

## 🐘 Why PostgreSQL?

- Free and open source
- Modern — supports JSON, arrays, window functions, CTEs, more
- Future-proof — used by startups and enterprises alike
- The data engineer's default — learn SQL on Postgres, adapt to
  Snowflake, Redshift, BigQuery with minor changes

---

## 🛠️ Setup

You need two things:

| Tool | What It Is | Why |
|:---|:---|:---|
| **PostgreSQL** | The database server | Stores and serves the data |
| **DBeaver** | A GUI client | Write and run queries visually |

You could use `psql` (command line) instead of DBeaver. A GUI makes
exploration easier while learning.

### Install PostgreSQL

1. Download: https://www.postgresql.org/download/
2. Run installer — accept defaults
3. **Set a password** — remember it, you'll need it
4. Leave port at `5432`
5. Uncheck "Stack Builder" at the end — not needed
6. Finish

### Install DBeaver

1. Download: https://dbeaver.io/download/
2. Install with defaults
3. Open it

### Connect DBeaver to PostgreSQL (first time only)

1. Click **New Database Connection** (top-left)
2. Choose **PostgreSQL** → Next
3. Leave host/port/database defaults
4. Check **"Show all databases"**
5. Enter your PostgreSQL password
6. Finish

You should see the server in the left panel. Expand it to see databases.

---

## 🧱 The Database Tree

Understanding how pieces nest is critical:

```
Server
 └── Database          ← top-level container
      └── Schema       ← folder-like organizer
           └── Table   ← rows and columns live here
```

| Level | What It Is | Analogy |
|:---|:---|:---|
| **Server** | The machine running PostgreSQL | The building |
| **Database** | A named container for related data | A filing cabinet |
| **Schema** | A folder inside the database | A drawer |
| **Table** | Structured rows and columns | A folder in the drawer |

One server → many databases. One database → many schemas. One schema →
many tables.

Our project:

```
Server (PostgreSQL)
 └── ecommerce_db
      └── ecommerce
           ├── customers
           ├── products
           ├── orders
           └── categories
```

---

## 🔨 What the Setup File Does

`sql/01_create_table.sql` builds the entire foundation in one run.

| Step | Statement | Purpose |
|:---|:---|:---|
| 1 | `CREATE DATABASE ecommerce_db;` | Creates the database |
| 2 | `CREATE SCHEMA ecommerce;` | Creates a schema inside it |
| 3 | `CREATE TABLE ecommerce.customers` | Customer records |
| 4 | `CREATE TABLE ecommerce.products` | Product catalog |
| 5 | `CREATE TABLE ecommerce.orders` | Orders linking customers ↔ products |
| 6 | `CREATE TABLE ecommerce.categories` | Product categories |
| 7 | `INSERT INTO ...` × 4 | Fills each table with sample data |

After running it, refresh the server panel in DBeaver. You'll see the
database, the schema, 4 tables, and rows inside each.

---

## 🧩 Concepts You Just Met

The setup file introduces several keywords. Each gets its own lesson
later, but here's the map:

| Keyword | What It Means |
|:---|:---|
| `CREATE DATABASE` | Make a new database |
| `CREATE SCHEMA` | Make a new schema (folder) |
| `CREATE TABLE` | Make a new table |
| `SERIAL` | Auto-incrementing integer (1, 2, 3, …) |
| `PRIMARY KEY` | Uniquely identifies each row |
| `REFERENCES` | Foreign key — links to another table |
| `UNIQUE` | No duplicate values allowed |
| `CHECK` | Validates a condition (e.g., price ≥ 0) |
| `DEFAULT` | Fallback value if none is given |
| `CURRENT_TIMESTAMP` | "Now" — current date and time |
| `NOT NULL` | Column must have a value |
| `INSERT INTO` | Add rows to a table |

Don't memorize these yet. Just know they exist.

---

## 📐 Basic SQL Style Rules

Two rules that make SQL readable:

**1. End every statement with a semicolon `;`**

A semicolon tells SQL "this statement is done." Without it, the compiler
keeps waiting for more.

**2. UPPERCASE keywords, lowercase identifiers**

- Keywords: `SELECT`, `CREATE`, `FROM`, `WHERE` — words SQL understands
- Identifiers: `customers`, `ecommerce_db` — names *you* give things

SQL is **case-insensitive** for keywords and identifiers, but consistent
casing makes your code readable.

```sql
-- ✅ Readable
CREATE TABLE ecommerce.customers (...);

-- ✅ Also works, harder to read
create table ecommerce.customers (...);
```

---

## ✅ Run It

1. Open DBeaver
2. Right-click the server → **SQL Editor** → **New Script**
3. Paste the contents of `sql/01_create_table.sql`
4. Select all (Ctrl+A) → **Run** (Ctrl+Enter)
5. Refresh the server panel (right-click → Refresh)

**Confirm:**
- `ecommerce_db` appears
- Inside it: `ecommerce` schema
- Inside that: 4 tables with data

---

## 🧭 Where This Fits

You now have a working database. Everything else builds on it:

- Next: **interact** with the data (Lesson 2)
- Then: **create** your own tables (Lesson 3–5)
- Then: **query** it (Lesson 9 onward)
- Finally: **wrap** it up (views, functions — Lesson 21+)

Each step assumes this foundation.

---

## ➡️ Next

**`2_Database_Tree_and_Objects.md`** — the hierarchy you just saw
expanded. What a "database object" is, what lives where, and how to
think about navigating a database like a pro.
