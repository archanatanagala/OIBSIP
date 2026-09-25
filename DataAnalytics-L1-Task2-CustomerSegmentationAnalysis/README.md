# LEVEL1-TASK2 - Customer Segmentation Analysis 

## Objective
Segment e-commerce customers based on purchasing behaviour to enable targeted marketing.

## Dataset
Online Retail II dataset from UCI (sourced via Kaggle - e-commerce customer data). 500k+ transactions from 2009-2011.

## Tech Stack
- Python, Pandas, NumPy
- Scikit-learn (StandardScaler, KMeans)
- Matplotlib, Seaborn
- Jupyter Notebook

## Workflow & Feature Checklist

[x] Load dataset and inspect structure; handle missing values and inconsistent data
- Removed null CustomerID, cancelled invoices (C), negative Quantity/Price

[x] Descriptive statistics: average purchase value, purchase frequency, customer lifetime value
- Calculated via RFM table (4338 customers)

[x] Feature selection: RFM Analysis
- Recency: Days since last purchase
- Frequency: Count of unique invoices
- Monetary: Sum of TotalPrice

[x] Data normalisation before clustering
- Used StandardScaler on RFM features

[x] Apply K-Means clustering + Elbow Method
- Tested K=1 to 10, Optimal K=4 found

[x] Visualise clusters using scatter plots
- Recency vs Monetary, Frequency vs Monetary

[x] Profile each cluster
- Mean R,F,M per cluster to label customer type

[x] Bar chart: number of customers per cluster

[x] Insights section

## Key Insights

1. **Cluster 0 - Loyal Champions (High Value):** Low Recency, High Freq, High Monetary. Action: VIP loyalty program, early access.
2. **Cluster 1 - At-Risk / Can't Lose Them:** High Recency, High Monetary. Action: Win-back campaign with 20% discount.
3. **Cluster 2 - New / Low Spenders (Largest):** Low Recency, Low Freq, Low Monetary. Action: Onboarding + bestseller recommendation.
4. **Cluster 3 - Regular / Potential Loyalists:** Medium R,F,M. Action: Loyalty points to move to Cluster 0.

## Conclusion
RFM + K-Means successfully identified 4 actionable segments. Focus on retention of Cluster 0 and reactivation of Cluster 1 for maximum ROI.

## How to Run
1. pip install pandas scikit-learn matplotlib seaborn
2. jupyter notebook online_retail.ipynb