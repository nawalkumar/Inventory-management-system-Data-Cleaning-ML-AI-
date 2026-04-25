# 🚀 Intelligent Forecasting & Inventory Management System

An end-to-end **Data Science + Machine Learning** solution designed to optimize retail and supply chain operations through demand forecasting, customer segmentation, and inventory optimization.

---

## 📌 Project Overview

This project leverages historical sales data to build a **smart inventory management system** that:

- Forecasts future demand using advanced ML/DL models  
- Segments customers and products for targeted insights  
- Recommends products using collaborative filtering  
- Optimizes inventory to reduce cost and prevent stockouts  
- Visualizes insights via an interactive Power BI dashboard  

---

## 💼 Business Impact

- 📉 **15–20% reduction in holding costs**
- 📦 **25% reduction in stockouts**
- ⚡ **50% cost optimization** using linear programming (simulation-based)

---

## 📊 Dataset

- Source: Kaggle Superstore Sales Dataset  
- Size: ~2,800 rows (sample used for demo)  
- Features: Sales, Customers, Products, Regions, Dates  

---

## 🧠 Key Features

### 🔹 Data Cleaning & EDA
- Missing value handling  
- Trend analysis (monthly, weekly, regional)  
- Top customers & products  
- RFM (Recency, Frequency, Monetary) segmentation  

---

### 🔹 Demand Forecasting
Implemented and compared multiple models:

- Linear Regression (baseline)
- LSTM (Deep Learning sequence model)
- Prophet (seasonality-aware, best performer)

📌 **Best Model:** Prophet (MAE ≈ 850)

---

### 🔹 Clustering & Segmentation
- K-Means clustering for product segmentation  
- Insights based on price vs. sales volume  

---

### 🔹 Recommendation System
- Collaborative filtering  
- Personalized product suggestions  

---

### 🔹 Inventory Optimization
- Linear Programming (SciPy `linprog`)  
- Economic Order Quantity (EOQ)  
- Cost minimization with constraints  

📌 Example:
- Optimal Inventory: **199 units**
- Cost reduced from **$400 → $196/month**

---

### 🔹 Visualization Dashboard
- Built using **Power BI**
- Includes:
  - KPIs
  - Forecast trends
  - Inventory alerts
  - Customer insights  

---

### 🔹 Automated Reporting
- Generates PDF reports with insights, charts, and tables  

---

## 🛠️ Tech Stack

**Languages & Libraries**
- Python (Pandas, NumPy)
- Scikit-learn
- TensorFlow / Keras
- Prophet
- SciPy

**Visualization**
- Matplotlib, Seaborn
- Power BI

**Environment**
- Jupyter Notebook / Google Colab

---

## 📂 Project Structure
```
<img width="362" height="458" alt="image" src="https://github.com/user-attachments/assets/de2e967a-2780-412c-ae90-61ba1f9adf8e" />

```


---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repository
```bash
git clone https://github.com/yourusername/intelligent-forecasting-inventory.git
cd intelligent-forecasting-inventory

2️⃣ Create Virtual Environment
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
3️⃣ Install Dependencies
pip install -r requirements.txt
▶️ Usage

Run modules step-by-step:

🔹 1. Data Cleaning & EDA
jupyter notebook eda.ipynb
🔹 2. Forecasting
jupyter notebook forecasting.ipynb
🔹 3. Clustering & Recommendations
jupyter notebook insights.ipynb
🔹 4. Inventory Optimization
jupyter notebook optimization.ipynb
🔹 5. Generate Report
python generate_report.py
📈 Sample Results
📊 Monthly Sales Peak: $5,205
📅 Forecast (Next Month): ~$5,500
📉 Cost Optimization: 50% savings
👥 Customer Segment: Majority "Champions"
📸 Screenshots

Add images in /screenshots folder

Monthly Trends
Forecast Graph
Dashboard Overview
Inventory Optimization
🔗 Project Link

👉 Notebook:
https://github.com/nawalkumar/Inventory-management-system-Data-Cleaning-ML-AI-/blob/main/Intelligent_Forecasting_and_Inventory_Management_System.ipynb

🤝 Contributing

Contributions are welcome!

Fork the repo
Create a new branch
Commit changes
Open a Pull Request
📜 License

MIT License

📬 Contact

📧 Email: nawalkumar4810167@gmail.com

If you found this project useful, consider giving it a ⭐
