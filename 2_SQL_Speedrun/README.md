# Module 2: SQL Speedrun

> **Breadth over depth.** This module covers the full SQL surface a Data
> Engineer needs — from databases to window functions — in one pass.
> Deep dives live in `6_SQL_Deep_Dive/` (later).

---

## 🎯 What This Module Is

A structured, progressive walkthrough of SQL — written for someone who
already knows how to program (Python) but has never touched a database.

Every lesson is:
- **Self-contained** — you can read it standalone
- **Progressive** — each builds on the last
- **Practical** — every concept has runnable SQL
- **Reference-ready** — you can come back and skim later

This is **not** a course. It's my personal learning journal — and I'm
writing it the way I wish SQL had been taught to me.

---

## 🧰 Setup

You need two things:

| Tool | Purpose | Link |
|:---|:---|:---|
| **PostgreSQL** | The database server | https://www.postgresql.org/download/ |
| **DBeaver** | GUI client to write and run queries | https://dbeaver.io/download/ |

Setup instructions are in `1_Databases_and_Setup.md`.

---

## 📚 The Lessons

Read in order. Each `.md` maps to a matching `.sql` file in `sql/`.

| # | Lesson | Topic |
|:--|:---|:---|
| 1 | `1_Databases_and_Setup.md` | What a database is, RDBMS vs NoSQL, install |
| 2 | `2_Database_Tree_and_Objects.md` | Server → DB → Schema → Table, objects |
| 3 | `3_Create_Database_and_Schema.md` | CREATE DATABASE / SCHEMA, casing rules |
| 4 | `4_Tables_DataTypes_Constraints.md` | CREATE TABLE, types, PK/FK/UNIQUE/CHECK |
| 5 | `5_Data_Modeling_ERD.md` | ERD, crow's foot notation, e-commerce model |
| 6 | `6_Insert_and_Serial.md` | INSERT, SERIAL, auto-increment |
| 7 | `7_SQL_Command_Categories.md` | DDL, DML, DCL, TCL |
| 8 | `8_Transactions_and_ACID.md` | BEGIN / COMMIT / ROLLBACK / SAVEPOINT |
| 9 | `9_CRUD_Operations.md` | SELECT, INSERT, UPDATE, DELETE |
| 10 | `10_Select_Where_Operators.md` | WHERE + all operator categories |
| 11 | `11_Order_By_Limit_Fetch.md` | Sorting and limiting results |
| 12 | `12_Aggregations_GroupBy_Having.md` | COUNT, SUM, AVG, GROUP BY, HAVING |
| 13 | `13_Null_Handling.md` | NULL, COALESCE, NULLIF |
| 14 | `14_Case_Conditional_Logic.md` | CASE WHEN THEN ELSE END |
| 15 | `15_String_Numeric_Date_Functions.md` | Built-in functions for text, numbers, dates |
| 16 | `16_Subqueries.md` | Inline, correlated, derived tables |
| 17 | `17_Joins.md` | INNER, LEFT, RIGHT, FULL, CROSS |
| 18 | `18_Set_Operators.md` | UNION, UNION ALL, INTERSECT, EXCEPT |
| 19 | `19_CTEs.md` | WITH, single and multiple CTEs |
| 20 | `20_Window_Functions.md` | ROW_NUMBER, RANK, LAG, LEAD, NTILE |
| 21 | `21_Views_and_Materialized_Views.md` | Views, materialized views, refresh |
| 22 | `22_Functions_and_Procedures.md` | CREATE FUNCTION / PROCEDURE, PL/pgSQL |
| 23 | `23_Exception_Handling.md` | EXCEPTION WHEN, RAISE NOTICE |
| 24 | `24_Exercises.md` | 10 exercises, easy → hard |

---

## 🗂️ How This Module Is Organized

```
2_SQL_Speedrun/
├── README.md                          ← you are here
├── 1_Databases_and_Setup.md           ← lessons (progressive, teaching-first)
├── 2_Database_Tree_and_Objects.md
├── ...
├── 24_Exercises.md
│
└── sql/                               ← flat folder, one file per lesson
    ├── 01_create_table.sql            ← setup (builds the e-commerce DB)
    ├── 02_crud_basics.sql
    ├── ...
    └── 99_exercises.sql
```

**Two tracks:**

| Track | Purpose | Style |
|:---|:---|:---|
| **`.md` (root)** | Teach the concept | Long, progressive, one idea at a time |
| **`sql/` (flat)** | Run the concept | Compact, all-in-one, top-to-bottom runnable |

Every `.md` points to its matching `.sql`. Every `.sql` assumes the
e-commerce database from `01_create_table.sql` exists.

---

## 🗃️ The Dataset

All examples use a single e-commerce database with 4 tables:

| Table | What It Stores |
|:---|:---|
| `customers` | Customer info (name, email, city, state) |
| `products` | Product catalog (name, category, price, stock) |
| `orders` | Orders linking customers ↔ products |
| `categories` | Product categories |

The database is created by `sql/01_create_table.sql` and grows as the
lessons progress — we add columns, update rows, and delete records along
the way to demonstrate each concept.

---

## 🧠 The Learning Method

This module follows one rule:

> **Read a lesson. Run its SQL. Confirm it worked. Move on.**

No skipping. No "I'll come back to that." Each lesson assumes the one
before it is understood and practiced.

Every lesson has the same structure:

1. **🎯 What Is It?** — plain-English definition
2. **📖 Core Concept** — broken into digestible pieces
3. **🔍 Example** — small, focused illustration
4. **⚠️ Pitfalls** — the mistakes beginners make
5. **🧠 Rule of Thumb** — one-line takeaway
6. **✅ Practice** — points to the matching SQL file
7. **🧩 Concepts Introduced** — what you just learned
8. **➡️ Next** — what comes next

This structure keeps every lesson predictable and skimmable.

---

## ⚠️ What's NOT Here (By Design)

This module is a **speedrun**. It covers breadth, not depth. The
following are intentionally deferred to `6_SQL_Deep_Dive/`:

- Query optimization and `EXPLAIN` plans
- Indexing internals and performance tuning
- `MERGE` / `UPSERT` and idempotent load patterns
- Incremental loads and CDC (change data capture)
- Table partitioning
- Advanced patterns (gaps-and-islands, sessionization, SCD in SQL)
- Data quality checks in SQL

If you find yourself needing one of those mid-module, that's fine —
finish the speedrun first, then dive deep.

---

## ✅ Progress Tracker

| # | Lesson | Notes | SQL | Status |
|:--|:---|:---|:---|:---|
| 1 | Databases and Setup | ✅ | ✅ | Done |
| 2 | Database Tree and Objects | — | — | Next |
| 3 | Create DB and Schema | — | — | — |
| ... | ... | — | — | — |
| 24 | Exercises | — | — | — |

I'll update this as I go.

---

## 🔗 Related Modules

| Module | Relation |
|:---|:---|
| `1_Fundamentals/` | Prerequisite — broad DE concepts |
| `6_SQL_Deep_Dive/` | Follow-up — depth on optimization, indexing, patterns |
| `3_Big_Data_Tools/` | Next — Spark, Airflow, Kafka |
| `4_Modern_Data_Stack/` | Later — dbt, Snowflake, orchestration |

---

*This README is the map. The lessons are the territory. Start at 1 and go.*
```

---

## 🧠 Why This README Works

| Section | Purpose |
|:---|:---|
| **Framing line** | Sets expectation: breadth, not depth |
| **Setup** | Points to install tools upfront |
| **Lesson table** | The full map — you know where you're going |
| **Organization** | Explains the two-track (`.md` + `sql/`) system |
| **Dataset** | Introduces the e-commerce DB before Lesson 1 |
| **Method** | Tells you *how* to consume the module |
| **What's NOT here** | Prevents scope creep, points to deep dive |
| **Progress tracker** | Living checklist — you update as you go |
| **Related modules** | Shows where this fits in the whole repo |
