# 📊 Power BI Dashboard Guide  
## Intelligent Forecasting & Inventory Management System

---

## 🚀 Overview

This dashboard provides interactive insights for:

- 📈 Demand Forecasting  
- 📦 Inventory Optimization  
- 👥 Customer Segmentation  
- 📊 Sales Performance  

**Pages:**
- Overview  
- Forecasting  
- Inventory  
- Customer Insights  

---

## 🧰 Prerequisites

- Power BI Desktop  
- CSV Files:
  - cleaned_sales_data.csv  
  - rfm_analysis.csv  
  - prophet_forecast.csv  
  - inventory_results.csv  

---

## ⚙️ Setup

### 1. Import Data
Home → Get Data → Text/CSV  
Load as:
- Sales  
- RFM  
- Forecasts  
- Inventory  

---

### 2. Create Relationships

- Sales[customer_name] → RFM  
- Sales[date] → Forecasts[ds]  
- Sales[product_code] → Inventory  

📌 Set cross-filter = **Both**

---

## 📊 Key Visuals

### 🔹 Overview
- KPIs: Total Sales, Inventory Turnover  
- Chart: Actual vs Forecast  

---

### 🔹 Forecasting
- Line Chart: Sales vs Predictions  
- KPI: Next Month Demand  

---

### 🔹 Inventory
- Bar Chart: Optimal Inventory  
- Table: Stock Alerts  

---

### 🔹 Insights
- Scatter: RFM Segmentation  
- Top Customers & Products  

---

## 🧮 Important DAX

```DAX
Inventory Turnover =
DIVIDE(SUM(Sales[Sales]), AVERAGE(Inventory[Optimal_Inventory]))
Stock Alert =
IF(AVERAGE(Inventory[Optimal_Inventory]) < AVERAGE(Inventory[Demand_Units])*0.8,
"Low Stock","OK")
```
