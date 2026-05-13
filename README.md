# 💳 Credit Card Analytics Dashboard — Power BI

> **2 Interactive Dashboards | DAX Measures | Customer & Transaction Intelligence**

[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi&logoColor=white)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Calculations-orange)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/Power%20Query-ETL-blue)](https://learn.microsoft.com/en-us/power-query/)
[![License: MIT](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)

---

## 🔗 Live Dashboard

👉 **[View Interactive Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMmVlOTE2NmEtNmE2NC00ZDE4LTliNmMtZmI2N2E3NDVmOWI5IiwidCI6IjVjZTE4MWM3LTA1NTktNDUzYS1hNGJjLWIwNDMxN2RkMzIzZiJ9)**


![image alt](https://github.com/ParthPatilAnalyst/Credit-Card-Dashboard/blob/88e3747007fbb22f788115b6ebacee8b8f7be5f1/Dashboard%20page%201.png)
![image alt](https://github.com/ParthPatilAnalyst/Credit-Card-Dashboard/blob/88e3747007fbb22f788115b6ebacee8b8f7be5f1/Dashboard%20page%202.png)

---

## 🌟 Situation

Financial organisations rely on credit card data to understand customer value, spending behaviour, and revenue performance — but raw transactional data stored across disconnected files offers no visibility on its own. Decision-makers were forced to wait on slow, manually compiled static reports that showed no segmentation, no week-over-week trends, and no way to interrogate the data interactively.

The core problem was fragmentation: customer demographic records and transaction financial records existed in separate CSV files with no integration, no standardised categories, and no calculated metrics. This made it impossible to answer even basic business questions — which income group generates the most revenue? Is revenue growing week-over-week? Which spending categories drive card usage?

The need was a **centralised, always-on analytics platform** that merged these data sources, cleaned and modelled them correctly, and delivered live, interactive dashboards for both customer and transaction intelligence.

---

## 🎯 Task

The project was built to eliminate six specific pain points faced before the dashboard existed:

| Pain Point | Target Outcome |
|---|---|
| Data stored in separate, unlinked files | Single unified data model with a defined relationship |
| Static reports requiring manual updates | Fully dynamic dashboards with auto-refreshing visuals |
| No customer segmentation | Age group and income group segmentation via DAX columns |
| No real-time KPI tracking | Live KPI cards for revenue, transactions, and interest earned |
| No trend or growth visibility | Week-over-week revenue comparison with % change |
| Slow, inefficient decision-making | Self-service, slicer-driven exploration for all stakeholders |

Deliverables: two fully interactive Power BI dashboards — a **Customer Analysis Dashboard** and a **Transaction Analysis Dashboard** — connected through a shared data model with DAX-powered KPIs.

---

## ⚙️ Action

### 1. Data Sources

Two CSV datasets were used as the foundation:

**Customer Dataset** — demographic and behavioural fields:
`Client Number · Age · Gender · Income · Education Level · Job Role · Marital Status · Satisfaction Score`

**Transaction Dataset** — financial and transactional fields:
`Transaction Amount · Transaction Volume · Credit Limit · Interest Earned · Spending Category · Transaction Method · Weekly Date`

---

### 2. Data Cleaning & Transformation (Power Query)

All raw data was processed through Power Query before loading into the model:

- Converted all columns to correct data types
- Removed duplicate records across both datasets
- Handled missing and null values
- Standardised categorical text fields (e.g., `male` / `Male` / `M` → `Male`)
- Trimmed whitespace and cleaned inconsistent string entries
- Ensured referential integrity between the two datasets on `Client_Num`

---

### 3. Data Modelling

A clean star-schema-style model was built with two tables:

```
customer_data  (Dimension Table)
      │
      │  One-to-Many on Client_Num
      ▼
cc_detail      (Fact Table)
```

This structure enables accurate cross-filtering, faster query performance, and consistent slicer behaviour across both dashboards.

---

### 4. DAX Calculations

**Calculated Columns** (for segmentation):

```dax
-- Age group segmentation
Age Group = 
SWITCH(TRUE(),
    customer_data[Age] < 30, "20s",
    customer_data[Age] < 40, "30s",
    customer_data[Age] < 50, "40s",
    customer_data[Age] < 60, "50s",
    "60+"
)

-- Income group segmentation
Income Group = 
SWITCH(TRUE(),
    customer_data[Income] < 35000, "Low",
    customer_data[Income] < 70000, "Medium",
    "High"
)
```

**Measures** (for KPI reporting):

```dax
-- Week-over-week revenue comparison
Current Week Revenue = 
CALCULATE(SUM(cc_detail[Revenue]),
    FILTER(ALL(cc_detail), cc_detail[Week_Num] = MAX(cc_detail[Week_Num])))

Previous Week Revenue = 
CALCULATE(SUM(cc_detail[Revenue]),
    FILTER(ALL(cc_detail), cc_detail[Week_Num] = MAX(cc_detail[Week_Num]) - 1))

WoW Revenue % = 
DIVIDE([Current Week Revenue] - [Previous Week Revenue],
       [Previous Week Revenue], 0)
```

---

### 5. Dashboard 1 — Customer Analysis

**Purpose:** Understand who the customers are and which segments drive value.

**Visuals:** Bar charts · Donut charts · Pie charts · KPI cards

**Key questions answered:**
- Which age group generates the highest revenue?
- Which income segment (Low / Medium / High) is most valuable?
- How does revenue split by gender?
- What is the distribution of customers across job roles and education levels?

---

### 6. Dashboard 2 — Transaction Analysis

**Purpose:** Track financial performance and identify spending trends.

**Visuals:** Line charts · Treemaps · Bar charts · KPI cards

**Key questions answered:**
- What is this week's revenue vs. last week?
- Which spending categories drive the most card usage?
- Which transaction methods are most common?
- What is the trend in interest earned over time?

---

### 7. Interactivity Features

- **Slicers** — Gender, Age Group, Income Group, Week, Spending Category
- **Drill-down / Drill-through** — from summary to individual transaction level
- **Custom tooltips** — additional context on hover
- **Synced filters** — slicers apply consistently across both dashboard pages
- **Dynamic visuals** — all charts update automatically on every filter change

---

## 📊 Result

### Business Impact

| Metric | Before | After |
|---|---|---|
| Reporting turnaround | Manual, multi-hour process | Real-time, self-service |
| Customer segmentation | None | Age group + Income group |
| Revenue trend visibility | None | Week-over-week % change |
| Data integration | Two disconnected files | Unified relational model |
| Stakeholder access | Static PDF reports | Live interactive dashboard |

### Key Insights Surfaced

- **High-income customers** contribute a disproportionate share of total revenue despite being a smaller segment — retention of this group is critical.
- **Week-over-week revenue tracking** revealed seasonal dips and spikes that were previously invisible in monthly static reports.
- **Age group segmentation** showed mid-career customers (40s) as the highest-value cohort by average transaction amount.
- **Spending category analysis** identified which merchant categories generate the most card volume — directly informing rewards programme design.
- **Interest earned trends** highlighted customers most likely to carry a balance, enabling targeted financial product offerings.

### Live Dashboard

The published dashboard is accessible to stakeholders without any Power BI licence via the public link — enabling organisation-wide visibility with zero additional tooling cost.

👉 **[Open Live Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMmVlOTE2NmEtNmE2NC00ZDE4LTliNmMtZmI2N2E3NDVmOWI5IiwidCI6IjVjZTE4MWM3LTA1NTktNDUzYS1hNGJjLWIwNDMxN2RkMzIzZiJ9)**

---

## 📁 Repository Structure

```
├── Credit_Card_Dashboard.pbix     # Power BI project file (both dashboards)
└── README.md                      # This file
```

---

## 🚀 Getting Started

### Prerequisites

- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free download)

### Run Locally

```bash
git clone https://github.com/your-username/credit-card-analytics-dashboard.git
```

1. Open `Credit_Card_Dashboard.pbix` in Power BI Desktop.
2. If prompted, reconnect the data source to your local CSV files.
3. Click **Refresh** to reload data.
4. Use the slicers on each dashboard page to explore insights.

---

## 🔮 Future Enhancements

- Connect to a live SQL database instead of static CSV files
- Add revenue forecasting using Power BI's built-in AI visuals
- Build a customer churn prediction model integrated into the dashboard
- Add row-level security (RLS) for role-based access control
- Expand KPIs to include credit utilisation rate and delinquency flags

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
