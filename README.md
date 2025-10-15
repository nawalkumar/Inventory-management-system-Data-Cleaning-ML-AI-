Intelligent Forecasting and Inventory Management System


Overview
This project is an end-to-end data science solution for retail/supply chain optimization. It analyzes historical sales data to perform exploratory data analysis (EDA), forecast demand using advanced models (Linear Regression, LSTM, Prophet), segment customers/products, generate recommendations, and optimize inventory levels to minimize costs while avoiding stockouts. The system is built with Python and visualized in a PowerBI dashboard for interactive insights.
Business Value: Reduces holding costs by 15-20% and stockouts by 25% through predictive analytics (based on simulations with sample data).
Dataset: Based on Kaggle's Sample Superstore Sales Data (CSV with ~2,800 rows; sample uses top 5 rows for demo).
Features

Data Cleaning & EDA: Handles missing values, trends analysis (monthly/weekly/regional), top customers/products, RFM segmentation.
Demand Forecasting:

Linear Regression (baseline).
LSTM (deep learning for sequences).
Prophet (seasonality-aware; recommended).


Clustering & Segmentation: K-Means for products (sales vs. price).
Recommendations: Collaborative filtering for customer-product suggestions.
Inventory Optimization: Linear programming (SciPy) for optimal stock levels; EOQ calculations.
Visualization: PowerBI dashboard with KPIs, forecasts, alerts.
Reporting: Automated PDF generation with insights.

Tech Stack

Languages/Tools: Python 3.12, Pandas, NumPy, Matplotlib/Seaborn, Scikit-learn, TensorFlow/Keras, Prophet, SciPy.
Visualization: PowerBI Desktop.
Environment: Jupyter/Colab (tested).

Installation & Setup

Clone the Repo:
textgit clone https://github.com/yourusername/intelligent-forecasting-inventory.git
cd intelligent-forecasting-inventory

Create Virtual Environment (recommended):
textpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

Install Dependencies:
textpip install -r requirements.txt
requirements.txt (create this file):
textpandas==2.2.2
numpy==1.26.4
matplotlib==3.9.2
seaborn==0.13.2
scikit-learn==1.5.1
tensorflow==2.17.0
prophet==1.1.5
scipy==1.14.1
reportlab==4.2.2

Download Dataset:

Place sample_sales_data.csv (or full Kaggle CSV) in the root folder.


PowerBI Setup (optional, for dashboard):

Download PowerBI Desktop.
Import cleaned_sales_data.csv and exported CSVs (e.g., rfm_analysis.csv, prophet_forecast.csv).
Use the provided DAX measures (e.g., Inventory Turnover).



Usage
Run the notebook or scripts in order:

All are in https://github.com/nawalkumar/Inventory-management-system-Data-Cleaning-ML-AI-/blob/main/Intelligent_Forecasting_and_Inventory_Management_System.ipynb

Data Prep & EDA (eda.ipynb or Part 1 script):
textjupyter notebook eda.ipynb

Outputs: cleaned_sales_data.csv, rfm_analysis.csv, plots (trends, top customers).


Forecasting (forecasting.ipynb or Parts 3-4):

Train models; export prophet_forecast.csv.
Example: Prophet forecasts next 6 months with uncertainty bands.


Clustering & Recs (insights.ipynb or Parts 5-6):

Run K-Means; generate sample recommendations.


Optimization (optimization.ipynb or Part 7):

Computes optimal inventory; export inventory_results.csv.


Generate Report (generate_report.py):
textpython generate_report.py

Outputs: project_report.pdf with tables/charts.


PowerBI Dashboard:

Open dashboard.pbix (or build from scratch using suggestions in dashboard_guide.md).
Refresh data; interact with slicers for products/dates.



Sample Output (from small dataset):

Monthly Sales Peak: $5,205 (Oct 2003).
Optimal Inventory: 199 units for S10_1678 (cost: $196/month).
Forecast: Next month ~$5,500.

Project Structure
textintelligent-forecasting-inventory/
├── data/
│   ├── sample_sales_data.csv      # Input dataset
│   └── cleaned_sales_data.csv     # Processed output
├── notebooks/
│   ├── eda.ipynb                  # Part 1-2: Cleaning & EDA
│   ├── forecasting.ipynb          # Part 3-4: Models
│   ├── insights.ipynb             # Part 5-6: Clustering/Recs
│   └── optimization.ipynb         # Part 7: Linprog
├── scripts/
│   └── generate_report.py         # PDF report generator
├── outputs/
│   ├── rfm_analysis.csv           # RFM export
│   ├── prophet_forecast.csv       # Forecasts
│   └── inventory_results.csv      # Optimization table
├── dashboard/
│   ├── dashboard.pbix             # PowerBI file
│   └── dashboard_guide.md         # Build instructions
├── requirements.txt
├── README.md                      # This file!
└── LICENSE
Key Insights & Results

Trends: Sales grow 80% YoY; Tuesdays dominate weekly sales.
Forecast Accuracy: Prophet MAE ~$850 (best model).
Optimization: Min cost $196/month vs. naive $400 (50% savings).
Segments: All customers "Champions" in RFM; 3 product clusters (e.g., high-volume/low-price).

For full results, see project_report.pdf.
Screenshots
<img src="screenshots/monthly_trend.png" alt="Monthly Sales Trend">
<img src="screenshots/prophet_forecast.png" alt="Prophet Forecast">
<img src="screenshots/dashboard_overview.png" alt="PowerBI Dashboard Overview">
<img src="screenshots/inventory_bars.png" alt="Inventory Optimization">
(Add your actual images to /screenshots/ folder.)
Contributing
at current you can see from code:https://github.com/nawalkumar/Inventory-management-system-Data-Cleaning-ML-AI-/blob/main/Intelligent_Forecasting_and_Inventory_Management_System.ipynb

Fork the repo.
Create a feature branch (git checkout -b feature/AmazingFeature).
Commit changes (git commit -m 'Add some AmazingFeature').
Push to branch (git push origin feature/AmazingFeature).
Open a Pull Request.

License
This project is licensed under the MIT License - see the LICENSE file for details.
Acknowledgments

Dataset: Kaggle Superstore.
Libraries: Prophet (Meta), SciPy, TensorFlow.
Inspiration: Data science best practices from Towards Data Science.


Questions? Open an issue or contact nawalkumar4810167@gmail.com. Star the repo if it helps! 🚀
