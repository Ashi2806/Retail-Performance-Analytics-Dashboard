# 📊 Retail Sales Analytics Dashboard | Power BI

## 📌 About the Project

This is an **end-to-end Retail Sales Analytics and Business Intelligence project** built in Microsoft Power BI. It takes messy, raw sales transaction data and turns it into a clean, interactive dashboard that reveals how the business is really performing — across sales, profitability, products, customers, regions, and order trends.

The project follows a full analytics workflow:

**Data Understanding → Data Cleaning → Data Transformation → Data Modeling → DAX → Analysis → Visualization → Business Insights**

---

## 🎯 The Problem

Real-world sales data is rarely analysis-ready. This dataset — covering customers, products, orders, regions, pricing, discounts, and shipping — came with the usual list of issues:

- Inconsistent category labels
- Missing or invalid values
- Wrong data types
- Outliers and suspicious entries
- Duplicate records
- Messy numerical fields

The goal was to turn this raw data into something trustworthy enough to actually make decisions from.

---

## 🎯 Objectives

- Clean and standardize the raw sales dataset
- Catch and fix data-quality issues before analysis
- Build a solid Power BI data model
- Write reusable DAX measures and KPIs
- Analyze sales, profit, products, customers, and regions
- Track order status and trends
- Package everything into an interactive multi-page dashboard
- Turn the numbers into actionable insights

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Modeling, analysis, visualization |
| **Power Query** | Data cleaning and transformation |
| **DAX** | Measures, KPIs, calculations |
| **CSV/Excel** | Source data |
| **GitHub** | Version control and documentation |

---

## 🔄 Workflow

```
Raw Sales Data
      ↓
Data Understanding
      ↓
Data Quality Assessment
      ↓
Data Cleaning
      ↓
Data Transformation
      ↓
Data Modeling
      ↓
DAX Measures & KPIs
      ↓
Data Validation
      ↓
Dashboard Development
      ↓
Business Insights
```

---

## 1️⃣ Understanding the Data

Before touching anything, I explored the dataset to understand what I was working with — customer details, product info, transactions, quantities, unit prices, discounts, sales amounts, profit, demographics, satisfaction scores, region/city, order status, shipping details, and order dates.

Specifically, I checked:

- Row and column counts
- Data types
- Missing values
- Unique values per column
- Duplicate records
- Invalid entries
- Outliers
- How fields related to one another

## 2️⃣ Cleaning & Transforming the Data

All cleaning was done in Power Query.

**Data quality checks covered:**
- Missing values
- Duplicates
- Invalid entries
- Inconsistent categories
- Wrong data types
- Numerical outliers
- Suspicious transaction values

**Gender standardization** — the raw column had multiple variants of the same value (`M`, `m`, `Male`, `male`, `F`, `f`, `Female`, `female`). These were consolidated into: `Male`, `Female`, `Other`, `Unknown` — so the same group isn't accidentally split across categories during analysis.

**Age validation** — flagged unrealistic values (e.g., `999`) so they wouldn't distort customer demographic analysis.

**Quantity validation** — checked for negative values, zeros, and abnormally high numbers that looked like data-entry mistakes.

**Sales amount validation** — cross-checked recorded sales figures against `Quantity × Unit Price × Discount` to catch inconsistencies.

**Shipping validation** — reviewed unusually long "Days to Ship" values to separate genuine outliers from data errors.

**Data type correction** — assigned proper types (Text, Whole Number, Decimal, Date, Currency, Percentage) across all fields to ensure calculations and visuals behaved correctly.

## 3️⃣ Data Modeling

Once cleaned, the data was structured into a model built around Sales, Products, Customers, Regions, Orders, and Profitability, with relationships set up so slicers and filters interact properly across every report page.

## 4️⃣ DAX Measures & KPIs

Core measures written for the dashboard:

```DAX
Total Sales = SUM(retail_sales_dataset[sales_amount])

Total Profit = SUM(retail_sales_dataset[profit])

Total Quantity = SUM(retail_sales_dataset[quantity])

Total Orders = DISTINCTCOUNT(retail_sales_dataset[order_id])

Total Customers = DISTINCTCOUNT(retail_sales_dataset[customer_id])

Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)

Analysis Period = 
"Analysis Period: " & 
FORMAT(MIN(retail_sales_dataset[order_date]), "MMM YYYY") & 
" – " & 
FORMAT(MAX(retail_sales_dataset[order_date]), "MMM YYYY")
```

`Profit Margin` is formatted as a percentage in the report.

**Dynamic date range** — the "Analysis Period" label in the report header isn't static text. It's driven by the measure above, so it automatically reflects the earliest and latest order dates in the dataset. Refresh the data with a wider or narrower date range, and the header updates itself — no manual edits needed.

## 5️⃣ Dashboard — Four Pages

Each page is scoped to one analytical area, so nothing is duplicated across the report.

### 📈 Page 1 — Sales Overview
**KPIs:** Total Sales · Total Profit · Total Quantity · Total Orders

**Visuals:** Sales trend over time, sales by region, sales by payment method, sales by product category, sales vs. profit comparison.

This is the executive-level snapshot of overall performance.

### 📦 Page 2 — Product Analysis
**KPIs:** Total Products · Total Quantity Sold · Average Unit Price · Best-Selling Product

**Visuals:** Top products by sales and by profit, quantity sold by category, average price by category, product-level profitability.

Helps pinpoint which products and categories actually drive revenue and profit.

### 👥 Page 3 — Customer & Regional Analysis
**Customer visuals:** customers by gender, sales by age group, customer satisfaction, top customers by sales.

**Regional visuals:** sales by city, customer count by region, regional performance comparison.

**Filters available:** gender, age group, region, city, product category, customer satisfaction.

### 📦 Page 4 — Orders & Profitability
**KPIs:** Total Orders · Total Sales · Total Profit · Average Shipping Cost · Profit Margin

**Visuals:** orders by status, orders and profit margin by year, and a category profitability summary table comparing product category against total sales, total profit, profit margin, and total orders.

## 🎛️ Interactivity

The report isn't a static export — it's built to be explored:

- Slicers and cross-filtering across all pages
- Drill-down on charts
- KPI cards
- Dynamic, segment-level filtering (region, category, customer segment, etc.)

## 🎨 Design Principles

- Consistent color theme across all pages
- Clear KPI hierarchy
- Clean, uncluttered layout
- Chart types chosen for clarity, not decoration
- Readable labels
- A layout that works for both technical and non-technical viewers

---

## 📊 Key Metrics Tracked

| KPI | What It Measures |
|---|---|
| Total Sales | Overall revenue |
| Total Profit | Overall profit |
| Total Quantity | Units sold |
| Total Orders | Unique order count |
| Total Customers | Unique customer count |
| Average Order Value | Average revenue per order |
| Profit Margin | Profit as a % of sales |
| Average Shipping Cost | Average cost per shipment |

---

## 🔍 Business Questions This Dashboard Answers

**Sales:** How are sales trending? How do regions and categories compare? What's overall revenue health?

**Products:** What are the best-selling and most profitable products? How do categories stack up?

**Customers:** How is the customer base distributed by gender and age? How satisfied are they? Who are the top spenders?

**Regions:** Which cities and regions outperform others?

**Orders:** What does the order-status breakdown look like, and how are order trends moving over time?

**Profitability:** Which categories are most profitable, and how does profit margin compare across the business?

---

## 💡 Business Value

This dashboard turns scattered transactional data into a single source of truth that helps a business:

- Track overall performance at a glance
- Spot the most profitable products and categories
- Understand who its customers are
- Compare regional performance
- Monitor order activity
- Flag areas that need a closer look

---

## 🧠 Skills Demonstrated

Data Analytics · Exploratory Data Analysis · Data Quality Assessment · Data Cleaning · Data Transformation · Power BI · Power Query · Data Modeling · DAX · Dynamic Measures · KPI Development · Interactive Dashboard Design · Data Visualization · Slicers & Filters · Business Intelligence · Sales/Product/Customer/Regional/Profitability Analysis

---

## 📂 Repository Structure

```
Sales-Analytics-PowerBI/
│
├── README.md
│
├── Dataset/
│   └── retail_sales_dataset.csv
│
├── PowerBI/
│   └── Retail_Sales_Analytics_Dashboard.pbix
│
├── Screenshots/
│   ├── 01_Sales_Overview.png
│   ├── 02_Product_Analysis.png
│   ├── 03_Customer_Regional_Analysis.png
│   └── 04_Orders_Profitability.png
│
├── DAX/
    └── measures.dax

```

---

## 🖼️ Dashboard Demo

https://github.com/user-attachments/assets/919832b7-b867-4677-a566-06e82b944031

---

## 📁 What's Inside

- **`Retail_Sales_Analytics_Dashboard.pbix`** — the full Power BI file: Power Query transformations, data model, DAX measures, and all four dashboard pages with filters and interactions.
- **`retail_sales_dataset.csv`** — the source dataset.
- **`measures.dax`** — the DAX calculations used throughout the report.
- **`Screenshots/`** — page-by-page previews for quick viewing on GitHub.


---

## 🚀 How to Run This Project

1. Clone or download this repository.
2. Open `Retail_Sales_Analytics_Dashboard.pbix` in Power BI Desktop.
3. Update the source-data path if needed.
4. Refresh the dataset.
5. Explore all four pages using the built-in filters and slicers.

---

## ✔️ Data Preparation Checklist

- Initial data inspection
- Missing-value handling
- Duplicate detection
- Invalid-value review
- Gender standardization
- Age validation
- Quantity validation
- Sales-value validation
- Shipping-data validation
- Data type correction
- Transformation & modeling

---

## 📌 Outcome

The result is a fully interactive Power BI dashboard that takes raw sales data through the complete analytics lifecycle — from cleaning to modeling to visualization — and turns it into insights a business can actually act on.

---

## ⭐ Highlights

End-to-end Power BI project · real-world data cleaning · Power Query transformations · DAX-driven KPIs · interactive dashboard design · product, customer, regional, and profitability analysis · business-focused storytelling
