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
1. Dataset: Ames Housing Dataset - 1460 houses, 80 features. Target variable SalePrice is right-skewed, handled via EDA.
2. Top correlated features with SalePrice are Overall Qual (0.79), GrLivArea (0.71), GarageCars and TotalBsmtSF - bigger area and higher quality = higher price.
3. Linear Regression baseline achieved good performance with R2 ~0.82 and low RMSE on test set. Ridge and Lasso were compared as bonus, with Ridge performing slightly better in controlling overfitting.
4. Coefficient Analysis shows Overall Qual, GrLivArea, and TotalBsmtSF have highest positive impact on house price. Some features like Overall Cond have negative impact.
5. Missing values were handled by median/mode imputation and categorical features were One-Hot Encoded - required because Linear Regression needs numerical input.

# Business Recommendation 
Linear Regression is effective for Ames Housing price prediction and gives interpretable coefficients. Overall Quality is the single most important driver of price. For business use, this can help in automated property valuation.

## Results

Model performance and observations are documented in the Jupyter Notebook after training and evaluation.

## Conclusion

This project demonstrates an end-to-end machine learning workflow for house price prediction, including data cleaning, exploratory analysis, feature encoding, model training, evaluation, and interpretation.
