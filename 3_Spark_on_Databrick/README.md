# Module 3: Spark Deep Dive

> **From "my data doesn't fit in RAM" to "I trained a distributed ML model."**
> A hands-on, progressive walkthrough of Apache Spark using PySpark.

---

## 🎯 What This Module Is

A structured, progressive deep dive into Spark — the distributed computing
framework every data engineer needs. Written for someone who already knows
Python and SQL, and wants to actually use Spark on real data.

Every lesson is:

- **Self-contained** — you can read it standalone
- **Progressive** — each builds on the last
- **Hands-on** — every concept runs in a notebook
- **Practical** — no academic detours

---

## 🧰 Setup

Two paths:

**Option A — Databricks Community Edition (recommended)**
- Free cluster, no local install
- Mimics real-world distributed setup
- Instructions: `9_Setting_Up_PySpark.md`

**Option B — Local PySpark**
- Run on your own machine
- Good for learning syntax, not for real scale
- Instructions: `9_Setting_Up_PySpark.md`

---

## 📚 The Lessons

Read in order. Each `.md` maps to a section in a notebook.

### Part 1: Background & Why

| # | Lesson | Topic |
|:--|:---|:---|
| 1 | `1_Why_Spark.md` | When data doesn't fit in RAM |
| 2 | `2_Big_Data_and_Distributed_Systems.md` | Distributed computing, master/worker nodes |
| 3 | `3_Hadoop_and_HDFS.md` | HDFS, blocks, replication |
| 4 | `4_MapReduce.md` | Map, Reduce, job tracking |
| 5 | `5_Spark_vs_MapReduce.md` | In-memory vs disk, why Spark is faster |
| 6 | `6_Spark_Ecosystem.md` | SQL, Streaming, MLlib, GraphX |

### Part 2: RDD Foundations

| # | Lesson | Topic |
|:--|:---|:---|
| 7 | `7_RDDs_Fundamentals.md` | Immutability, distribution, fault tolerance, laziness |
| 8 | `8_RDD_Operations.md` | Transformations vs Actions |

### Part 3: DataFrames — The Core

| # | Lesson | Topic |
|:--|:---|:---|
| 9  | `9_Setting_Up_PySpark.md` | Databricks or local setup |
| 10 | `10_SparkSession.md` | The entry point to Spark |
| 11 | `11_Row_Objects.md` | What a row is in PySpark |
| 12 | `12_Creating_DataFrames.md` | From lists, Row objects, storage, empty |
| 13 | `13_DataFrame_Schema.md` | StructType, StructField, DDL |
| 14 | `14_Storing_DataFrames.md` | Writing to CSV, Parquet, JSON, tables |
| 15 | `15_Displaying_DataFrames.md` | show, display, lazy evaluation |
| 16 | `16_Head_Tail_Limit.md` | Getting top/bottom rows |
| 17 | `17_DataFrame_Dimensions.md` | Counting rows and columns |
| 18 | `18_Column_Objects.md` | Accessing columns |
| 19 | `19_Column_Operations.md` | Expressions, cast, alias, rename, drop |
| 20 | `20_Row_Operations.md` | Filter vs slice vs index |
| 21 | `21_Filtering.md` | filter, where, string, NULL |
| 22 | `22_Sorting.md` | orderBy, sort, multi-column, expressions |
| 23 | `23_GroupBy_Aggregations.md` | groupBy, agg, single + multiple |
| 24 | `24_Pivot_Tables.md` | pivot, cross-tabulation |
| 25 | `25_Joins.md` | Inner, left, right, full, semi, anti, cross |
| 26 | `26_Concatenation.md` | union, unionByName |

### Part 4: Advanced DataFrames

| # | Lesson | Topic |
|:--|:---|:---|
| 27 | `27_Window_Functions.md` | Windows, ranking, lag/lead, frames |
| 28 | `28_Missing_Data.md` | na.drop, na.fill, mean-fill |

### Part 5: ML with PySpark

| # | Lesson | Topic |
|:--|:---|:---|
| 29 | `29_MLlib_Intro.md` | What MLlib is, DataFrame-based API |
| 30 | `30_Feature_Engineering_MLlib.md` | VectorAssembler, feature representation |
| 31 | `31_Linear_Regression.md` | Regression end-to-end |
| 32 | `32_Logistic_Regression.md` | Classification end-to-end |
| 33 | `33_ML_Pipelines.md` | Pipeline, Transformer, Estimator |

### Practice

| # | Lesson | Topic |
|:--|:---|:---|
| 34 | `34_Exercises.md` | 10 exercises, easy → hard |

---

## 🗂️ How This Module Is Organized

```
3_Spark_Deep_Dive/
├── README.md
├── 1_Why_Spark.md
├── 2_Big_Data_and_Distributed_Systems.md
├── 3_Hadoop_and_HDFS.md
├── 4_MapReduce.md
├── 5_Spark_vs_MapReduce.md
├── 6_Spark_Ecosystem.md
├── 7_RDDs_Fundamentals.md
├── 8_RDD_Operations.md
├── 9_Setting_Up_PySpark.md
├── 10_SparkSession.md
├── 11_Row_Objects.md
├── 12_Creating_DataFrames.md
├── 13_DataFrame_Schema.md
├── 14_Storing_DataFrames.md
├── 15_Displaying_DataFrames.md
├── 16_Head_Tail_Limit.md
├── 17_DataFrame_Dimensions.md
├── 18_Column_Objects.md
├── 19_Column_Operations.md
├── 20_Row_Operations.md
├── 21_Filtering.md
├── 22_Sorting.md
├── 23_GroupBy_Aggregations.md
├── 24_Pivot_Tables.md
├── 25_Joins.md
├── 26_Concatenation.md
├── 27_Window_Functions.md
├── 28_Missing_Data.md
├── 29_MLlib_Intro.md
├── 30_Feature_Engineering_MLlib.md
├── 31_Linear_Regression.md
├── 32_Logistic_Regression.md
├── 33_ML_Pipelines.md
├── 34_Exercises.md
└── notebooks/
    ├── 01_dataframes_basics.ipynb
    ├── 02_column_operations.ipynb
    ├── 03_row_operations.ipynb
    ├── 04_joins_and_aggregations.ipynb
    ├── 05_window_functions.ipynb
    └── 06_ml_pipeline.ipynb
```

**Two tracks:**

| Track | Purpose | Style |
|:---|:---|:---|
| **`.md` (root)** | Teach the concept | Progressive, teaching-first |
| **`notebooks/`** | Run the concept | Runnable, cell-by-cell |

---

## 🧠 The Learning Method

> **Read a lesson. Open the matching notebook. Run the cell. Confirm. Move on.**

Every lesson follows the same structure:

1. 🎯 What Is It?
2. 📖 Core Concept
3. 🔍 Example
4. ⚠️ Pitfalls
5. 🧠 Rule of Thumb
6. ✅ Practice (points to notebook)
7. 🧩 Concepts Introduced
8. ➡️ Next

---

## 📓 Notebooks Overview

| Notebook | Covers Lessons |
|:---|:---|
| `01_dataframes_basics.ipynb` | 9–17 — Setup, SparkSession, Rows, creating, schemas, displaying, dimensions |
| `02_column_operations.ipynb` | 18–19 — Column objects, expressions, cast, alias, rename, drop |
| `03_row_operations.ipynb` | 20–22 — Row filtering, slicing, indexing, sorting |
| `04_joins_and_aggregations.ipynb` | 23–26 — GroupBy, agg, pivot, joins, concatenation |
| `05_window_functions.ipynb` | 27 — Windows, ranking, lag/lead, frames |
| `06_ml_pipeline.ipynb` | 29–33 — MLlib, feature engineering, regression, classification, pipelines |

Notebooks are launched on Databricks (Option A) or Jupyter with PySpark (Option B).

---

## ⚠️ What's NOT Here (By Design)

This module is an **applied deep dive** — enough to write real Spark jobs.

Deferred to `6_Production_DE` or a future `Spark_Internals_Deep_Dive`:

- DAG scheduler, Catalyst optimizer, Tungsten engine
- Partitioning strategies (repartition, coalesce)
- Broadcast joins, caching strategies
- Structured Streaming
- Cluster management (YARN, Kubernetes)
- Cost optimization

---

## 🔗 Related Modules

| Module | Relation |
|:---|:---|
| `2_SQL_Speedrun` | Prerequisite — Spark SQL is 80% the same SQL |
| `4_Big_Data_Tools` | Follow-up — Airflow orchestrates Spark; Kafka feeds Spark Streaming |
| `5_Modern_Data_Stack` | Follow-up — Databricks is the commercial Spark platform |
| `6_Production_DE` | Follow-up — Spark job tuning, cluster optimization |

---

## ✅ Progress Tracker

| # | Lesson | Notes | Notebook | Status |
|:--|:---|:---|:---|:---|
| 1 | Why Spark | — | — | ⏳ |
| 2 | Big Data & Distributed Systems | — | — | ⏳ |
| 3 | Hadoop & HDFS | — | — | ⏳ |
| 4 | MapReduce | — | — | ⏳ |
| 5 | Spark vs MapReduce | — | — | ⏳ |
| 6 | Spark Ecosystem | — | — | ⏳ |
| 7 | RDD Fundamentals | — | — | ⏳ |
| 8 | RDD Operations | — | — | ⏳ |
| 9 | Setting Up PySpark | — | — | ⏳ |
| 10 | SparkSession | — | 01 | ⏳ |
| 11 | Row Objects | — | 01 | ⏳ |
| 12 | Creating DataFrames | — | 01 | ⏳ |
| 13 | DataFrame Schema | — | 01 | ⏳ |
| 14 | Storing DataFrames | — | 01 | ⏳ |
| 15 | Displaying DataFrames | — | 01 | ⏳ |
| 16 | Head, Tail, Limit | — | 01 | ⏳ |
| 17 | DataFrame Dimensions | — | 01 | ⏳ |
| 18 | Column Objects | — | 02 | ⏳ |
| 19 | Column Operations | — | 02 | ⏳ |
| 20 | Row Operations | — | 03 | ⏳ |
| 21 | Filtering | — | 03 | ⏳ |
| 22 | Sorting | — | 03 | ⏳ |
| 23 | GroupBy & Aggregations | — | 04 | ⏳ |
| 24 | Pivot Tables | — | 04 | ⏳ |
| 25 | Joins | — | 04 | ⏳ |
| 26 | Concatenation | — | 04 | ⏳ |
| 27 | Window Functions | — | 05 | ⏳ |
| 28 | Missing Data | — | 05 | ⏳ |
| 29 | MLlib Intro | — | 06 | ⏳ |
| 30 | Feature Engineering (MLlib) | — | 06 | ⏳ |
| 31 | Linear Regression | — | 06 | ⏳ |
| 32 | Logistic Regression | — | 06 | ⏳ |
| 33 | ML Pipelines | — | 06 | ⏳ |
| 34 | Exercises | — | — | ⏳ |

I'll update this as I go.

---

*This README is the map. The lessons are the territory. Start at 1 and go.*