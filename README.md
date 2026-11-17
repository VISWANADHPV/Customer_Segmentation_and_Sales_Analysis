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

- 
