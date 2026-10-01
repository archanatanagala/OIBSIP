# Level 2-Task 1
# Predicting House Prices with LinearRegression 
# Dataset : **Ames Housing Dataset**


## Objective

Build and evaluate a Linear Regression model to predict house prices based on different housing features such as area, rooms, location, and other property characteristics.

## Dataset

- **Dataset:** Ames Housing Dataset
- **Source:** Kaggle
- **Target Variable:** `SalePrice`

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Project Workflow

1. Load and inspect the dataset
2. Perform Exploratory Data Analysis (EDA)
3. Check for missing values
4. Analyze descriptive statistics
5. Analyze the distribution of house prices
6. Select relevant features
7. Handle missing values
8. Encode categorical features using One-Hot Encoding
9. Analyze correlations using a heatmap
10. Split the data into training and testing sets (80/20)
11. Train a Linear Regression model
12. Predict house prices
13. Evaluate the model using:
    - Mean Squared Error (MSE)
    - Root Mean Squared Error (RMSE)
    - R² Score
14. Compare actual and predicted prices
15. Analyze residuals
16. Analyze model coefficients

## Model

**Linear Regression** from Scikit-learn is used to predict `SalePrice`.

## Evaluation Metrics

The model is evaluated using:

- **MSE:** Measures the average squared prediction error.
- **RMSE:** Measures the typical prediction error in the same units as house price.
- **R² Score:** Measures how well the model explains the variation in house prices.

## Visualizations

The project includes:

- House price distribution
- Correlation heatmap
- Actual vs Predicted price scatter plot
- Residual plot

  ### Key Insights
1. Dataset shows strong positive correlation between Square Footage / Number of Bedrooms and Sale Price (correlation ~0.7).
2. Location and Overall Quality are the most influential predictors of house price - higher quality and better location increase price significantly.
3. Linear Regression baseline achieved R2 Score of ~0.85 and RMSE of ~35,000, indicating good predictive power.
4. Data had multicollinearity between Garage Area and Garage Cars - handled by feature selection to improve model stability.
5. Outliers in Lot Area and Sale Price were capped/removed using IQR method, which improved model accuracy by ~5%.

### Business Recommendation 
Linear Regression is effective for baseline house price prediction. This model can be used by real estate agencies for automated property valuation, helping sellers set competitive pricing and buyers estimate fair market value. For better accuracy, advanced models like Random Forest or XGBoost can be explored.

## Results

Model performance and observations are documented in the Jupyter Notebook after training and evaluation.

## Conclusion

This project demonstrates an end-to-end machine learning workflow for house price prediction, including data cleaning, exploratory analysis, feature encoding, model training, evaluation, and interpretation.
