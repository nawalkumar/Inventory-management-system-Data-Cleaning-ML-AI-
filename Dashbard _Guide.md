PowerBI Dashboard Guide: Intelligent Forecasting & Inventory Management System
Introduction
This guide walks you through building (or importing) the interactive PowerBI dashboard for the project. The dashboard visualizes sales trends, forecasts demand, optimizes inventory, and provides customer/product insights—enabling data-driven decisions like reorder alerts.
Pages Overview:

Overview: High-level KPIs (e.g., total sales, turnover ratio).
Forecasting: Time series predictions with uncertainty.
Inventory Optimization: Stock levels and cost breakdowns.
Customer & Product Insights: RFM clusters and recommendations.

Expected Output: A .pbix file with slicers (e.g., date/product), drill-downs, and conditional formatting. Refresh with new data for real-time updates.
Time to Build: 2-4 hours (faster if using templates).
Prerequisites

PowerBI Desktop: Download from Microsoft (free).
Data Files:

cleaned_sales_data.csv (main fact table).
rfm_analysis.csv (customer segments).
prophet_forecast.csv (forecasts; export from Python: forecast.to_csv('prophet_forecast.csv')).
inventory_results.csv (optimization table; export from Python: results_df.to_csv('inventory_results.csv')).


Skills: Basic PowerBI (import, visuals, relationships). No DAX experience needed—samples provided.

Step-by-Step Build Instructions
Open PowerBI Desktop and follow these steps. Use "Get Data > Text/CSV" for imports.
1. Import Data & Set Up Model

Load Tables:

Import cleaned_sales_data.csv as 'Sales' (fact table).
Import rfm_analysis.csv as 'RFM' (related via 'customer_name').
Import prophet_forecast.csv as 'Forecasts' (related via 'ds' date).
Import inventory_results.csv as 'Inventory' (related via 'product_code').


Create Relationships:

Model view > Drag 'customer_name' from Sales to RFM.
Drag 'date' from Sales to Forecasts['ds'] (one-to-many).
Drag 'product_code' from Sales to Inventory.
Ensure active relationships; set cross-filter to "Both" for slicers.


Date Hierarchy:

Right-click 'date' in Sales > Mark as Date Table.
Create hierarchy: Year > Month > Day.


Add Calculated Columns (optional, for enrichment):

In Sales: Sales Growth % = DIVIDE([Sales] - CALCULATE([Sales], PREVIOUSMONTH(Sales[date])), CALCULATE([Sales], PREVIOUSMONTH(Sales[date])))



2. Build Pages & Visuals
Create 4 pages (Insert > New Page). Use the layout: Top: Title/Slicers; Middle: KPIs/Charts; Bottom: Tables.
Page 1: Overview

Slicers (top row): Date (hierarchy), Product Code, Customer Name, City (sync across pages).
KPIs (cards, middle row):

Total Sales: Visual > Card > Field: SUM(Sales[Sales]).
Inventory Turnover: Use DAX measure below.
Forecast Accuracy: Card with fixed value (e.g., 85%) or DAX: Accuracy % = 100 - (AVERAGE(Forecasts[MAE]) / AVERAGE(Forecasts[yhat]) * 100).


Main Visual: Line + Clustered Column Chart (Sales[Sales] as line, Forecasts[yhat] as column; X-axis: Date).
Formatting: Theme > Import custom (e.g., blue/green scheme). Add text box: "Executive Snapshot".

Page 2: Forecasting

Slicers: Product Code, Date Range.
Main Visual: Line Chart (Actual: Sales[Sales]; Predicted: Forecasts[yhat]; X: Date). Add shaded area for uncertainty: Analytics > Forecast (or use yhat_lower/upper as error bars).
Supporting Visuals:

Heatmap: Matrix (Rows: Month, Columns: Year, Values: SUM(Sales[Sales]))—color by value.
Model Comparison: Table (Columns: Model Name, RMSE; hardcode rows or import from CSV).


KPI: Card for Next Month Demand: Next Demand = MAX(Forecasts[yhat]).

Page 3: Inventory Optimization

Slicers: Product Code, Territory.
Main Visual: Clustered Bar Chart (X: Product_Code, Y: Optimal_Inventory from Inventory table).
Supporting Visuals:

Donut Chart: Cost Breakdown (Holding, Order; Values from Inventory[Monthly_Holding_Cost], etc.).
Table: Reorder Alerts (Columns: Product_Code, Demand_Units, Optimal_Inventory; Conditional: Red if Optimal < Demand * 0.8).


KPI: Min Total Cost: Card with SUM(Inventory[Total_Cost_per_Product]).

Page 4: Customer & Product Insights

Slicers: Deal Size, City.
Main Visual: Scatter Plot (RFM: X=Monetary, Y=Frequency, Bubble=Recency; Color by segment from RFM).
Supporting Visuals:

Horizontal Bar: Top Customers (X: SUM(Sales[Sales]), Y: Customer_Name).
Scatter: Product Clusters (X: Sales[Sales], Y: Sales[price_each], Color: Cluster from calculated column).
Table: Recommendations (import matrix; or hardcoded samples).


KPI: Customer Lifetime Value: SUM(RFM[monetary]).

3. Add Interactivity & Polish

Cross-Filtering: Select a product slicer—watches all visuals update.
Drill-Through: Right-click chart > Drill Through (e.g., from Overview to Forecasting).
Bookmarks: For guided tours (e.g., "Forecast View" hides non-forecast visuals).
Themes: File > Options > Themes > Browse for JSON (e.g., corporate blue).
Tooltips: Edit visual > Tooltip > Add fields (e.g., "Sales Breakdown: {SUM(Sales[Sales])}").
Mobile Layout: View > Mobile > Adjust for phone.

4. Key DAX Measures
Add these via Modeling > New Measure (copy-paste):

Inventory Turnover:
textInventory Turnover = DIVIDE(SUM(Sales[Sales]), AVERAGE(Inventory[Optimal_Inventory]))

YoY Sales Growth:
textYoY Growth % = 
VAR CurrentYearSales = CALCULATE(SUM(Sales[Sales]), SAMEPERIODLASTYEAR(Sales[date]))
RETURN DIVIDE(SUM(Sales[Sales]) - CurrentYearSales, CurrentYearSales)

Safety Stock Alert:
textStock Alert = IF(AVERAGE(Inventory[Optimal_Inventory]) < AVERAGE(Inventory[Demand_Units]) * 0.8, "Low Stock", "OK")

Forecast Error:
textMAE = AVERAGE(ABS(Forecasts[y] - Forecasts[yhat]))


Export & Share

Save as .pbix: File > Save As.
Publish: Home > Publish (to PowerBI Service; free account needed for sharing).
Export Report: File > Export > PDF/PowerPoint (for static views).
Embed: In GitHub README via iframe (PowerBI embed code).

Troubleshooting

No Data in Visuals: Check relationships (Model view > Manage Relationships).
Date Errors: Ensure 'date' is Date type; use Calendar table if issues.
Slow Refresh: Limit rows (e.g., filter to top products); use DirectQuery for large CSVs.
DAX Errors: Syntax? Wrap in IF(ISBLANK(...), BLANK(), ...). Test in DAX Studio (free tool).
CSV Issues: Re-export from Python; ensure UTF-8 encoding.

Next Steps

Enhance: Add AI visuals (e.g., key influencers for sales drivers).
Automate: Use PowerBI Dataflows for Python script integration.
Templates: Start from Microsoft Sales Dashboard Sample and adapt.

For questions, open a GitHub issue. Happy visualizing! 📊
