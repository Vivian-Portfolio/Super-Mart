# Super Mart Sales Analysis
> *Built an interactive Power BI sales dashboard analyzing two years of Super Mart transactions to uncover revenue trends, top products, and profitability insights*

---

## ⚙️ Project Type Flags

- [x] Dashboard / Data Visualization
- [ ] Predictive Modelling 
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

[project-root]/
│
├── data/
│   ├── raw/                  # Original, unmodified source data - never edited
│   ├── processed/            # Cleaned and transformed data
│   └── external/             # Reference data, lookup tables, third-party files
│
├── notebooks/                # Jupyter, R Markdown, or Colab notebooks
│
├── scripts/                  # Reusable .py, .R, or .sh processing files
│
├── queries/                  # SQL files (retain this folder for SQL-heavy projects)
│   ├── exploratory/          # Ad-hoc or investigative queries
│   ├── transformations/      # Cleaning and reshaping logic
│   └── final/                # Production-ready or presentation queries
│
├── reports/                  # Final outputs: PDFs, slide decks, Word docs
│
├── visuals/                  # Exported charts, dashboard screenshots, ERD diagrams
│
├── docs/                     # Data dictionaries, schema notes, reference material
│
├── project_metadata.yml      # Machine-readable metadata (optional)
└── README.md                 # You are here
⚠️ Delete folders you didn't use. An empty folder is worse than no folder. SQL-heavy projects: keep queries/. Analysis-only projects: keep notebooks/. Both? Keep both.

## 5. Data Workflow

1. **Source:** Two Excel tables - Input Data (transaction records) and Master Data (product reference list). Data covers January 2021 - December 2022.
2. **Ingestion:** Both tables loaded into Excel, Input Data contains individuals sales transactions. Master Data contains products details including category, unit of measure, buying                         price, and selling  price.
3. **Transformation:** Using Power Query, additional columns were extracted from the data field - Day, Month, and Year - to enable time-based analysis. Merge Queries was used to join                              Master Data columns into the input Data tables using Product ID as the common key.
4. **Modeling:** In Power BI, two calculated columns were added - Total Buying Value and Total Selling Value. Two Dax measures were then created - Profit (Total Selling Value minus Total                    Buying Value) and Profit Percentage (Profit divided by Total Selling Value Mutiplied by 100).
5. **Analysis:** Sales performance was analyzed across time periods, product categories, sale types, payment modes, and individual products using interactive slicers and visualizations.
6. **Output:** Interactive Power BI dashboard, written summary report (Word document), and project documentation uploaded to GitHub.

### Dataset / Table: `Input Data`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `Date` | Date| Date of the sales transaction | 01/01/2021 |
| `Product ID` | String | Unique identifier for each product | P0024 |
| `Quantity` |Integer | Number of units sold per transaction| 9 |
| `Sale Type` | String | Channel of sale | Direct Sales |
| `[Payment Mode` | String | Method of payment used  | Online |
| `Discount %` | Float | Discount applied to the transaction  | 0.0% |
| `Day` | Integer| Day extracted from date (Power Query)| 1 |
| `Month` | String |  Month extracted from date (Power Query)  |  January  |
| `Year` | Integer  | Year extracted from date (Power Query)  | 2021 |

> **Row count (approx.):** Multiple transaction records across 2021–2022
> **Date range:**January 2021 – December 2022
> **Key join / relationship:** `Input Data.Product ID ` → `Master Data.Product ID`

---

### Dataset / Table: `Master Data`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `Product ID ` | String | Unique identifier for each product  | P0015 |
| `Product` | String | Product name |  Product15  |
| `Category` | String  |Product category grouping|  Category02  |
| `UOM` | String | Unit of measure | Ft|
| `Buying Price` |  Float | Cost price per unit | 12 |
| `Selling Price` | Float | Selling price per unit | 15.72 |

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

| Metric | Definition | Why It Matters |
|--------|-----------|----------------|
| `Total Sales` | Sum of Total Selling Value across all transactions | Measures overall revenue generated by Super Mart |
| `Total Profit` | Total Selling Value minus Total Buying Value | Shows how much the business earns after product costs |
| `Profit %` | Profit divided by Total Selling Value multiplied by 100 | Measures profitability as a percentage of revenue |
|` Top Product` | Product with the highest total sales value | Identifies the single most valuable product in the catalogue |
| `Top Category` | Category with the highest total sales value | Identifies the strongest performing product group |
| `Monthly Sales Trend` | Sum of Total Selling Value grouped by month | Reveals seasonal patterns and peak trading periods |
| `Daily Sales Trend` | Sum of Total Selling Value grouped by day | Shows within-month fluctuations in purchasing behaviour |
| `Sales by Channel` | Total sales split by sale type (Online, Direct Sales, Wholesaler) | Compares revenue contribution across selling channels |
| `Sales by Payment Mode` | Total sales split by payment method (Cash, Online) | Reveals customer payment preferences |

<!--

### Analytical Approach

[Describe how you approached the analysis. Were you exploring patterns? Testing a hypothesis? Building and validating a pipeline? Be honest about your method - exploratory work is valid, just call it that.]

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `[Metric 1]` | [What it measures, in one sentence] | [What decision or question it answers] |
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
