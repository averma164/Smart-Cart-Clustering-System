# 🛒 SmartCart Clustering System

An unsupervised machine learning customer segmentation system designed to analyze e-commerce transaction data, uncover distinct customer behavior patterns, and enable personalized marketing and retention strategies.

---

## 📌 Problem Statement

SmartCart is a growing e-commerce platform serving customers across multiple countries. Currently, SmartCart applies generic marketing and engagement strategies across its entire user base of **2,240 customers**. Without visibility into differing behavioral patterns, the business faces:
- Inefficient marketing spend
- Missed opportunities to retain high-value customers
- Delayed identification of churn-prone users

This project leverages unsupervised clustering algorithms to group customers based on demographics, purchasing behavior, channel preferences, and loyalty indicators—enabling data-driven decision-making for targeted campaigns.

---

## 📊 Dataset Overview

The dataset (`smartcart_customers.csv`) contains **2,240 customer records** across **22 attributes**:

### 1. Customer Demographics
| Feature | Description |
| :--- | :--- |
| `ID` | Unique customer identifier |
| `Year_Birth` | Year of birth of the customer |
| `Education` | Highest education level achieved |
| `Marital_Status` | Marital status of the customer |
| `Income` | Yearly household income |
| `Kidhome` | Number of small children in the household |
| `Teenhome` | Number of teenagers in the household |
| `Dt_Customer` | Date when the customer enrolled with SmartCart |

### 2. Purchase Behavior (Amount Spent)
| Feature | Description |
| :--- | :--- |
| `MntWines` | Amount spent on wine products |
| `MntFruits` | Amount spent on fruits |
| `MntMeatProducts` | Amount spent on meat products |
| `MntFishProducts` | Amount spent on fish products |
| `MntSweetProducts` | Amount spent on sweet products |
| `MntGoldProds` | Amount spent on gold products |

### 3. Purchase Behavior (Channel Frequency)
| Feature | Description |
| :--- | :--- |
| `NumDealsPurchases` | Purchases made using discounts |
| `NumWebPurchases` | Purchases made through the website |
| `NumCatalogPurchases` | Purchases made through the catalog |
| `NumStorePurchases` | Purchases made in physical stores |
| `NumWebVisitsMonth` | Number of visits to the website per month |

### 4. Customer Feedback & Recency
| Feature | Description |
| :--- | :--- |
| `Recency` | Number of days since the last purchase |
| `Complain` | Customer complained in the last 2 years (`1` = Yes, `0` = No) |

---

## 🛠️ Tech Stack

- **Language:** Python
- **Data Manipulation:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-Learn (`OneHotEncoder`, `StandardScaler`, `PCA`, `KMeans` / `AgglomerativeClustering`)

---

## ⚙️ Methodology & Workflow

1. **Data Cleaning:**
   - Handled missing values in `Income` and removed extreme demographic/income outliers.
   - Dropped non-informative identifiers (`ID`) and constant columns.
2. **Feature Engineering:**
   - Derived `Age` from `Year_Birth` and `Customer_Tenure` from `Dt_Customer`.
   - Aggregated product expenditures into `Total_Spending` and household dependents into `Total_Children`.
   - Consolidated `Marital_Status` categories into a binary `Living_with` feature (`Partner` vs. `Alone`).
3. **Encoding & Scaling:**
   - Applied `OneHotEncoder` to categorical attributes (`Education`, `Living_with`).
   - Standardized numerical features using `StandardScaler` and reduced dimensionality with `PCA` for clustering and visualization.
4. **Clustering & Evaluation:**
   - Evaluated optimal cluster counts using the **Elbow Method** and **Silhouette Score**.
   - Profiled resulting customer segments across spending, income, household size, and channel activity.

---

## 🔍 Key Customer Segments & Recommendations

*(Update the summary points below to match your exact cluster numbers and metrics from `smartCart.ipynb`)*

- **Cluster 0 — High-Income VIPs:** High household income, minimal children at home, high overall spend (especially on wines and meat), and frequent catalog/in-store purchases.
  - *Action:* Offer exclusive loyalty tiers, early catalog access, and premium product bundles.
- **Cluster 1 — Budget-Conscious Families:** Moderate income, children/teenagers at home, lower total spend, and high sensitivity to discounted deals.
  - *Action:* Target with family-pack discounts, seasonal coupons, and value promotions.
- **Cluster 2 — Digital Browsers / Churn-Prone:** High monthly website visits paired with low conversion or higher recency since last purchase.
  - *Action:* Deploy cart-abandonment reminders, personalized web retargeting, and first-purchase incentives.

---

## 📂 Repository Structure

```text
Smart-Cart-Clustering-System/
├── smartCart.ipynb              # End-to-end EDA, preprocessing, and clustering notebook
├── smartcart_customers.csv      # Raw customer dataset (2,240 records)
├── Smart_Cart_Description.txt   # Original problem statement & data dictionary
├── .gitignore                   # Excludes Jupyter checkpoints and local temp files
└── README.md                    # Project documentation