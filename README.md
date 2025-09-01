# 🛒 Retail Customer Segmentation & Purchase Prediction

## 📌 Project Overview
This project applies **Machine Learning (Supervised + Unsupervised)** to retail customer data to help businesses improve marketing campaigns.  
The goal is twofold:
1. **Segment customers** into meaningful groups using clustering (Unsupervised Learning).
2. **Predict purchase likelihood** during the next campaign (Supervised Learning).

---

## 📂 Dataset
- Source: [Online Retail Dataset (UCI/Kaggle)](https://www.kaggle.com/datasets/lakshmi25npathi/online-retail-dataset)
- Features include:
  - `InvoiceNo, StockCode, Description, Quantity, UnitPrice, InvoiceDate, CustomerID, Country`

---

### 📦 Data Optimization (Excel → Parquet Conversion)

The original dataset was provided in **Excel (.xlsx)** format (~500k+ rows).  
To improve efficiency, it was converted into **Parquet format** for faster processing and reduced file size.

```python
import pandas as pd

# Load Excel file
df = pd.read_excel("retail.xlsx")

# Save as compressed Parquet file
df.to_parquet("retail.parquet", engine="pyarrow", compression="snappy")

print("File successfully converted to Parquet!")

```


### 🔄 Converting Parquet Back to Excel/CSV

The dataset was optimized and saved in **Parquet format** for faster ML workflows.  
However, it can be easily converted back into **Excel (.xlsx)** or **CSV (.csv)** if required:

```python
import pandas as pd

# Load Parquet file
df = pd.read_parquet("retail.parquet", engine="pyarrow")

# Convert to CSV
df.to_csv("retail.csv", index=False)

# Convert to Excel
df.to_excel("retail.xlsx", index=False)

print("Parquet file successfully converted back to CSV and Excel!")


```

## 🛠️ Methodology
### 🔹 Data Preprocessing
- Removed cancellations, duplicates, missing IDs.
- Filtered out negative quantities and prices.
- Created `TotalAmount` for transaction values.

### 🔹 Feature Engineering
- Built **RFM metrics** (Recency, Frequency, Monetary).
- Created a target variable (`Purchased`) → whether customer purchased in last 30 days.

### 🔹 Unsupervised Learning (Segmentation)
- Applied **K-Means Clustering** on RFM features.
- Evaluated clusters with Silhouette Score.
- Identified customer groups:
  - **Cluster 0**: Medium-Value Customers (moderate frequency & spend).
  - **Cluster 1**: Inactive Customers (high recency, low spend).
  - **Cluster 2**: High-Value Loyal Customers (low recency, high frequency & spend).
  - **Cluster 3**: VIP Premium Customers (very high monetary value, very frequent).

### 🔹 Supervised Learning (Prediction)
- Models used:
  - Logistic Regression (baseline)
  - Random Forest Classifier (best performance)
- Evaluation Metrics:
  - Accuracy = **100%** (due to strong feature separation in this dataset)
  - ROC-AUC = **1.0**
  - Perfect classification of Purchasers vs Non-Purchasers

---

## 📊 Visualizations
- **2D Cluster Plots**: Recency vs Monetary, Frequency vs Monetary
- **3D Cluster Visualization**: Clear segmentation of customer groups
- **Confusion Matrix**: Random Forest perfectly predicts purchase outcome

---

## 🚀 Business Impact
- **Marketing Optimization**: Target high-value loyal customers with personalized campaigns.
- **Churn Prevention**: Identify inactive customers early and re-engage them.
- **Revenue Growth**: Focus promotions on segments most likely to purchase.

---

## 📦 Tech Stack
- **Languages**: Python (pandas, numpy, matplotlib, seaborn)
- **ML Models**: scikit-learn (KMeans, Logistic Regression, Random Forest)
- **Visualization**: Seaborn, Matplotlib
- **Optional**: Power BI / Tableau dashboard for segment analysis

---

## 📌 Key Results
- Successfully segmented customers into **4 meaningful groups**.
- Built a **predictive model** with **ROC-AUC = 1.0**.
- Delivered actionable insights for targeted marketing and customer retention.

---
Made with 💻, 📊, and a passion for data.


## 👩‍💻 About Me
Humera Shaik
📊 Data Analyst | 🎯 Forecasting & Insight Generation | 🤖 AI Tools Explorer

📧 Email: humerah610@gmail.com

📱 Phone: +91 7382273550
