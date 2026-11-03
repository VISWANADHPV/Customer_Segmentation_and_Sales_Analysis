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
