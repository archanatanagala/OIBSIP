# Data Analytics - Level 1 - Task 2
## Customer Segmentation Analysis

### Objective
To segment e-commerce customers based on their purchasing behaviour and identify customer groups that can support targeted marketing strategies.

### Dataset
Online Retail II dataset from UCI (sourced via Kaggle), containing e-commerce transaction data from 2009–2011.

### Tech Stack
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

### Workflow & Feature Checklist

#### 1. Data Loading and Inspection
- Loaded the Online Retail dataset.
- Inspected the dataset structure and data types.
- Checked for missing values and inconsistent data.

#### 2. Data Cleaning
Removed or handled:
- CustomerID missing values
- Cancelled invoices
- Negative quantity values
- Invalid or negative price values

#### 3. Descriptive Statistics
Analyzed:
- Average purchase value
- Purchase frequency
- Customer lifetime value

#### 4. RFM Analysis
Created an RFM table for customers using:

- **Recency** – Number of days since the customer's last purchase.
- **Frequency** – Number of purchases made by the customer.
- **Monetary** – Total amount spent by the customer.

The analysis was performed on **4,338 customers**.

#### 5. Feature Selection
Selected the following features for customer segmentation:
- Recency
- Frequency
- Monetary

#### 6. Data Scaling
Applied `StandardScaler` to standardize the RFM features before clustering.

#### 7. Customer Segmentation
Applied the **K-Means clustering algorithm** to group customers based on their purchasing behaviour.

#### 8. Elbow Method
Used the Elbow Method and inertia values for different numbers of clusters to help determine a suitable number of customer segments.

#### 9. Cluster Analysis
Analyzed the characteristics of each cluster based on:
- Recency
- Frequency
- Monetary value

#### 10. Visualizations
Created visualizations to understand:
- Customer segment distribution
- RFM characteristics of clusters
- Differences in purchasing behaviour between customer groups

### Key Insights
1. Customers can be grouped into different segments based on their purchasing behaviour.
2. RFM analysis helps identify differences in customer recency, purchase frequency, and spending.
3. K-Means clustering provides distinct customer groups that can be analyzed for targeted marketing.
4. **Cluster 0 - Loyal Champions (High Value):** Low Recency, High Freq, High Monetary. Action: VIP loyalty program, early access.
5. **Cluster 1 - At-Risk / Can't Lose Them:** High Recency, High Monetary. Action: Win-back campaign with 20% discount.
6. **Cluster 2 - New / Low Spenders (Largest):** Low Recency, Low Freq, Low Monetary. Action: Onboarding + bestseller recommendation.
7. **Cluster 3 - Regular / Potential Loyalists:** Medium R,F,M. Action: Loyalty points to move to Cluster 0.


### Business Recommendations
1. Develop targeted marketing campaigns for different customer segments.
2. Provide retention offers to customers who have not purchased recently.
3. Reward frequent and high-value customers through loyalty programs.
4. Use customer segment characteristics to personalize promotional offers.

### Project Files
- `T ARCHANA_TASK2.ipynb` - Jupyter Notebook containing the complete analysis.
- `Online_Retail.csv` - Dataset used for the analysis.
- `screenshots/` - Screenshots of analysis outputs and visualizations.

### Conclusion
Customer segmentation using RFM analysis and K-Means clustering helps identify groups of customers with similar purchasing behaviour. These segments can support targeted marketing, customer retention, and personalized business strategies.
