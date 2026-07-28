# Superstore Bashboard
> *Analyzed 9,994 retail transactions (2014–2017) to build an interactive Power BI dashboard tracking revenue, profit, and discount impact — helping stakeholders spot where discounting was eroding margin.*

---

## ⚙️ Project Type Flags
> *Check what applies. This helps reviewers and collaborators understand the nature of the work at a glance. Delete this block before publishing.*

- [ ] Exploratory Data Analysis (EDA)
- [ ] SQL Analysis / Querying
- [x] Dashboard / Data Visualization
- [ ] Data Pipeline / ETL
- [ ] Predictive Modelling / Machine Learning
- [x] Data Cleaning / Wrangling
- [ ] End-to-End (multiple of the above)
- [ ] Other: ___________

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Preparation](#5-data-preparation)
6. [Data Model & Schema](#6-data-model--schema)
7. [Analysis & Metrics](#7-analysis--metrics)
8. [Key Insights](#8-key-insights)
9. [Recommendations](#9-recommendations)
10. [Deliverables](#10-deliverables)
11. [Assumption](#11Assumption])
12. [Author](#12-author)

---

## 1. Project Overview

**Context:** Context: Superstore is a retail business selling products across multiple categories, customer segments, and regions. The business needed a clear view of its sales and profitability performance across 2014–2017.
Problem Statement: The business had raw order-level transaction data but no visual summary to track revenue, profit, top products, or sales trends across time, region, and category.

**Problem Statement:**  The business had raw order-level transaction data but no visual summary to track revenue, profit, top products, or sales trends across time, region, and category.

**Approach:** Cleaned the data in Power Query, removing duplicate rows and converting Order Date and Ship Date to proper date types. In Power BI, DAX measures were created for Total Revenue, Total Profit, Profit Margin, and Sales Growth %. An interactive dashboard was built with KPI cards, slicers, and multiple chart types to enable dynamic exploration of the data.

**Outcome:**  Delivered a fully interactive Sales Dashboard revealing Total Revenue of 2.30M, Total Profit of 286.40K, a 12.5% profit margin, Standard Class as the dominant shipping mode, and New York City as the top city by order volume.

---

## 2. Objectives

- **Primary Objective:** Primary Objective: Build an interactive Power BI sales dashboard to visualize Superstore's revenue, profit, and product performance across 2014 and 2017.
- **Secondary Objective 1:** Identify which product sub-categories are discounted heavily without a corresponding profit benefit.
- **Secondary Objective 2:** Determine top-performing products, customers, regions, and shipping modes by order volume and sales value.
- **Secondary Objective 3:** Track year-over-year sales growth trends across the 2014–2017 period.

---

## 3. Project Scope & Tools

### Scope

| Dimension | Details |
|-----------|---------|
| **In Scope** | Four years of Superstore transaction data (2014-2017), covering sales volume, revenue, profit, discount, product categories, shipping modes, and geography |
| **Out of Scope** | Customer demographic data beyond name and segment - no individual customer profiling was performed|
| **Time Period** | January 2014 - December 2017
| **Granularity** | Row-level order/line-item data (one row per order line) |

### Tools & Technologies

| Category | Tool(s) Used |
|----------|-------------|
| Data Processing | Microsoft Excel |
| Data Transformation | Power Query (Change Type, Remove Duplicates |
| Data Modelling |Power BI (DAX Measures
| Visualization |Power BI (KPI Cards, Bar Charts, Line Chart, Scatter Chart, Treemap, Pie Chart, Slicers, Badge Callouts) |
| Documentation | Microsoft Word, GitHub |

---

## 4. Repository Structure

```
[Superstore-Power-BI-Dashboard]/
│
├── data/
│   └── raw/                 # Original, unmodified source data
│
├── reports/                 # Final deliverables: Word report
│
├── visuals/                 # Dashboard screenshots and charts
│
├── README.md                # You are here
└── project_metadata.yml     # Project metadata
```

---

## 5. Data Workflow

1. **Source:** Superstore Sales dataset — order-level retail transaction records. Data covers January 2014 – December 2017.
2. **Ingestion:**Raw data loaded into Excel, containing order and ship dates, customer details, product category/sub-category, sales, profit, discount, quantity, and geographic fields (region, state, city).
3. **Transformation:** Using Power Query, duplicate rows were removed based on the unique Row ID field while preserving legitimate repeated Order IDs. Order Date and Ship Date were converted from text to Date type using "Change Type with Locale" (English – United States). Sales, Profit, and Discount were verified as Decimal Number, and Quantity as Whole Number.
4. **Modelling:** In Power BI, DAX measures were created for Total Revenue, Total Profit, Total Orders, Profit Margin, Previous Month Sales, and Sales Growth %.
5. **Analysis:** Sales performance was analyzed across time periods, product categories, customers, regions, and shipping modes using interactive slicers and visualizations.
6. **Output:** Output: Interactive Power BI dashboard, written analysis report (Word document), and project documentation uploaded to GitHub.
7. 

---

## 6. Data Model & Schema

### Dataset / Table: `Input Data`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `Row ID` | Integer | Unique identifier for each row | 1 | 
| `Order ID` | string | Unique identifier for each order (repeats across line items)|CA -2017-152156|
| `Order Date` | Date | Date the order was placed| 11/08/2017 |
| `Ship Date` | Date | Date of order was shipped | 11/11/2017 |
| `Ship Mode` | string | Shipping method used| [Standard Class |
| `Customer Name` | string |Name of customer | Claire Gute |
| `Segment` | [string  | Customer Segment | Consumer|
| `State` | [string  | State of order |Kentucky |
| `Region` | [string  | Sales Region| South |
| `City` | [string  | City of order | Henderson|
| `Category` | [string  | Production Category | Furniture |
| `Sub-Category` | String  | Product sub- category | Bookcases |
| `Sales` |  float  | Sales amount for the line items | 261.96 |
| `Quantity` |  integer |Number of units sold | 2 |
| `Discount` | float  |Discount applied to the line item | 0.0|
| `Profit` | float  | Profit for the line items | 41.91 |

Row count (approx.): 9,994 rows after cleaning. 
Date range: January 2014 - December 2017.

---

## 7 . Analysis & Metrics

### Key Metrics Defined

Total Revenue = SUM(superstore[Sales])
Total Profit = SUM(superstore[Profit])
Total Orders = DISTINCTCOUNT(superstore[Order ID])
Profit Margin = DIVIDE([Total Profit], [Total Revenue], 0)
Previous Month Sales = CALCULATE([Total Revenue], DATEADD(superstore[Order Date], -1, MONTH))
Sales Growth % = DIVIDE([Total Revenue] - [Previous Month Sales], [Previous Month Sales], 0)

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `Total Revenue ` |Sum of all Sales across the dataset | Establish the overall size of the business being analyzed|
| `Total Profit` | Sum of all Profit across the dataset | Shoes whether revenue is translating into actual earning  |
| `Profit Margin` |Total Profit / Total Revenue| Reveals how efficiently sales convert into profit - flags if margins are being eroded  |
| `Sales Growth%` |Month-over-month change in sales | Signals whether the business is expanding, flat or declining ] |
| `Total Orders` | Distinct count of Order ID | Measures transaction volume independents of order size |
| `Best Shipping Mode` | Ship Mode with highest order volume   | Highlights where fulfillment resources should be prioritized |
| `Top City by Orders` |City with the highest order volume | Identifies the strongest regional market for targeted strategy |

### Methods Use

- Descriptive statistics -distribution of sales and profit across categories, regions, and shipping modes
- Trend analysis across order year (2014–2017) and month
- Segmentation / group comparison by sub-category, region, and customer
- Correlation analysis between Discount and Profit Margin to test whether heavier discounting erodes margin
- DAX time-intelligence functions (DATEADD) for month-over-month sales growth


---


## 9. Key Insights

**Insight 1:Discounting is quietly eroding margin in specific sub-categories**
The scatter plot of Discount vs. Profit Margin shows several sub-categories with high discount percentages but low or negative profit margins. This suggests discount strategy in those lines needs review rather than blanket promotion.

**Insight 2: Standard Class dominates fulfillment**
Standard Class accounts for 2,994 of 5,009 orders (~60%), far outpacing Second Class, First Class, and Same Day combined — indicating most customers aren't paying for faster shipping.

**Insight 3: Technology leads category performance]**
Technology is the top-selling category, ahead of Furniture and Office Supplies, suggesting stronger unit economics or demand in that line worth replicating elsewhere.

**Insight 4 Sales accelerated sharply from 2015 to 2017**
After relatively flat growth in 2014–2015, sales rose sharply through 2017, pointing to a specific driver (new products, markets, or promotions) worth identifying and repeating.


---


## 10. Recommendations


| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | Review and cap discounting on sub-categories showing high discount but low profit margin | Insight 5 - discounting is eroding profitability in specific sub-categories | Sales / Pricing team |
| Medium | Investigate what's driving Technology's lead in sales and apply similar strategies to Furniture and Office Supplies | Insight 6 - Technology leads as the top-selling category| Sales / Marketing team |
| Low | Explore whether offering incentives for faster shipping tires could increase revenue per order | Insight 2 - Standard Class dominates at 60% of orders] | Operations team  


---


## 11. Assumptions & Limitations

### Assumptions
- Transaction records were assumed to be complete and accurate for the full 2014–2017 period; no validation was performed against an external source
- Row ID was treated as the unique identifier for deduplication; repeated Order IDs were assumed to be legitimate multi-line orders, not duplicates
- Discount and Profit figures as provided were assumed accurate at the time of sale, with no later adjustments or returns factored in

### Limitations
-The dataset does not include shipping cost data, so profitability figures reflect product margin only, not fully-loaded cost to serve
- No customer demographic data beyond name and segment was available, limiting deeper behavioral segmentation
- The analysis cannot distinguish whether discounting decisions were deliberate strategy or reactive - if heavy discounts in certain sub-categories were a considered pricing tactic, the margin erosion finding may reflect intent rather than a problem to fix
- The data covers only 2014–2017, so longer-term or seasonal trends beyond this window can't be determined
  

---


## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| Power BI Dashboard  | Interactive dashboard with KPIs cards, slicers, and charts covering revenue, profit, products and trends  |`visuals / superstore dashboard.pgn` |
| Analysis Report | Written words documents summarizing findings, insights and recommendation | [`reports / Superstore_Dashboard_Analysis_Report`] |
| Raw Data| Original Superstore Sales dataset| [`data/raw`] |


---


## 14. Author

**Vivian Okwara**
Data Analyst | Lagos, Nigeria

- 🔗 https://linkedin.com/in/okwara-vivian
- 💼 https://Vivian-Portfolio.github.io
- 📧 okwaravivian26@gmail.com

---

Last updated: Last updated: June 2026
