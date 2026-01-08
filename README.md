# 🏠 Modeling Property Sales Above Appraised Value

**Course:** Advanced Topics in Machine Learning  
**Authors:** Bnaya Unger, Tal Elrom  

## 📌 Project Overview
This project develops a data-driven machine learning framework to identify real estate transactions that are sold **above their appraised market value**.  
By combining supervised classification models with unsupervised clustering techniques, we analyze market behavior, uncover latent property segments, and flag high-potential transactions.

The task is formulated as a **binary classification problem**:

> **SaleAboveAppraisedValue = 1** if `SalePrice > TotalAppraisedValue`, otherwise `0`.

---

## 🎯 Motivation
The real estate market is complex, heterogeneous, and influenced by non-linear interactions between property characteristics, location, timing, and ownership patterns.  
For investors and property owners, **missing a property that sells above its appraised value (False Negative)** is more costly than incorrectly flagging a neutral transaction.

This project prioritizes **Recall** to minimize missed high-value opportunities.

---

## 📊 Dataset
- **Source:** data.gov  
- **File:** `Real_Estate_Sales_10012020_to_Current.csv`
- **Initial Size:** 7,410 transactions × 23 features  
- **Data Types:** Numerical, categorical, and temporal

Each row represents a real estate sale, including:
- Sale price and appraised value  
- Property type and building characteristics  
- Location identifiers  
- Sale date information  

---

## 🧹 Data Preprocessing
Key preprocessing steps included:
- Removal of identifier and redundant features  
- Dropping records with missing values in selected features  
- Temporal feature extraction (sale year, sale month)  
- Feature scaling using `StandardScaler`  

### Encoding Strategy
- **Low-cardinality categorical features:** One-Hot Encoding  
- **High-cardinality features:** Target Encoding  
This hybrid approach balances interpretability and dimensionality control.

---

## 🛠 Feature Engineering
To better capture real estate dynamics, we engineered domain-specific features:
- **Apartment vs. Private House** indicator  
- **Repeat_Grantor:** recurring sellers as a proxy for market expertise  
- **Price_Level:** appraisal value quartiles  
- **Street_Popularity:** transaction density per street  
- **AreaPerUnit:** built area per living unit  
- **Land_to_Building_Ratio:** land utilization efficiency  

---

## 🤖 Methodology

### Supervised Learning (Classification)
Models evaluated:
- Logistic Regression (baseline, interpretable)
- Decision Tree
- Support Vector Machine (SVM)
- Random Forest
- **XGBoost (final model)**

**Evaluation Metrics:**
- Recall (primary metric)
- Precision
- F1-Score
- Accuracy
- ROC-AUC

Hyperparameter tuning was performed using **RandomizedSearchCV**, optimizing for Recall.

---

### Unsupervised Learning (Clustering)
Used to explore latent market structure:
- **K-Means:** macro segmentation of property types  
- **DBSCAN:** density-based clustering and outlier detection  

Findings revealed clear separation between:
- Apartments / Condominiums  
- Private houses and multi-family homes  
- Unique and luxury outliers  

---

## 📈 Results
- **Best Model:** XGBoost  
- **Final Performance (after tuning):**
  - Recall: **0.62**
  - Accuracy: 0.68
  - Precision: 0.67
  - F1-Score: 0.64
  - ROC-AUC: 0.74

**Key Insights:**
- Timing and seasonality strongly influence over-appraisal likelihood  
- Location and ownership patterns are highly predictive  
- Ensemble methods outperform single models on structured real estate data  

---

## ⚠ Limitations
- Public records do not capture emotional or negotiation-driven pricing factors  
- Luxury and unique properties are harder to predict  
- No access to unstructured data (text descriptions or images)

---

## 🔮 Future Work
- Integrating macroeconomic and time-series indicators  
- Enriching data with external sources (transportation, schools, crime rates)  
- Applying NLP to broker remarks  
- Using computer vision to score interior property images  

---

## 🤝 Team Contribution
Both team members contributed equally to all stages of the project.  
Despite being on active military reserve duty during the project period, full collaboration and coordination were maintained throughout.

---

## 🧪 Technologies Used
- Python  
- pandas, NumPy  
- scikit-learn  
- XGBoost  
- Matplotlib / Seaborn  

---

## ▶ How to Run
1. Clone the repository  
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
