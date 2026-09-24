# TASK 3 - Cleaning Data

## Objective
Demonstrate professional-level data cleaning skills by taking a deliberately messy dataset and systematically transforming it into a clean, analysis-ready dataset. Document every decision.

## Tech Stack
Python, pandas, numpy, Jupyter Notebook

## Dataset Used
dirty_cafe_sales Dataset (Kaggle) - Deliberately messy version with nulls, duplicates, inconsistent formatting, outliers

## Feature Checklist Completed

### 1. Data Quality Report (Before Cleaning)
Performed initial audit:
- **Nulls per column:** Age (177), Cabin (687), Embarked (2)
- **Duplicate rows:** 15 duplicates found
- **Data type issues:** Age as object, Fare as string with "$", Pclass as float, Date formats mixed (MM/DD/YYYY vs DD-MM-YYYY)
- **Value range anomalies:** Fare negative values (-10), Age > 100, Gender as "Male"/"male"/"M"/"F"

### 2. Missing Data Handling
| Column | Strategy | Justification |
| :--- | :--- | :--- |
| Age | Median imputation (28) | Numeric, skewed by outliers, median is robust |
| Embarked | Mode imputation (S) | Categorical, only 2 missing, most common port |
| Cabin | New category "Unknown" | 77% missing, dropping would lose data |
| Fare | Mean imputation | Small missing count, normally distributed |

### 3. Duplicate Removal
- Identified 15 exact duplicate rows using `df.duplicated()`
- Removed using `df.drop_duplicates()`
- Documented: 15 rows removed (1.6% of data)

### 4. Standardisation
- Gender: "Male"/"male"/"M"/"m" -> "Male", "Female"/"female"/"F"/"f" -> "Female"
- Embarked Port: "S"/"southampton" -> "Southampton"
- Date column: Converted mixed formats to `datetime64[ns]` using `pd.to_datetime(errors='coerce')`
- Name: Removed extra spaces, title case

### 5. Outlier Detection (IQR Method)
- Used IQR for Fare and Age
- **Fare:** Q1=7.9, Q3=31, IQR=23.1 -> Upper bound 65.6. Found 25 outliers >100.
- Decision: Capped at 99th percentile (retain but cap, as high fare is valid for 1st class)
- **Age:** >80 considered outlier, retained as valid elderly passengers

### 6. Data Type Correction
- Pclass: float -> int
- Age: object -> float -> int
- Fare: object ($52.5) -> float (52.5)
- Survived: int -> bool/category
- Date_Boarded: object -> datetime
- PassengerID: int -> string (as ID not for math)

### 7. Before vs. After Summary Table
| Metric | Before | After |
| :--- | :--- | :--- |
| Total Rows | 891 | 876 (after dedup) |
| Null Count | 866 total | 0 |
| Duplicate Count | 15 | 0 |
| Incorrect dtypes | 5 columns | 0 |
| Standardisation Issues | 120+ values | 0 |

### 8. Cleaned Dataset Saved
Saved final clean dataset as `titanic_cleaned.csv` for future analysis.

## Project Structure
- data_cleaning.ipynb - Full notebook with markdown justification for each step
- titanic_raw.csv - Original messy dataset
- titanic_cleaned.csv - Final cleaned dataset
- README.md
# Project Files

- Jupyter Notebook containing the complete cleaning process.
- Dataset used for the project.
- Screenshots/output files.

## Conclusion

The project demonstrates a systematic data-cleaning workflow and prepares the dataset for further analysis.
## How to Run
pip install pandas numpy
jupyter notebook data_cleaning.ipynb
