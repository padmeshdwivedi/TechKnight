# 🚀 Project O.R.A – Oracle Retail Analytics (IICS Taskflow)

## 📌 Overview

This project demonstrates the design and implementation of an **end-to-end ETL pipeline** using **Informatica Intelligent Cloud Services (IICS)**.
The pipeline extracts retail data from CSV files, transforms it using business logic, and loads it into an **Oracle Data Warehouse**.

---

## 🎯 Objective

* Build a robust ETL pipeline using IICS
* Perform data cleaning, transformation, and aggregation
* Implement **Taskflow orchestration with dependency handling**
* Ensure **data consistency using Full Refresh (Truncate & Load)**

---

## 🏗️ Architecture

```
CSV Files → IICS Mappings → Oracle Tables
```

### Mappings:

1. **m_Store_Load**
2. **m_Product_Load**
3. **m_Sales_Fact_Load**

### Taskflow:

```
Store → Product → Decision → Sales → Notification
```

---

## ⚙️ Technologies Used

* Informatica IICS (Cloud Data Integration)
* Oracle Database
* SQL
* CSV (Flat Files)

---

## 🔄 ETL Process

### 1️⃣ Extract

* Source: CSV files

  * Store Data
  * Product Data
  * Sales Transactions

---

### 2️⃣ Transform

#### ✔ m_Store_Load

* Added `LOAD_DATE` using Expression Transformation

#### ✔ m_Product_Load

* Filtered products where `BASE_PRICE <= 500`

#### ✔ m_Sales_Fact_Load

* Lookup Transformation (Store & Product enrichment)
* Expression (Data standardization – UPPERCASE)
* Aggregator (TOTAL_REVENUE calculation)

---

### 3️⃣ Load

* Target: Oracle Tables

  * DIM_STORE
  * DIM_PRODUCT
  * FACT_SALES

* Implemented **Truncate & Load strategy**

---

## 🔄 Taskflow Design

### Execution Flow:

```
Start → Store Load → Product Load → Decision → Sales Load → Notification → End
```

### Features:

* Sequential execution of mappings
* Decision step for failure handling
* Stops pipeline if dimension load fails
* Notification on successful completion

---

## ⚠️ Challenges Faced

* ❌ ORA-02266 (Foreign Key constraint issue during TRUNCATE)
* ❌ Data type errors in DATE column
* ❌ Handling invalid data

### ✅ Solutions:

* Maintained correct truncate order (FACT → DIM)
* Used data validation and conversion functions
* Implemented proper error handling

---

## ✅ Results

* ✔ Successfully loaded 100 transaction records
* ✔ Filtered invalid products (price ≤ 500)
* ✔ Achieved full refresh data pipeline
* ✔ Automated workflow using Taskflow

---

## 💡 Key Learnings

* ETL pipeline design in IICS
* Lookup & Aggregator transformations
* Taskflow orchestration
* Handling real-world data issues
* Performance tuning and data consistency

---

## 📌 Conclusion

This project demonstrates practical knowledge of **ETL processes, data warehousing, and workflow automation**, making it suitable for real-world data engineering scenarios.

---

## 👨‍💻 Author

**Padmesh Dwivedi**
B.Tech CSE (AI & ML)
AKTU University

---
