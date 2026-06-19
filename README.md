# Super Mart Sales Analysis
> *Built an interactive Power BI sales dashboard analyzing two years of Super Mart transactions to uncover revenue trends, top products, and profitability insights*

---

## ⚙️ Project Type Flags
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
6. [Analysis & Metrics](#8-analysis--metrics)
7. [Key Insights](#9-key-insights)
8. [Recommendations](#10-recommendations)
9. [Deliverables](#13-deliverables)
10. [Author](#14-author)

---

## 1. Project Overview

**Context:** Super Mart is a retail business selling products across multiple categories, channels, and cities. The business needs a clear view of its sales and profitability performance across 2021 and 2022.

**Problem Statement:** The business had raw transaction data but no visual summary to track revenue, profit, top products or sales trends across time, location, and channel.

**Approach:** Prepared the data in Excel using Power Query, where additional columns for Day, Month, and Year were extracted from the date field. Using Merge Queries, columns from the Master Data table were joined into the Input Date table using Product ID as the key. In Power BI, calculated columns were added for Total buying Value and Total Selling Value, Dax measures were created for Profit and Profit Percentage. An interactive dashboard was built with KPIs cards, slicers and mulitple charts types to enable dynamic exploration of the data.

**Outcome:** Delivered a fully interactive Sales Dashboard revealing Total Sales of 401k, Total Profit of 69k, a 21% profit margin, Product41 as the top product, and clear monthly, daily and category-level sales patterns.

---

## 2. Objectives

- **Primary Objective:** Build an interactive Power BI sales dashboard to visualize Super Mart's revenue, profit, and product performance across 2012 and 2022.
- **Secondary Objective 1:** Identify the top-performing products and categories by total sales value. 
- **Secondary Objective 2:** Detemine monthly and daily sales trends to uncover peak and low performance periods.
- **Secondary Objective 3:** Compare sales performance across sales types (Online, Direct Sales, Wholesaler) and payment mode (Cash, Online).

---

## 3. Project Scope & Tools

### Scope

| Dimension | Details |
|-----------|---------|
| **In Scope** | Two years of Super Mart transaction data (2021 - 2022), covering sales volume, revenue, profit, product categories, sale types, and payment modes |
| **Out of Scope** | Customers demographics data and individual customer profiles - these were available in the dataset |
| **Time Period** | January 2021 - Decemeber 2022 |
| **Granularity** | Row-level transaction data (one row per sale transaction) |

### Tools & Technologies

| Category | Tool(s) Used |
|----------|-------------|
| Data Processing | Microsoft Excel, Power Query |
| Data Transformation | Power Query (Merge Queries, Add Column) |
| Data Modeling | Power BI (Calculated Columns, DAX Measures) |
| Visualization | Power BI (KPIs Cards, Bar Charts, Lines Charts, Donut Charts, Treemap, Slicers) |
| Documentation | Microsoft Word, GitHUb |


---

## 4. Repository Structure
```
[Super-Mart]/
│
├── data/
│  └──raw/                  # Original, unmodified source data 
│ 
├── docs/                   # Data dictionaries and project notes
|
├── reports/                # Final deliverables: Word report
│
├── visuals/                # Dashboard screenshots and charts 
│
├── README.md               # You are here
└── project_metadata.yml    # Project metadata
```

## 5. Data Workflow

1. **Source:** Two Excel tables - Input Data (transaction records) and Master Data (product reference list). Data covers January 2021 - December 2022.
2. **Ingestion:** Both tables loaded into Excel, Input Data contains individuals sales transactions. Master Data contains products details including category, unit of measure, buying                         price, and selling  price.
3. **Transformation:** Using Power Query, additional columns were extracted from the data field - Day, Month, and Year - to enable time-based analysis. Merge Queries was used to join                              Master Data columns into the input Data tables using Product ID as the common key.
4. **Modeling:** In Power BI, two calculated columns were added - Total Buying Value and Total Selling Value. Two Dax measures were then created - Profit (Total Selling Value minus Total                    Buying Value) and Profit Percentage (Profit divided by Total Selling Value Mutiplied by 100).
5. **Analysis:** Sales performance was analyzed across time periods, product categories, sale types, payment modes, and individual products using interactive slicers and visualizations.
6. **Output:** Interactive Power BI dashboard, written summary report (Word document), and project documentation uploaded to GitHub.

### Dataset / Table: Input Data

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| Date | Date| Date of the sales transaction | 01/01/2021 |
| Product ID | String | Unique identifier for each product | P0024 |
| Quantity |Integer | Number of units sold per transaction| 9 |
| Sale Type | String | Channel of sale | Direct Sales |
| Payment Mode | String | Method of payment used  | Online |
| Discount % | Float | Discount applied to the transaction  | 0.0% |
| Day | Integer| Day extracted from date (Power Query)| 1 |
| Month | String |  Month extracted from date (Power Query)  |  January  |
| Year | Integer  | Year extracted from date (Power Query)  | 2021 |

> **Row count (approx.):** Multiple transaction records across 2021–2022
> **Date range:**January 2021 – December 2022
> **Key join / relationship:** `Input Data.Product ID ` → `Master Data.Product ID`

---

### Dataset / Table: Master Data

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| Product ID  | String | Unique identifier for each product  | P0015 |
| Product | String | Product name |  Product15  |
| Category | String  |Product category grouping|  Category02  |
| UOM | String | Unit of measure | Ft|
| Buying Price |  Float | Cost price per unit | 12 |
| Selling Price | Float | Selling price per unit | 15.72 |

> **Row count (approx.):** 46 product records
> **Key join / relationship:** `Master Data.Product ID` → `Input Data.Product ID`

---

**Table Relationships Summary:**

| Relationship | Join Key | Type |
|-------------|----------|------|
| `Input Data` → `Master Data` | `Product ID` | `Many-to-One` |

---

## 8. Analysis & Metrics

### Analytical Approach

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| Total Sales | Total revenue from all transactions | Shows overall business performance |
| Total Profit | Revenue minus cost of goods sold | Shows actual earnings after costs |
| Profit % | Profit as a percentage of revenue | Measures how efficiently the business converts sales to profit |
| Top Product | Highest selling product by value | Guides stock prioritization decisions |
| Top Category | Highest selling category by value | Identifies the strongest product group |

### Methods Used

- Descriptive statistics - total sales, profit, and profit margin across the full dataset
- Trend analysis across months and days to identify peak and low trading periods
- Segmentation and group comparison by product, category, sale type, and payment mode
- Custom aggregation using DAX measures in Power BI (Profit and Profit %)
- Calculated columns in Power BI for Total Buying Value and Total Selling Value

---

## 9. Key Insights

1. *Total Sales reached 401K with a 21% profit margin* - meaning Super Mart retains approximately ₦1 in every ₦5 of revenue generated, after product costs.

2. *Product41 is the single top-performing product* with 23K in sales value - significantly ahead of other products, making it the most critical item for stock availability.

3. *January recorded the highest monthly sales*, peaking near 50K, suggesting a strong start-of-year trading period that could be leveraged for future promotions.

4. *Daily sales show recurring peaks around the 10th, 20th, and 30th of each month* - likely aligned with salary payment cycles or restocking patterns.

5. *Online and Direct Sales dominate the sales channel mix*, together accounting for over 85% of transactions, with Wholesaler contributing a smaller share.

6. *Payment is evenly split between Cash and Online (50/50)* - indicating customers have no strong preference for one payment method over the other.

7. *Category04 and Category02 are the top two performing categories*, together making up the majority of category-level revenue.

---

## 10. Recommendations

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | Prioritize stock availability for Product41 and the top 5 products year-round to prevent lost sales from stockouts | Insight 2 - Product41 is the single top-performing product at    23K in sales value | Inventory / Procurement team |
| High | Plan targeted promotions and increased stock levels ahead of January, which consistently records the highest monthly sales | Insight 3 - January peaked near 50K, the strongest       month of the year | Sales / Marketing team |
| Medium | Schedule restocking and staffing around the 10th, 20th, and 30th of each month to meet recurring demand peaks | Insight 4 - Daily sales show consistent peaks around these dates | Operations team |
| Medium | Investigate whether the Wholesaler channel can be expanded, given that Online and Direct Sales currently dominate over 85% of transactions | Insight 5 - Wholesaler contributes a   smaller share of total transactions | Sales / Business Development team |
| Low | Introduce category-level targets for Category04 and Category02 to sustain their leading performance and identify growth opportunities | Insight 7 -  These two categories together      make up the majority of category revenue | Category Management team |
---

## 11. Assumptions & Limitations

### Assumptions
- All transaction records in the Input Data table were assumed to be complete and accurate - no validation was performed against an external source
- Product prices in the Master Data table were assumed to be fixed across the entire 2021–2022 period - price changes over time were not accounted for
- Discount % was 0.0% across all visible records - it was assumed discounts were not applied during this period

### Limitations
- The dataset does not include customer information - therefore no analysis of customer behaviour, repeat purchases, or customer segmentation was possible
- Product and category names are generic (Product41, Category02) - real product names were not available, limiting business-specific interpretation of findings
- No regional or store-level data was available - all analysis is at the overall business level only
- The data covers only 2021–2022 - longer-term trends beyond this period cannot be determined

> The goal here is pre-emptive Q&A. A thoughtful reviewer might ask: "Did you account for price changes?" - this section answers before they ask.

---

## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| Power BI Dashboard | Interactive sales dashboard with KPI cards, slicers, and charts covering revenue, profit, products, categories, and trends | visuals/Super_Mart_Sales_Dashboard.png |
| Summary Report | Written Word document summarizing findings, insights, and recommendations | reports/Super_Mart_Sales_Dashboard_Summary_Report.docx |
| Raw Data | Original Excel file containing Input Data and Master Data sheets | data/raw/supermart-practice-file.xlsx |

---

## 14. Author

**Vivian Okwara**
Data Analyst | Lagos, Nigeria

- 🔗 https://linkedin.com/in/okwara-vivian
- 💼 https://Vivian-Portfolio.github.io
- 📧 okwaravivian26@gmail.com

---

*Last updated: Last updated: June 2026
