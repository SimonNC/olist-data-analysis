
# Power BI — Olist E-Commerce Analytics Dashboard

## 🎯 Purpose
This Power BI project represents the **final analytics layer** of the Olist end-to-end data project.
It is designed to showcase **BI best practices**, including clean data modeling, KPI design, and business storytelling.

Target audience:
- Recruiters
- BI / Analytics Managers
- Data Analysts & Analytics Engineers

---

## 🔌 Data Source Configuration

The dashboard uses a **single Power BI parameter**:

- **Parameter name**: `DataFolder`
- **Expected value**: path to the local `data_cleaned/` directory

This makes the project:
- Portable
- Version-controlled
- Easy to run on any machine

➡️ Update the parameter before refreshing the model.

---

## 🧱 Data Model Overview

**Modeling principles**
- Star-schema inspired
- Explicit Date dimension
- Single-direction relationships
- Clear fact vs dimension separation

### Fact Tables
- `orders_clean`
- `order_items_clean`
- `reviews_clean`

### Dimension Tables
- `customers_clean`
- `products_clean`
- `date_dim`

---

## 📊 Measures & KPIs

Measures are centralized and grouped by business domain:

### Sales
- Total Revenue
- Total Orders
- Average Order Value (AOV)

### Delivery
- Delivered Orders
- On-Time Delivery Rate
- Average Delivery Days
- SLA Buckets (≤7, 8–15, 16–30, >30 days)
- Cumulative Delivery Performance

### Reviews
- Average Review Score
- Review Mix (Positive / Neutral / Negative)
- Review Volume Over Time

---

## 📈 Dashboard Pages

### 1️⃣ Sales
Focus: **Commercial performance**
- Revenue & orders trends
- Category & regional breakdown
- KPI cards for executive overview

### 2️⃣ Delivery
Focus: **Logistics & SLA performance**
- Delivered orders vs on-time rate
- SLA distribution
- Identification of SLA tipping points
- Cumulative delivery curve

### 3️⃣ Reviews
Focus: **Customer satisfaction**
- Review score distribution
- Review mix evolution
- Strong correlation between delivery delays & negative reviews

---

## 💡 Key Business Findings

- Customer satisfaction drops sharply after **~25–30 delivery days**
- Late deliveries (>30 days) generate a majority of negative reviews
- Fast deliveries (≤7 days) strongly correlate with positive feedback
- Delivery performance is a key driver of customer perception

---

## ♿ Accessibility & UX

- Consistent color semantics across pages
- KPI-first layout
- Clear visual hierarchy
- Mobile-friendly navigation
- Accessible design considerations

---

## 🧠 Why This Power BI Project Matters

This dashboard reflects **production-level BI expectations**:
- Clean and auditable model
- Business-driven KPIs
- Reusable measures
- Insight-focused storytelling

It is designed to be **maintainable, scalable, and decision-oriented**.

---

## 👤 Author
**Simon**  
Data Analyst  
Portfolio Project — 2026
