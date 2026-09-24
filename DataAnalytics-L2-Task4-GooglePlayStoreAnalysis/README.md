# TASK 4 - Unveiling the Android App Market (Google Play Store Analysis)

## Objective
To perform a comprehensive EDA on Google Play Store ecosystem - cleaning messy real-world data, exploring app categories, analyzing ratings, size, installs, pricing trends, and conducting sentiment analysis on user reviews to provide data-driven insights for new app developers.

## Tech Stack
Python, pandas, numpy, matplotlib, seaborn, plotly, VADER / TextBlob, Jupyter Notebook

## Datasets Used
1. `googleplaystore.csv` - 10k+ apps data from Kaggle
2. `googleplaystore_user_reviews.csv` - User reviews data

## Steps Performed

#### 1. Data Loading & Cleaning
- Loaded both datasets separately
- Fixed data types: Cleaned `Installs` (10,000+), `Size` (M/k), `Price` ($)
- Handled nulls, removed 483 duplicates
- Converted Ratings, Reviews to numeric

#### 2. EDA & Visualizations
- **Category Analysis:** Bar chart - FAMILY & GAME are most saturated categories
- **Ratings Analysis:** Distplot of ratings (4.1 avg), Avg rating by category
- **