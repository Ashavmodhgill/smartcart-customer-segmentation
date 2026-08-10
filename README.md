# 🛒 SmartCart Customer Segmentation & Behavioral Analysis

An end-to-end Machine Learning project applying unsupervised learning techniques to segment e-commerce customers into distinct personas based on demographic attributes, spending behaviors, and campaign responses.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Dataset Summary](#-dataset-summary)
- [Key Features & Tech Stack](#-key-features--tech-stack)
- [Workflow & Methodology](#-workflow--methodology)
- [Cluster Insights & Business Personas](#-cluster-insights--business-personas)
- [Marketing & Business Recommendations](#-marketing--business-recommendations)
- [How to Run](#-how-to-run)

---

## 📌 Project Overview
Understanding customer heterogeneity is critical for targeted marketing and revenue optimization. This project analyzes purchasing patterns and demographic profiles of **SmartCart** customers using unsupervised machine learning. By reducing data dimensions via **3D Principal Component Analysis (PCA)** and applying **Agglomerative Hierarchical Clustering**, we group customers into **4 actionable personas**.

---

## 📊 Dataset Summary
The dataset contains customer demographic data, purchasing channels, campaign responsiveness, and category-level spending.
- **Records:** 2,240 rows (2,236 after outlier cleaning)
- **Features:** 22 raw columns, engineered up to 18 features for modeling.

---

## 🛠️ Key Features & Tech Stack
- **Language:** Python 3.x
- **Data Manipulation:** `pandas`, `numpy`
- **Visualization:** `matplotlib`, `seaborn`, `mpl_toolkits.mplot3d`
- **Machine Learning:** `scikit-learn` (`StandardScaler`, `OneHotEncoder`, `PCA`, `KMeans`, `AgglomerativeClustering`)
- **Optimization:** `kneed` (`KneeLocator`) for automated elbow detection

---

## ⚙️ Workflow & Methodology

1. **Data Preprocessing & Cleaning:**
   - Imputed missing values in `Income` using the median (24 records).
   - Removed extreme outliers (e.g., customers aged > 90 or earning > $600,000).
2. **Feature Engineering:**
   - Calculated `Age` `2026 - Year_Birth` and `customer_Tenure_days`.
   - Consolidated `Total_spending` across all product categories (Wines, Fruits, Meat, Fish, Sweets, Gold).
   - Aggregated `total_children` from `Kidhome` and `Teenhome`.
   - Grouped `Education` into 3 tiers (*UnderGraduate*, *Graduate*, *PostGraduate*) and `Marital_Status` into `Living_With` (*Partner* vs. *Alone*).
3. **Encoding & Scaling:**
   - Applied `OneHotEncoder` on categorical attributes and standard feature scaling via `StandardScaler`.
4. **Dimensionality Reduction:**
   - Applied **3D PCA** to compress 18 features while retaining key variance structure.
5. **Clustering & Model Evaluation:**
   - Evaluated optimal $K$ using the **Elbow Method (WCSS)** and **Silhouette Score Analysis**, determining $K = 4$.
   - Selected **Agglomerative Clustering ($K=4$, Ward linkage)** over K-Means for cleaner spatial separation in 3D PCA space.

---

## 💡 Cluster Insights & Business Personas

| Cluster | Persona | Avg Income | Avg Spending | Household Structure | Key Behavioral Trait |
| :---: | :--- | :---: | :---: | :--- | :--- |
| **0** | **Budget Families** | ~$39.7k | ~$222 | Partnered, ~1.24 Kids | High web visits (~6.3/mo), deal-sensitive, price comparisons. |
| **1** | **High-Value Couples** | ~$72.8k | **~$1,237** | Partnered, ~0.51 Kids | High multi-channel spenders (Store/Catalog/Web), low deal usage. |
| **2** | **Single Budget Shoppers** | ~$37.0k | ~$166 | Single, ~1.27 Kids | Lowest spenders, high web visits, budget/essential buyers. |
| **3** | **High-Value Singles (VIPs)**| ~$70.7k | **~$1,190** | Single, ~0.46 Kids | **Highest Response Rate (32%)**, long customer tenure (~376 days). |

---

## 🚀 Marketing & Business Recommendations

- **Cluster 0 (Budget Families):** Focus on family bundle discounts, "Buy 1 Get 1 Free" promotions, and deal alerts to convert high web visits into sales.
- **Cluster 1 (High-Value Couples):** Target with premium product lines, direct mail catalogs, and loyalty reward programs rather than price discounts.
- **Cluster 2 (Single Budget Shoppers):** Offer cart-recovery incentives, low minimum free-shipping thresholds, and discount vouchers for daily essentials.
- **Cluster 3 (High-Value Singles / VIPs):** Prioritize for exclusive campaign launches, VIP early-access events, and luxury item cross-selling, as they yield the highest conversion rate (32%).

---

## 💻 How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/Ashavmodhgill/smartcart-customer-segmentation.git](https://github.com/Ashavmodhgill/smartcart-customer-segmentation.git)
   cd smartcart-customer-segmentation and install these dependencies pip install pandas numpy matplotlib seaborn scikit-learn kneed
   
   
