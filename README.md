

# Credit Card Analytics Dashboard — Power BI Project

## Introduction

The **Credit Card Analytics Dashboard** is a comprehensive business intelligence project developed using Microsoft Power BI. The primary aim of this project is to convert raw and unstructured credit card data into meaningful insights through interactive and user-friendly dashboards.

In today’s data-driven environment, organizations require fast and accurate insights to make decisions. This project addresses that need by providing a centralized analytics solution that helps stakeholders understand customer behavior, spending patterns, and overall revenue performance.

![image alt](https://github.com/ParthPatilAnalyst/Credit-Card-Dashboard/blob/dbcddf55cd29d444acc9488cc377040d25b71568/1.png)
![image alt](https://github.com/ParthPatilAnalyst/Credit-Card-Dashboard/blob/dbcddf55cd29d444acc9488cc377040d25b71568/2.png)

---

## Project Description

This project is designed as an end-to-end analytics solution that combines **data cleaning, data modeling, DAX calculations, and dashboard visualization** into a single workflow.

The solution consists of two main dashboards:

* **Customer Dashboard** — focuses on customer demographics and segmentation
* **Transaction Dashboard** — focuses on financial performance and transaction trends

Both dashboards are fully interactive and allow users to explore data at multiple levels using filters and drill-down features.

---

## Problem Statement

Before implementing this dashboard, the organization faced several challenges:

* Data was stored in separate files with no integration
* Reports were static and required manual updates
* No proper segmentation of customers
* Lack of real-time performance tracking
* Difficulty in identifying trends and patterns
* No week-over-week comparison of revenue

These issues made decision-making slow and inefficient.

---

## Solution Approach

To solve these problems, a structured approach was followed:

1. Combine customer and transaction datasets
2. Clean and transform data using Power Query
3. Build a relational data model
4. Create calculated columns for segmentation
5. Develop DAX measures for KPIs
6. Design interactive dashboards for analysis

This approach ensures accuracy, scalability, and ease of use.

---

## Project Objectives

* Provide a unified view of customer and transaction data
* Enable real-time monitoring of KPIs
* Perform customer segmentation based on age and income
* Analyze transaction trends over time
* Track revenue growth using weekly comparisons
* Support data-driven decision-making

---

## Tools & Technologies

* **Microsoft Power BI Desktop** – Used for dashboard development
* **Power Query (M Language)** – Used for data transformation and cleaning
* **DAX (Data Analysis Expressions)** – Used for calculations and measures
* **CSV Files** – Used as source data
* **Power BI Data Model** – Used to create relationships
* **GitHub** – Used for version control and documentation

---

## Dataset Description

### Customer Dataset

Contains demographic and behavioral information:

* Client Number
* Age
* Gender
* Income
* Education Level
* Job Role
* Marital Status
* Satisfaction Score

### Transaction Dataset

Contains financial and transactional data:

* Transaction Amount
* Transaction Volume
* Credit Limit
* Interest Earned
* Spending Category
* Transaction Method
* Weekly Date

---

## Data Cleaning & Transformation

Data preparation is one of the most important steps in this project. The following transformations were performed:

* Converted columns into correct data types
* Removed duplicate records
* Handled missing and null values
* Standardized categorical values (e.g., Male/Female)
* Trimmed and cleaned text fields
* Ensured consistency across datasets

This step ensures high data quality and reliable analysis.

---

## Data Modeling

A proper data model was created to ensure performance and scalability.

### Model Design

* **customer_data** (dimension table)
* **cc_detail** (fact table)
* Relationship: One-to-Many using `Client_Num`

### Benefits

* Faster data processing
* Accurate filtering across visuals
* Better user experience

---

## DAX Calculations

### Calculated Columns

* Age Group (for segmentation)
* Income Group (Low, Medium, High)
* Week Number (for time analysis)

### Measures

* Total Revenue
* Current Week Revenue
* Previous Week Revenue
* Week-over-Week Revenue %

These calculations allow dynamic and flexible reporting.

---

## Dashboard 1: Customer Analysis

### Purpose

To understand customer demographics and behavior.

### Key Insights

* Which age group generates more revenue
* Which income segment is most valuable
* Gender-based revenue comparison
* Customer distribution across categories

### Visuals Used

* Bar charts
* Donut charts
* Pie charts
* KPI cards

---

## Dashboard 2: Transaction Analysis

### Purpose

To analyze financial performance and transaction trends.

### Key Insights

* Weekly revenue performance
* Growth or decline in revenue
* Spending behavior across categories
* Usage patterns of credit cards

### Visuals Used

* Line charts
* Treemaps
* Bar charts
* KPI cards

---

## Interactivity Features

* Slicers for filtering (Gender, Age, Income, Week, Category)
* Drill-down and drill-through functionality
* Custom tooltips for additional insights
* Synced filters across dashboards
* Dynamic visuals that update automatically

---

## Business Impact

After implementing this dashboard:

* Reporting time reduced significantly
* Decision-making became faster
* Improved understanding of customer segments
* Better tracking of revenue performance
* Easy identification of trends and patterns

---

## Project Workflow

1. Data Understanding
2. Data Cleaning
3. Data Modeling
4. DAX Calculations
5. Dashboard Design
6. Testing and Validation

---



## How to Run the Project

1. Download the Power BI `.pbix` file
2. Open it in Power BI Desktop
3. Load or refresh the dataset
4. Use filters to explore insights

---

## Future Enhancements

* Add predictive analytics (forecasting revenue)
* Connect to live database instead of CSV
* Add customer churn prediction
* Improve UI design and user experience
* Include more advanced KPIs


---


## Conclusion

This project demonstrates strong practical knowledge of data analytics, Power BI, and business intelligence concepts. It highlights the ability to convert raw data into actionable insights and build professional dashboards that support real-world business decisions.


