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
| **In Scope** | Four years of Superstore transaction data (2014–2017), covering sales volume, revenue, profit, discount, product categories, shipping modes, and geography |
| **Out of Scope** | Customer demographic data beyond name and segment — no individual customer profiling was performed|
| **Time Period** | January 2014 – December 2017
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


```

1. **Source:** Superstore Sales dataset — order-level retail transaction records. Data covers January 2014 – December 2017.
2. **Ingestion:**Raw data loaded into Excel, containing order and ship dates, customer details, product category/sub-category, sales, profit, discount, quantity, and geographic fields (region, state, city).
3. **Transformation:** Using Power Query, duplicate rows were removed based on the unique Row ID field while preserving legitimate repeated Order IDs. Order Date and Ship Date were converted from text to Date type using "Change Type with Locale" (English – United States). Sales, Profit, and Discount were verified as Decimal Number, and Quantity as Whole Number.
4. **Modelling:** In Power BI, DAX measures were created for Total Revenue, Total Profit, Total Orders, Profit Margin, Previous Month Sales, and Sales Growth %.
5. **Analysis:** Sales performance was analyzed across time periods, product categories, customers, regions, and shipping modes using interactive slicers and visualizations.
6. **Output:** Output: Interactive Power BI dashboard, written analysis report (Word document), and project documentation uploaded to GitHub.

---

## 6. Data Model & Schema

### Dataset / Table: `[name]`

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

Row count (approx.): 9,994 rows after cleaning. Date range: January 2014 - December 2017.

---

## 7 . Analysis & Metrics

### Key Performance Indicators

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `KPIs` | [What it measures, in one sentence] | [What decision or question it answers] |
| `[Metric 2]` | [What it measures, in one sentence] | [What decision or question it answers] |
| `[Metric 3]` | [What it measures, in one sentence] | [What decision or question it answers] |

### Methods Used

- [e.g., Descriptive statistics - distribution, central tendency, outlier detection]
- [e.g., Trend analysis across [time period]]
- [e.g., Segmentation / group comparison by [dimension]]
- [e.g., Correlation analysis between [variable A] and [variable B]]
- [e.g., SQL window functions for [specific aggregation]]
- [e.g., Custom aggregation or transformation logic in [tool]]

---

## 9. Key Insights

<!--
  Findings + implications. Not just what happened - what it means.

  WHAT GOOD LOOKS LIKE:
  ✅ "Return rates, not sales volume, explain Region A's underperformance.
      Region A's return rate on home goods was 34% - more than double the
      company average. Revenue was not lost at the point of sale; it was
      lost post-sale through refunds. This points to a fulfilment or
      product quality issue specific to that region, not a demand problem."

  WHAT TO AVOID:
  ❌ "Region A had lower revenue than other regions in Q4."
     (That's an observation. It describes what happened.
      An insight says what it means and where to look next.)

  Aim for 3–6 insights. Quality over quantity.
-->

**Insight 1: [Short descriptive headline]**
[What you found + what it suggests. One short paragraph.]

**Insight 2: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 3: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 4 (if applicable): [Short descriptive headline]**
[What you found + what it suggests.]

---

## 10. Recommendations

<!--
  Action-oriented. Addressed to a real audience.
  Tied explicitly to the insight that supports each one.

  WHAT GOOD LOOKS LIKE:
  Priority: High
  Recommendation: "Conduct a fulfilment audit for home goods deliveries
                   in Region A - specifically investigating whether returns
                   correlate with a particular warehouse, carrier, or SKU batch."
  Based On: Insight 1 - return rate anomaly in Region A
  Owner: Operations / Supply Chain team

  WHAT TO AVOID:
  ❌ "Improve the return rate."
     (Not actionable. Doesn't say who, how, or where to start.)
  ❌ "Further analysis is needed."
     (This is a placeholder, not a recommendation.)
-->

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Medium | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Low | [Exploratory or longer-term suggestion] | [Insight it comes from] | [Who should act] |

---

## 11. Assumptions & Limitations

<!--
  WHAT GOOD LOOKS LIKE:
  Assumption: "Transaction records were assumed to be complete for all five regions.
               No validation was performed against source system record counts."
  Limitation: "The analysis cannot distinguish between returns initiated by
               the customer vs. returns initiated by the business (e.g., recalls).
               If business-initiated returns are concentrated in Region A, the
               return rate finding may reflect a policy decision, not a quality issue."

  WHAT TO AVOID:
  ❌ Leaving this section blank or writing "None known."
     Every project has limitations. Documenting them is a sign of
     analytical maturity - not a confession of failure.
-->

### Assumptions
- [What did you treat as true without being able to verify?]
- [What simplifications did you make for scope or feasibility?]
- [What domain rules or definitions did you accept as given?]

### Limitations
- [What gaps exist in the data?]
- [What analysis was out of scope but could affect interpretation?]
- [What would a more rigorous version of this project include?]
- [Are there known biases in the data source or collection method?]

> *The goal here is pre-emptive Q&A. What would a thoughtful skeptic push back on? Document the answer here, before they ask.*

---

## 12. Future Enhancements

<!--
  WHAT GOOD LOOKS LIKE:
  ✅ "Automate the monthly data pull from the POS export folder using
      a scheduled Python script, replacing the current manual process."
  ✅ "Expand the return rate analysis to include carrier-level data,
      which was unavailable in this dataset but exists in the logistics system."

  WHAT TO AVOID:
  ❌ "Add a machine learning model."
     (Vague, and disconnected from the actual findings of this project.)
  ❌ Listing aspirational features that don't follow logically from the work.
-->

- [ ] [Enhancement 1 - specific and traceable to a real gap in this project]
- [ ] [Enhancement 2]
- [ ] [Enhancement 3]
- [ ] [Enhancement 4]

---

## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |

---

## 14. Author

**[Your Name]**
[Your role or title - current or target]

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [Email - optional]

---

*Last updated: [Month YYYY]*
*If this template helped you, consider starring the repository.*
