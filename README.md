# 🛒 Walmart Sales Data Analysis

An end-to-end SQL project analyzing Walmart sales data to uncover top-performing branches, product trends, and customer behaviour — with the goal of identifying opportunities to improve sales strategies.

---

## 📌 Project Overview

This project explores historical sales data from **3 Walmart branches** (Mandalay, Yangon, Naypyitaw) containing **1,000 transactions across 17 columns**.

The analysis covers three key areas:
- **Product Analysis** — best and worst performing product lines
- **Sales Analysis** — revenue trends, peak hours, and seasonal patterns
- **Customer Analysis** — customer segments, gender distribution, and profitability

---

## 🗃️ Dataset

- **Source:** [Kaggle — Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting)
- **Rows:** 1,000
- **Columns:** 17

| Column | Description |
|--------|-------------|
| invoice_id | Unique sales invoice ID |
| branch | Branch code (A, B, C) |
| city | Branch location |
| customer_type | Member or Normal |
| gender | Customer gender |
| product_line | Product category |
| unit_price | Price per unit |
| quantity | Units sold |
| VAT | 5% tax on COGS |
| total | Total bill amount |
| date | Transaction date |
| time | Transaction time |
| payment_method | Cash / Credit card / Ewallet |
| cogs | Cost of Goods Sold |
| gross_margin_percentage | Gross margin % |
| gross_income | Gross profit |
| rating | Customer rating (1–10) |

---

## 🔧 Tools Used

| Tool | Purpose |
|------|---------|
| MySQL | Database creation, querying, analysis |
| SQL (DDL + DML) | Data wrangling, feature engineering, EDA |

---

## 🧠 Approach

### 1. Data Wrangling
- Built database and created table with `NOT NULL` constraints to eliminate null values at entry
- Inserted and validated all 1,000 records

### 2. Feature Engineering
Added three new calculated columns:
- `time_of_day` — Morning / Afternoon / Evening
- `day_name` — Mon to Fri (busiest day per branch)
- `month_name` — Jan / Feb / Mar (highest revenue month)

### 3. Exploratory Data Analysis (EDA)
Answered 20+ business questions across product, sales, and customer dimensions.

---

## 💡 Business Questions Answered

**Product**
- Which product line generates the most revenue?
- Which product line has the highest VAT?
- Which branches are above average in units sold?

**Sales**
- Which time of day sees the most sales?
- Which month had the highest COGS and revenue?
- Which city generates the most revenue?

**Customer**
- Which customer type is most profitable?
- What is the gender distribution per branch?
- Which day/time gets the best customer ratings?

---

## 💰 Revenue & Profit Formulas

```
COGS          = unit_price × quantity
VAT           = 5% × COGS
Total         = COGS + VAT
Gross Income  = Total − COGS
Gross Margin  = Gross Income / Total Revenue
```

---

## 🗄️ Database Setup

```sql
CREATE DATABASE IF NOT EXISTS walmartSales;

CREATE TABLE IF NOT EXISTS sales(
    invoice_id           VARCHAR(30)    NOT NULL PRIMARY KEY,
    branch               VARCHAR(5)     NOT NULL,
    city                 VARCHAR(30)    NOT NULL,
    customer_type        VARCHAR(30)    NOT NULL,
    gender               VARCHAR(30)    NOT NULL,
    product_line         VARCHAR(100)   NOT NULL,
    unit_price           DECIMAL(10,2)  NOT NULL,
    quantity             INT            NOT NULL,
    tax_pct              FLOAT(6,4)     NOT NULL,
    total                DECIMAL(12,4)  NOT NULL,
    date                 DATETIME       NOT NULL,
    time                 TIME           NOT NULL,
    payment              VARCHAR(15)    NOT NULL,
    cogs                 DECIMAL(10,2)  NOT NULL,
    gross_margin_pct     FLOAT(11,9),
    gross_income         DECIMAL(12,4),
    rating               FLOAT(2,1)
);
```

> For all queries, see [`SQL_queries.sql`](./SQL_queries.sql)

---

## 📁 Project Structure

```
Walmart-Sales-Analysis/
│
├── data/
│   └── WalmartSalesData.csv      # Raw dataset
│
├── SQL_queries.sql                # All analysis queries
└── README.md
```


