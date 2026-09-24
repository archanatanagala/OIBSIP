# 2: Wine Quality Prediction - T ARCHANA
**OASIS INFOBYTE SIP Data Analytics -Level 2-Task 2**

## Dataset
**File:** `WineQT.csv` (Kaggle - 1143 rows, 13 columns, 78.06 kB)
Columns: Id, fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol, quality
Target: quality (3-8). Id column dropped.

## Tech Stack
- Python 3.13.13
- pandas, scikit-learn, matplotlib, seaborn
- No nltk, No wordcloud - 100% error free

## How to Run
1. Keep `WineQT.csv` in same folder as notebook
2. pip install pandas scikit-learn matplotlib seaborn
3. Run `T_ARCHANA_TASK2.ipynb` -> Run All

## Workflow Covered

**1. Load and Inspect & Class Distribution**
Loaded WineQT.csv, dropped Id, checked shape (1143,12), df.info(), df.describe(). Plotted quality countplot. Quality 5=577, 6=283 are majority, 3=10, 8=18 are minority.

**2. EDA**
Distribution plots via df.hist() - alcohol and volatile acidity skewed. Correlation heatmap via sns.heatmap(df.corr()) - alcohol vs quality +0.48 positive, volatile acidity vs quality -0.39 negative.

**3. Class Imbalance Discussion**
Yes, imbalance exists: 5 and 6 = 75% data, 3 and 8 = 2.4% only. Effect: Dummy model predicting only 5 gets 50.4% accuracy. Model biased, low recall for minority. Solution: stratify=y and class_weight='balanced'.

**4. Feature Engineering - Binning**
Binary: Bad (0) = quality <=6 (80.7%), Good (1) = quality >=7 (19.3%) - Used for final model.
3-Class: Low=3-4, Medium=5-6, High=7-8.
Justification: Binary chosen because it is business relevant (Good/Bad), reduces imbalance, improves F1 from 0.55 to 0.83.

**5. Train/Test Split with Stratification**
train_test_split(test_size=0.20, random_state=42, stratify=y) + StandardScaler. Stratify preserves class ratio, ensures minority class 3,8 present in test set.

**6. Train 3 Classifiers**
RandomForestClassifier(n_estimators=100, class_weight='balanced'), SGDClassifier(loss='log_loss'), SVC(class_weight='balanced').

**7. Evaluate**
Accuracy, classification_report, confusion_matrix heatmap for each. RF ~88%, SVC ~85%, SGD ~83% on Binary target.

**8. Feature Importance**
rf.feature_importances_ plotted via barplot. Top: alcohol, volatile acidity, sulphates. Matches domain knowledge.

**9. Comparison Table**
| Model | Accuracy | F1-Score |
| Random Forest | 0.88 | 0.83 |
| SVC | 0.85 | 0.79 |
| SGD | 0.83 | 0.77 |

**10. Conclusion**
Best for Deployment: Random Forest - Highest accuracy & F1, handles imbalance, gives feature importance, fast inference, robust. Use case: Predict Good/Bad before bottling. Future: XGBoost, SMOTE.


## Visualizations

The project includes:

- Distribution plots of chemical features.
- Correlation heatmap.
- Other relevant visualizations used during the analysis.

## Project Files

- `T ARCHANA_TASK2.ipynb` — Jupyter Notebook containing the complete analysis and modelling.
- `WineQT.csv` — Dataset used for the project.
- `README.md` — Project documentation.


