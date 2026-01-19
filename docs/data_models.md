# Data Model — Olist E-Commerce Analytics

## 🎯 Objective
This document describes the **analytical data model implemented in Power BI** for the Olist end-to-end analytics project.

The model is designed to support:
- Reliable KPI computation
- High-performance BI queries
- Clear separation of business domains (Sales, Delivery, Reviews)

It follows **analytics engineering and BI best practices**:
- Explicit grain definition
- Fact / dimension separation
- Single-direction relationships
- Business logic pushed upstream when possible

---

## 🧱 Modeling Approach

### Design Principles
- Star-schema inspired architecture
- Domain-driven fact tables
- Dedicated dimensions for time, delivery, and review semantics
- No many-to-many or bidirectional relationships
- Measures isolated in a dedicated table

This model is optimized for:
- Sales performance analysis
- Delivery SLA monitoring
- Customer satisfaction & review analysis

---

## 📐 Grain Definitions

| Table            | Grain Description |
|------------------|------------------|
| f_orders         | One row per order |
| f_order_items    | One row per order × product |
| f_reviews        | One row per order review |
| d_customers      | One row per customer |
| d_products       | One row per product |
| d_date           | One row per calendar day |
| d_delivery_days  | One row per delivery day value |
| d_review_type    | One row per review sentiment |

Clear grain definition prevents:
- Double counting
- Ambiguous aggregations
- KPI inconsistencies across dashboards

---

## 📊 Fact Tables

### 🧾 f_orders — Order & Delivery Lifecycle
**Purpose**  
Central fact table for order tracking and delivery performance.

**Key Fields**
- order_id (PK)
- customer_id (FK)
- order_delivered_customer_date
- delivery_days
- delivery_sla_bucket
- delivery_sla_sort
- delivery_days_bin_label
- delivery_days_bin_center

**Use Cases**
- Delivered orders count
- Delivery delay analysis
- SLA performance tracking
- Bridge between sales, delivery, and reviews

---

### 📦 f_order_items — Revenue & Products
**Purpose**  
Transactional revenue analysis at product level.

**Key Fields**
- order_id (FK)
- product_id (FK)
- price
- freight_value

**Business Logic**
- Revenue = price + freight_value

**Use Cases**
- Total revenue
- Category performance
- Average Order Value (AOV)

---

### ⭐ f_reviews — Customer Satisfaction
**Purpose**  
Customer feedback and satisfaction analysis.

**Key Fields**
- order_id (FK)
- review_score

**Use Cases**
- Average review score
- Review distribution
- Satisfaction vs delivery delay analysis

---

## 🧩 Dimension Tables

### 👤 d_customers — Customer Geography
- customer_id (PK)
- customer_state

Used for:
- Regional sales analysis
- Delivery performance by state

---

### 🛒 d_products — Product Catalog
- product_id (PK)
- product_category_name

Used for:
- Category-level revenue analysis
- Product segmentation

---

### 🌐 d_category_translation — Category Normalization
- category_portuguese
- category_english

Used for:
- Consistent category naming
- English dashboards and storytelling

---

### 📅 d_date — Time Intelligence
- Date (PK)
- Year
- Month
- MonthNum
- MonthYear

Used for:
- Trend analysis
- Year-over-year comparisons
- Consistent temporal slicing

---

### 🚚 d_delivery_days — Delivery Duration
- DeliveryDay (PK)

Used for:
- Cumulative delivery performance curves
- SLA threshold analysis
- Delivery distribution modeling

---

### ⭐ d_review_type — Review Semantics
- Review Type (Positive / Neutral / Negative)
- SortOrder

Used for:
- Review mix analysis
- Ordered sentiment visualizations

---

## 🔗 Relationships Overview

| From (Fact) | To (Dimension) | Cardinality |
|------------|---------------|------------|
| f_orders.customer_id | d_customers.customer_id | Many-to-One |
| f_order_items.order_id | f_orders.order_id | Many-to-One |
| f_order_items.product_id | d_products.product_id | Many-to-One |
| f_reviews.order_id | f_orders.order_id | Many-to-One |
| f_orders.order_delivered_customer_date | d_date.Date | Many-to-One |
| f_orders.delivery_days | d_delivery_days.DeliveryDay | Many-to-One |

All relationships:
- Single-direction
- No bi-directional filtering
- No ambiguous joins

---

## 📐 Measures Table

### 🧮 _measures
Dedicated table for all DAX measures (no data).

Purpose:
- Centralize KPI definitions
- Improve model readability
- Avoid measure duplication

Examples:
- Total Revenue
- Total Orders
- AOV
- On-Time Delivery Rate
- Average Review Score

---

## 🧠 Business Rules Embedded

- Revenue = SUM(price + freight_value)
- Delivery SLA buckets computed upstream
- Review sentiment mapping:
  - 4–5 → Positive
  - 3 → Neutral
  - 1–2 → Negative
- Delivery bins used for non-linear satisfaction analysis

Business logic is intentionally **pushed upstream (Python)** to:
- Ensure consistency
- Simplify DAX
- Improve maintainability

---

## 🚀 Why This Model Works

- Designed for production BI usage
- Scales easily with new KPIs or dimensions
- Supports cross-domain analysis (Sales × Delivery × Reviews)
- Optimized for Power BI performance and clarity

This model reflects **real-world analytics engineering standards**, not exploratory analysis.

---

## 👤 Author

**Simon Jorite**  
Data Analyst | Analytics Engineer  
Microsoft Power BI Certified (PL-300)

Data Analyst with a strong background in **operations, logistics, finance, and e-commerce**, specialized in transforming complex datasets into **reliable KPIs and decision-oriented dashboards**.

Experienced across the full analytics lifecycle:
- Data preparation & quality (Python, SQL)
- Analytical modeling (star schema, BI-ready datasets)
- Business KPI design and storytelling in Power BI

This project reflects a **production-oriented analytics approach**, aligned with real business constraints and stakeholder expectations.

📍 Location: Lyon - France (Open to Hybrid / Remote projects)  
🔗 GitHub: https://github.com/SimonNC  
🔗 LinkedIn: www.linkedin.com/in/simonjorite  
📧 Contact: simon.jorite@gmail.com
