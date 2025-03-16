This is my reference codes
# Customer Spending Prediction Project  
**Group Number: Peer-16  
**Date:** March 16, 2025  

---

## 1. Introduction  
This report details the preprocessing and machine learning pipeline developed to predict customer spending behavior using transaction and social media data. The project involved data augmentation, dataset merging with transitive properties, quality checks, and predictive modeling.

---

## 2. Methodology  

### Part 1: Data Augmentation  
- **Missing Value Handling**:  
  - Customer ratings imputed using Random Forest regression.  
  - 5% random noise added to `purchase_amount`.  
  - Log transformation applied to address skewness.  
- **Synthetic Data**:  
  - Generated 100 synthetic transactions via resampling.  

### Part 2: Dataset Merging  
- **ID Mapping**:  
  - Linked legacy and new customer IDs using `id_mapping.csv`.  
  - Resolved conflicts by retaining first-occurring `customer_id_new`.  
- **Feature Engineering**:  
  - Created `engagement_score` (weighted average of social and transaction data).  
  - Computed monthly spending averages.  
  - Applied TF-IDF to `review_sentiment`.  

### Part 3: Data Consistency Checks  
- **Validation**:  
  - Removed 12 duplicate entries.  
  - Confirmed all `product_category` values were valid.  
- **Statistical Analysis**:  
  - Generated distribution plots pre/post-augmentation.  
  - Identified 8 highly correlated features (|r| > 0.85).  

### Bonus Challenge: ML Model  
- **Models Trained**:  
  - Random Forest (MAE: 54.23, R²: 0.82).  
  - XGBoost (MAE: 49.15, R²: 0.85).  
- **Key Features**:  
  - `engagement_score` (22% importance).  
  - `monthly_avg_spending` (18% importance).  

---

## 3. Team Contributions  
| Member        | Role                                       |  
|---------------|--------------------------------------------|  
| Denys Ntwaritaganzwa    | Data loading, cleaning, imputation and report writing |  
| Aubin Ntwali   | Dataset merging conflict resolution and ML modeling  |  
| [Member 3]    | Feature engineering and quality checks    |  
| [Member 4]    | ML modeling and             |  

---

## 4. Challenges & Solutions  
1. **Multiple ID Mappings**:  
   - *Issue*: 15% of legacy IDs mapped to multiple new IDs.  
   - *Fix*: Retained first valid mapping per transaction.  
2. **Skewed Purchase Data**:  
   - *Issue*: `purchase_amount` skewness = 2.4.  
   - *Fix*: Applied log transformation (post-skewness = 0.7).  

---

## 5. Key Insights  
- Social media engagement scores improved spending predictions by 14%.  
- Augmentation reduced class imbalance in Electronics category by 30%.  
- XGBoost outperformed Random Forest by 3.7% in R² score.  

---

## 6. References  
1. F. Pedregosa et al., "Scikit-learn: Machine Learning in Python," *JMLR*, vol. 12, pp. 2825–2830, 2011.  
2. T. Chen and C. Guestrin, "XGBoost: A Scalable Tree Boosting System," *KDD '16*, 2016.  
3. N. V. Chawla et al., "SMOTE: Synthetic Minority Over-sampling Technique," *JAIR*, vol. 16, pp. 321–357, 2002.  

---

## 7. Conclusion  
The pipeline successfully merged heterogeneous datasets and predicted customer spending with 85% accuracy. Data quality checks and feature engineering were critical to model performance.  

**Appendix**: Code snippets and visualisations available in the GitHub repository.  
