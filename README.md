# Customer_Segmentation_and_Sales_Analysis
Analyzing online retail transactions to discover customer segments, sales patterns, product performance, and business insights.
# Customer Segmentation and Sales Analysis Using Online Retail Data

# 1. Introduction

## 1.1 Purpose & Scope

This project aims to analyze online retail transaction data to understand customer purchasing behavior and sales performance. The system will process historical sales records to identify customer segments, discover purchasing patterns, and generate actionable business insights.

The project utilizes Python and data analytics techniques to support data-driven decision-making and improve customer retention strategies.

## 1.2 Key Objectives

- Clean and preprocess online retail transaction data.
- Analyze sales trends and revenue performance.
- Identify top-selling and high-revenue products.
- Study customer purchasing behavior.
- Perform customer segmentation using RFM Analysis.
- Create visualizations for business insights.
- Generate recommendations for customer retention and sales growth.

## Dataset Information

| Attribute | Details |
|------------|------------|
| Dataset | Online Retail II |
| Source | UCI Machine Learning Repository |
| File Format | Excel (.xlsx) |
| Number of Records | 1,067,371 |
| Number of Columns | 8 |
| Unit of Observation | Retail Transaction |
| Domain | E-Commerce / Retail Analytics |
| Data Type | Transactional Data |
| Time Period | December 2009 - December 2011 |
| Subject Area | Business |
| Missing Values | Yes |
| Feature Type | Integer, Real, Text |
| Associated Tasks | Classification, Regression, Clustering |
| Target Analysis | Customer Segmentation & Sales Analysis |

---

# 2. Data Requirements & Architecture

## 2.1 Data Sources

### Dataset
https://archive.ics.uci.edu/dataset/502/online+retail+ii

### Source Attributes

- Invoice Number
- Stock Code
- Description
- Quantity
- Invoice Date
- Unit Price
- Customer ID
- Country

## 2.2 Data Preprocessing (Python & Pandas)

### Initial Data Inspection

- Load dataset using Pandas.
- Understand dataset structure.
- Check missing values.
- Remove duplicate records.

### Data Cleaning

- Handle missing Customer IDs.
- Remove null descriptions.
- Remove canceled transactions.
- Remove negative quantities if necessary.

### Feature Engineering

Create new features:

- Total Sales = Quantity × Unit Price
- Purchase Month
- Purchase Year
- Purchase Day

### Data Aggregation

- Monthly Sales
- Country-wise Sales
- Customer-wise Purchases
- Product-wise Revenue

---

# 3. System Features & Analytical Pipeline

## 3.1 Sales Analysis

Using Python libraries such as:

- Pandas
- NumPy
- Matplotlib
- Seaborn

### Analysis Tasks

- Monthly Revenue Trends
- Top-Selling Products
- Top Revenue-Generating Products
- Country-wise Sales Performance
- Sales Distribution Analysis

---

## 3.2 Customer Segmentation (RFM Analysis)

### Recency (R)

Days since customer's last purchase.

### Frequency (F)

Number of transactions made by customer.

### Monetary Value (M)

Total amount spent by customer.

### Customer Groups

- Champions
- Loyal Customers
- Potential Loyalists
- At Risk Customers
- Lost Customers

---

## 3.3 Exploratory Data Analysis (EDA)

### Visualization Techniques

### Seaborn

- Heatmaps
- Bar Charts
- Histograms
- Boxplots

### Matplotlib

- Line Charts
- Pie Charts
- Scatter Plots

### Key Insights

- Sales trends over time
- Customer purchase frequency
- Product popularity
- Revenue distribution

---

# 4. Technologies Used

## Programming Language

- Python

## Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## Development Environment

- Jupyter Notebook
- Anaconda

---

# 5. Project Workflow

```text
Dataset Collection
        ↓
Data Cleaning
        ↓
Data Preprocessing
        ↓
Exploratory Data Analysis
        ↓
Sales Analysis
        ↓
RFM Customer Segmentation
        ↓
Data Visualization
        ↓
Business Insights & Recommendations
```

---

# 6. Expected Outputs

- Customer Segmentation Report
- Sales Performance Dashboard
- Top Products Analysis
- Revenue Trend Analysis
- Country-wise Sales Report
- Business Recommendations

---

# 7. Project Directory Structure

```text
Customer_Segmentation_Project/
│
├── data/
│   └── OnlineRetail.xlsx
│
├── notebooks/
│   ├── 1_data_cleaning.ipynb
│   ├── 2_eda.ipynb
│   ├── 3_sales_analysis.ipynb
│   └── 4_customer_segmentation.ipynb
│
├── images/
│
├── reports/
│   └── final_report.pdf
│
├── README.md
│
└── requirements.txt
```

---

# 8. Conclusion

This project analyzes online retail transaction data to identify customer segments and evaluate sales performance.

Through customer segmentation and sales analytics, businesses can better understand customer behavior, improve marketing strategies, and increase overall profitability.

---

# Author

**Viswanadh PV**

# License

This project is developed for educational and academic purposes.


# Phase 2 – Data Preprocessing & Cleaning
 
## Customer Segmentation and Sales Analysis Using Online Retail Data
 
Data preprocessing is a critical step in transforming raw transaction data into a reliable dataset for analysis.
 
In this phase, the **Online Retail II** dataset was combined, cleaned, and standardized using Python and Pandas. The objective was to remove records that do not represent genuine customer purchases, preserve the cancellation records for separate analysis, and prepare an analysis-ready dataset for sales analysis and RFM customer segmentation.
 
---
 
## Dataset
 
| Attribute | Details |
|---|---|
| Dataset | Online Retail II |
| Source | UCI Machine Learning Repository |
| File Format | Excel (.xlsx), two sheets: `Year 2009-2010` and `Year 2010-2011` |
| Original Records | 1,067,371 |
| Original Features | 8 |
| Final Records | 1,003,336 |
| Final Features | 15 (8 original + 7 engineered) |
| Time Period | 1 December 2009 – 9 December 2011 |
 
The two yearly sheets were combined into a single dataset before any cleaning was applied.
 
---
 
## Data Preparation Workflow
 
The following preprocessing steps were performed in order:
 
| Step | Process | Outcome |
|---|---|---|
| 01 | Dataset loading and inspection | Combined both sheets (1,067,371 × 8); reviewed structure, columns, and data types |
| 02 | Column and text standardization | Renamed columns; trimmed text; standardized stock-code and description formatting |
| 03 | Duplicate removal | Removed 34,335 exact duplicate rows |
| 04 | Cancellation separation | Moved 19,104 cancelled-invoice rows to a separate dataset |
| 05 | Quantity validation | Removed 3,393 remaining rows with zero or negative quantity |
| 06 | Price validation | Removed 2,626 rows with a unit price of zero or below |
| 07 | Non-product removal | Removed 4,573 rows for postage, fees, adjustments, vouchers, and test codes |
| 08 | Missing-value handling | Resolved missing descriptions; retained missing Customer IDs with a documented purpose |
| 09 | Post-standardization checks | Removed 2 new duplicates and 2 fully reversed orders |
| 10 | Feature engineering | Created 7 new features, including `TotalSales` |
| 11 | Final validation | Verified dataset consistency and completeness |
 
---
 
## Key Data Cleaning Decisions
 
### Column Names and Data Types
 
`Price` was renamed to `UnitPrice` and `Customer ID` to `CustomerID`. `CustomerID` was stored as a nullable integer because it is an identifier, not a numerical measure (it is read as a decimal only because of its missing values). `Invoice` and `StockCode` were stored as text, `Country` as a category, and `InvoiceDate` as a datetime.
 
### Text and Identifier Standardization
 
Descriptions in 213,039 rows contained leading or trailing spaces, and 3,471 rows used lowercase stock codes (for example `85123a` alongside `85123A`). Stock codes were converted to uppercase, and descriptions were trimmed, uppercased, and stripped of repeated spaces, so the same product is no longer counted as several. 595 stock codes in the cleaned data had more than one description; each was mapped to its most frequent description to support product-level revenue analysis.
 
### Duplicate Records
 
34,335 exact duplicate rows were removed. Two further duplicates appeared after descriptions were standardized and were removed as well.
 
### Cancellations
 
Invoice numbers starting with `C` represent cancelled orders and carry negative quantities. These 19,104 rows were **separated into their own dataset** (8,292 invoices from 2,572 customers) instead of being discarded, so they remain available for return and cancellation analysis. They were excluded from the main dataset so that revenue is not distorted.
 
### Invalid Quantities and Prices
 
A further 3,393 rows had zero or negative quantity without a cancellation prefix, and 2,626 rows had a unit price of zero or below (including bad-debt adjustment entries). None of these represent a valid sale, so they were removed.
 
### Non-Product Stock Codes
 
Several stock codes record services, fees, or internal entries instead of merchandise and would distort revenue and top-product rankings. 4,573 rows were removed for these codes:
 
| Code | Meaning |
|---|---|
| `POST`, `DOT`, `C2`, `C3` | Postage and carriage |
| `M` | Manual entry |
| `D` | Discount |
| `S` | Samples |
| `BANK CHARGES`, `AMAZONFEE`, `CRUK` | Charges and commissions |
| `ADJUST`, `ADJUST2`, `B` | Adjustments and bad debt |
| `TEST001`, `TEST002` | Test products |
| `PADS` | Placeholder item priced at a fraction of a penny |
| `gift_0001_*` | Gift vouchers |
 
### Missing Values
 
| Column | Missing in raw data | Treatment |
|---|---|---|
| `Description` | 4,382 (0.41%) | All were removed by the earlier validation steps; none remain |
| `CustomerID` | 243,007 (22.77%) | Retained in the main dataset (226,761 rows after cleaning) |
 
Rows without a Customer ID are valid sales and remain in the main dataset so that revenue, product, and country analysis cover the whole business. They are excluded only from the RFM dataset, because a customer cannot be segmented without an identity. No Customer IDs were imputed.
 
### Fully Reversed Orders
 
Two very large orders were cancelled by their own credit notes minutes later: invoice `541431` (74,215 units, cancelled by `C541433`) and invoice `581483` (80,995 units, cancelled by `C581484`). Because cancellations were removed from the main dataset, the original orders would have remained and added about £245,653 of revenue that never happened (about 1.3% of the total). Both orders were removed.
 
### Feature Engineering
 
| Feature | Description |
|---|---|
| `TotalSales` | `Quantity × UnitPrice` |
| `Year` | Year of purchase |
| `Month` | Month of purchase |
| `Day` | Day of month |
| `DayOfWeek` | Name of the weekday |
| `Hour` | Hour of purchase |
| `YearMonth` | Year-month label for monthly trends |
 
### Partial Final Month
 
The data ends on 9 December 2011, so December 2011 contains only 24,752 rows. It should be excluded or flagged in monthly revenue trends to avoid a misleading decline.
 
---
 
## Cleaning Impact Summary
 
| Stage | Rows removed | Rows remaining |
|---|---:|---:|
| Raw data (both sheets combined) | – | 1,067,371 |
| Exact duplicates | 34,335 | 1,033,036 |
| Cancelled invoices (separated) | 19,104 | 1,013,932 |
| Zero or negative quantity | 3,393 | 1,010,539 |
| Zero or negative price | 2,626 | 1,007,913 |
| Non-product stock codes | 4,573 | 1,003,340 |
| Missing descriptions | 0 | 1,003,340 |
| Duplicates after standardization | 2 | 1,003,338 |
| Fully reversed orders | 2 | 1,003,336 |
| **Total** | **64,035 (6.0%)** | **1,003,336 (94.0%)** |
 
---
 
## Final Data Quality Results
 
| Quality Check | Result |
|---|---|
| Original Dataset Shape | 1,067,371 × 8 |
| Cleaned Dataset Shape | 1,003,336 × 15 |
| Missing Values (`Description`) | 0 |
| Missing Values (`CustomerID`) | 226,761 (retained intentionally) |
| Duplicate Records | 0 |
| Minimum Quantity | 1 |
| Minimum Unit Price | 0.03 |
| Unique Customers | 5,852 |
| Unique Invoices | 39,514 |
| Unique Products (Stock Codes) | 4,723 |
| Countries | 43 |
| Total Cleaned Revenue | £19,397,657 |
 
---
 
## Datasets Prepared
 
| Dataset | Contents | Purpose |
|---|---|---|
| Cleaned transactions | 1,003,336 rows × 15 columns | Sales analysis and EDA |
| RFM base | 776,575 rows; 5,852 customers; 36,592 invoices (86.7% of cleaned revenue) | Customer segmentation |
| Cancellations | 19,104 rows; 8,292 invoices | Return and cancellation analysis |
 
For RFM, recency should be measured from a snapshot date of **10 December 2011** (the day after the last invoice), and frequency counted as unique invoices per customer.
 
---
 
## Outcome
 
The preprocessing phase produced a consistent, validated dataset that contains only genuine product sales. Duplicates, cancellations, invalid quantities and prices, and non-product entries were removed or separated, product labels were standardized, and new time-based and revenue features were created.
 
The resulting datasets are ready for exploratory data analysis and customer segmentation, with a focus on:
 
- Monthly revenue trends and seasonality
- Top-selling and top-revenue products
- Country-wise sales performance (with the United Kingdom, about 85% of revenue, shown separately from other countries)
- Customer purchasing behavior and purchase frequency
- RFM-based customer segmentation
- Extreme order quantities, which remain in the data and are reviewed during EDA


# Phase 3 – Exploratory Data Analysis (EDA)

## Customer Segmentation and Sales Analysis Using Online Retail Data

Exploratory Data Analysis (EDA) turns a cleaned dataset into an understanding of how the business actually behaves: when it sells, what it sells, where it sells, and who buys.

In this phase, the cleaned **Online Retail II** dataset from Phase 2 was explored using Python, Pandas, Matplotlib, and Seaborn. The analysis covers sales trends, product popularity, country performance, revenue distribution, customer purchase behavior, and purchase timing. The findings also guide the choices made in the RFM segmentation phase.

---

## Dataset Used

| Attribute | Details |
|---|---|
| Dataset | Online Retail II (cleaned in Phase 2) |
| Records | 1,003,336 transaction lines |
| Invoices | 39,514 |
| Products (Stock Codes) | 4,723 |
| Countries | 43 |
| Identified Customers | 5,852 (rows with a Customer ID: 776,575) |
| Total Revenue | £19,397,657 |
| Time Period | 1 December 2009 – 9 December 2011 |

Sales, product, country, and timing analysis use the full cleaned dataset. Customer-level analysis uses only rows with a Customer ID, which cover 86.7% of revenue.

---

## EDA Workflow

| Step | Analysis | Techniques |
|---|---|---|
| 01 | Summary statistics | Descriptive statistics for quantity, price, and sales |
| 02 | Sales trends over time | Line chart of monthly revenue |
| 03 | Product popularity | Bar charts of top products by units and revenue |
| 04 | Country performance | Pie chart and bar chart |
| 05 | Revenue distribution | Histogram and boxplot of invoice value |
| 06 | Customer purchase frequency | Histogram of invoices per customer |
| 07 | Purchase timing | Seaborn heatmap of day of week by hour |
| 08 | Frequency vs monetary value | Scatter plot and correlation |
| 09 | Revenue concentration | Cumulative revenue curve across customers |
| 10 | Insights and implications | Summary for sales analysis and RFM |

---

## Summary Statistics

| Measure | Median | Mean | 99th Percentile | Maximum |
|---|---:|---:|---:|---:|
| Quantity per line | 4 | 11.0 | 108 | 19,152 |
| Unit price (£) | 2.10 | 3.34 | 16.95 | 1,157.15 |
| Sales per line (£) | 10.08 | 19.30 | 179.00 | 38,970.00 |
| Value per invoice (£) | 301 | 491 | 4,098 | 52,941 |

A typical invoice contains 15 line items (median) and about 148 units. The mean is well above the median for every measure, which shows that a small number of large orders pull the averages up. Medians are therefore the more reliable summary of a typical order.

---

## 1. Sales Trends Over Time

![Monthly Revenue](images/01_monthly_revenue.png)

- Revenue follows a clear **seasonal pattern**. September to November produced 36.1% of revenue in the first 12 months (Dec 2009 – Nov 2010) and 37.5% in the second (Dec 2010 – Nov 2011).
- **November is the peak month** in both years: £1.43M in November 2010 and £1.45M in November 2011 (15.2% of the second 12-month period's revenue).
- The weakest months were February and April 2011, at roughly £0.51M each. From January to August 2011, monthly revenue averaged about £650K.
- Year-on-year growth is modest. Revenue for Dec 2010 – Nov 2011 was £9.55M, against £9.40M for Dec 2009 – Nov 2010, an increase of **1.7%**.
- **December 2011 is a partial month** (data ends on 9 December), so its low value of £446K is not a decline and is shown as a dashed line. The full months of December 2009 (£798K) and December 2010 (£776K) are comparable.

---

## 2. Product Popularity

![Top Products](images/02_top_products.png)

| Rank | Top by units sold | Units | Top by revenue | Revenue |
|---:|---|---:|---|---:|
| 1 | World War 2 Gliders Asstd Designs | 106,139 | Regency Cakestand 3 Tier | £330,590 |
| 2 | Jumbo Bag Red Retrospot | 97,176 | White Hanging Heart T-Light Holder | £261,169 |
| 3 | Pack of 72 Retrospot Cake Cases | 94,884 | Jumbo Bag Red Retrospot | £182,681 |
| 4 | White Hanging Heart T-Light Holder | 94,719 | Party Bunting | £148,318 |
| 5 | Small Popcorn Holder | 88,499 | Assorted Colour Bird Ornament | £129,324 |

- **Volume and revenue tell different stories.** The best-selling product by units (World War 2 Gliders, 106,139 units) earned only £24,446, while the Regency Cakestand sold 26,478 units and earned £330,590. Four products appear in both top-10 lists: Jumbo Bag Red Retrospot, White Hanging Heart T-Light Holder, Assorted Colour Bird Ornament, and Small Popcorn Holder.
- White Hanging Heart T-Light Holder appears on the most invoices (5,464), making it the most widely purchased item.
- Revenue is **spread across a broad catalogue**. The top 10 products make up only 7.6% of revenue. About 290 products (6.1% of the range) generate half of the revenue, and about 1,041 products (22%) generate 80%.
- 118 products appear on only a single invoice, which suggests a long tail of slow-moving items.

---

## 3. Country-wise Sales Performance

![Country Revenue](images/03_country_revenue.png)

| Country | Revenue | Share | Invoices | Customers | Average Invoice |
|---|---:|---:|---:|---:|---:|
| United Kingdom | £16,554,814 | 85.3% | 36,182 | 5,334 | £458 |
| EIRE (Ireland) | £623,414 | 3.2% | 581 | 3 | £1,073 |
| Netherlands | £549,773 | 2.8% | 216 | 22 | £2,545 |
| Germany | £383,289 | 2.0% | 753 | 107 | £509 |
| France | £311,090 | 1.6% | 598 | 93 | £520 |
| Australia | £167,800 | 0.9% | 89 | 15 | £1,885 |

- The **United Kingdom accounts for 85.3% of revenue**, so country charts must show the UK separately or the other 42 countries disappear. Outside the UK, revenue totals £2.84M (14.7%), and the top five export markets account for 71.6% of it.
- Export revenue is concentrated in **a few large accounts**. EIRE generated £623K from only 3 identified customers, and the Netherlands generated £550K from 22 customers at an average invoice of £2,545 (more than five times the UK average of £458). These look like wholesale buyers, not typical retail customers.
- Germany and France contribute through many more customers (107 and 93) at invoice values close to the UK level.

---

## 4. Revenue and Order Value Distribution

![Invoice Value Distribution](images/04_invoice_value_distribution.png)

- Invoice values are **heavily right-skewed** (skewness 18.2). The median invoice is £301, while the mean is £491.
- 3,491 invoices (8.8%) are flagged as outliers by the boxplot rule, with values up to £52,941. These are large bulk orders consistent with a wholesale business, not data errors, so they were **kept**. A log scale is used for visualization.
- At line level, lines with 100 or more units are only 1.3% of all lines but account for **30.8% of all units sold**.

---

## 5. Customer Purchase Behavior

![Customer Frequency](images/05_customer_frequency.png)

| Measure | Value |
|---|---|
| Customers analysed | 5,852 |
| Invoices per customer (median / mean / max) | 3 / 6.3 / 373 |
| One-time buyers | 1,619 (27.7%) |
| Customers with 2–3 invoices | 27.4% |
| Customers with 10 or more invoices | 16.4% |
| Spend per customer (median / mean) | £856 / £2,875 |
| Largest customer spend | £580,987 (Customer 18102) |
| Customers active in the last 90 days of the data | 49.4% |
| Customers with no purchase in the last 180 days | 40.7% |

- The customer base splits into a large group of **occasional buyers** (over half of customers placed three or fewer orders) and a smaller group of **highly frequent buyers** (16.4% placed ten or more).
- Almost half of customers (49.4%) bought within the final 90 days, and about 41% have been inactive for more than 180 days. This spread in recency is what the RFM analysis will use to separate active customers from those at risk or lost.

### Revenue Concentration

![Revenue Concentration](images/08_revenue_concentration.png)

| Customer Group | Share of Revenue (identified customers) |
|---|---:|
| Top 1% | 31.3% |
| Top 10% | 63.4% |
| Top 20% | 76.8% |
| Bottom 50% | 6.6% |
| Repeat customers (2+ invoices) | 96.7% |

Revenue depends heavily on a small group of high-value customers. The top 10% of customers generate about 63% of revenue from identified customers, while the bottom half generates under 7%.

---

## 6. Purchase Timing

![Weekday and Hour Heatmap](images/06_weekday_hour_heatmap.png)

| Day | Share of Revenue | Invoices |
|---|---:|---:|
| Monday | 17.6% | 6,245 |
| Tuesday | 19.6% | 7,146 |
| Wednesday | 17.4% | 7,115 |
| Thursday | 20.7% | 8,167 |
| Friday | 15.5% | 5,987 |
| Saturday | 0.1% | 30 |
| Sunday | 9.2% | 4,824 |

- **Thursday is the strongest day** (20.7% of revenue, 8,167 invoices), followed by Tuesday.
- **Saturday has almost no trading** (30 invoices in two years), which points to a business that does not operate on Saturdays.
- Trading is concentrated around midday. 78.1% of invoices are placed between 10:00 and 15:59, and the 12:00 hour alone accounts for 14.4% of revenue.
- Thursday is the only day with meaningful **evening activity** (360 invoices in the 18:00 hour and 288 in the 19:00 hour), while other weekdays are close to zero after 18:00.

---

## 7. Relationship Between Frequency and Monetary Value

![Frequency vs Monetary](images/07_frequency_vs_monetary.png)

Customers who order more often also spend more. The Spearman correlation between the number of invoices and total spend is **0.86**, a strong positive relationship. Both measures span several orders of magnitude, so a log scale is used.

---

## Key Insights

| Area | Insight |
|---|---|
| Seasonality | Revenue peaks every November; Sep–Nov brings about 37% of annual revenue |
| Growth | Year-on-year revenue growth is only 1.7% (Dec 2010 – Nov 2011 vs the prior 12 months) |
| Products | Unit volume does not equal revenue; revenue is spread over a wide catalogue |
| Geography | The UK provides 85.3% of revenue; export income comes from a few wholesale accounts |
| Order value | Right-skewed, with median £301 against mean £491; bulk orders are legitimate |
| Customers | 27.7% buy only once; the top 10% of customers generate 63.4% of revenue |
| Timing | Orders peak at midday and on Thursdays; Saturdays are almost empty |

---

## Data Limitations

- **Missing Customer IDs.** Customer-level findings cover the 86.7% of revenue that has a Customer ID. Invoices without an ID are larger on average (£881 vs £460), so customer-level analysis may understate bulk buyers.
- **Two years of data.** Seasonality is based on only two November peaks, so it should be treated as a consistent pattern, not a proven cycle.
- **Partial December 2011.** Excluded from all trend comparisons.

---

## Implications for the Next Phases

- **Sales analysis:** analyse the UK and export markets separately, exclude December 2011 from trend comparisons, and rank products by revenue as well as units.
- **RFM segmentation:** use a snapshot date of 10 December 2011. Because Monetary and Frequency are highly skewed and strongly correlated (ρ = 0.86), use quantile-based scores, not fixed thresholds, and consider reviewing the very largest accounts separately so they do not dominate the segments.
- **Business strategy:** the large one-time buyer group (27.7%) and the 41% of customers inactive for six months are the clearest retention opportunities.

---

## Outcome

The EDA established how sales, products, countries, and customers behave in the Online Retail II data. It confirmed strong seasonality with a November peak, a catalogue where revenue is widely distributed, a business dominated by the UK with a handful of large export accounts, and a customer base in which a small share of buyers generates most of the revenue.

These findings define the analysis choices for the sales analysis and RFM customer segmentation phases that follow.


