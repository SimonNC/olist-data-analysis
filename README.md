# olist-data-analysis

End-to-end data analytics project based on the Olist e-commerce dataset.
The project focuses on building a clean, reliable analytical dataset using Python, followed by business analysis and visualization in Power BI.

> 🚧 **Project status**:
>
> * ✅ Data profiling, cleaning, and quality checks completed in Python
> * 🔄 Power BI modeling and dashboarding in progress

---

## 🎯 Project Objectives

* Understand and prepare raw e-commerce data for analysis
* Apply structured data profiling and cleaning practices
* Enforce data quality rules and business assumptions
* Export analytics-ready datasets in efficient formats
* Build a scalable foundation for BI and dashboarding

---

## 🧰 Tech Stack

* **Python** (pandas, pyarrow)
* **Jupyter Notebook**
* **CSV & Parquet** (data storage)
* **Power BI** (next step)

---

## 📊 Dataset Overview

The project uses the public **Olist Brazilian E-Commerce Dataset**, including the following core tables:

* Orders
* Customers
* Order Items
* Products
* Product Category Translation
* Reviews

---

## 🧪 Data Processing Workflow (Python)

Each table follows the same structured pipeline:

1. **Data Profiling & Understanding**

   * Dataset structure (shape, columns, data types)
   * Missing values and distributions
   * Identification of business-relevant columns

2. **Data Cleaning**

   * Column selection aligned with analytical goals
   * Type standardization (datetime, numeric, categorical)
   * Business rules application
   * Handling missing values
   * Data normalization

3. **Data Quality Checks**

   * Primary key uniqueness
   * Non-null constraints
   * Business logic validation (e.g. non-negative prices, review score ranges)
   * Referential integrity preparation

4. **Export**

   * Clean datasets exported in both **CSV** and **Parquet** formats

---

## 🗂️ Cleaned Tables & Outputs

All cleaned datasets are stored in the `data_cleaned/` directory.

| Table                | Output Files                                                            |
| -------------------- | ----------------------------------------------------------------------- |
| Orders               | `orders_clean.csv` / `orders_clean.parquet`                             |
| Customers            | `customers_clean.csv` / `customers_clean.parquet`                       |
| Order Items          | `order_items_clean.csv` / `order_items_clean.parquet`                   |
| Products             | `products_clean.csv` / `products_clean.parquet`                         |
| Category Translation | `category_translation_clean.csv` / `category_translation_clean.parquet` |
| Reviews              | `reviews_clean.csv` / `reviews_clean.parquet`                           |

---

## 🛡️ Data Quality Approach

Data quality is enforced directly in the pipeline using explicit checks:

* Primary key uniqueness
* Mandatory fields validation
* Numeric constraints (e.g. prices ≥ 0, review scores between 1 and 5)
* Controlled categorical values
* Lookup table integrity

Any violation stops the pipeline early to prevent propagating invalid data.

---

## 📈 Next Steps: Power BI

The next phase of the project will focus on:

* Data modeling (relationships, grain definition)
* Measures and KPIs (revenue, order volume, delivery performance, customer satisfaction)
* Interactive dashboards for business insights
* Performance optimization

---

## 📁 Repository Structure

```text
├── main.ipynb              # Data profiling, cleaning, and export pipeline
├── data_cleaned/           # Analytics-ready datasets (CSV & Parquet)
├── README.md               # Project documentation
└── .gitignore
```

---

## 👤 Author

**Simon**
Data Analyst

This project is part of a personal portfolio focused on practical, business-oriented data analytics.
