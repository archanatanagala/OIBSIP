#TASK 3 - Fraud Detection - Credit Card Fraud Detection
**By T ARCHANA | Data Analytics Internship**

## Objective
Build a machine learning pipeline to detect fraudulent financial transactions from a heavily imbalanced dataset, addressing class imbalance as core challenge.

## Dataset
**File:** `creditcard.csv`
**Source:** Kaggle - Credit Card Fraud Detection (284,807 transactions, 492 fraudulent)
**Columns:** 31 columns
- Time: seconds elapsed since first transaction
- V1-V28: PCA transformed features (anonymized for privacy)
- Amount: transaction amount
- Class: Target - 0=Non-Fraud, 1=Fraud (0.172% fraud)

## Tech Stack
- Python 3.13, pandas, scikit-learn, imbalanced-learn (SMOTE), matplotlib, seaborn, Jupyter Notebook
- Install: `pip install pandas scikit-learn matplotlib seaborn imbalanced-learn`

## How to Run
1. Download `creditcard.csv` and place in same folder as `T_ARCHANA_TASK3.ipynb`
2. `pip install scikit-learn imbalanced-learn`
3. Open notebook -> Run All
4. No nltk, No wordcloud - 100% error free

## Workflow - All Checklist Covered

**1. Load dataset and analyse class imbalance**
Loaded via `pd.read_csv()`, shape (284807, 31). Class count: Non-Fraud 284315 (99.827%), Fraud 492 (0.172%). Imbalance ratio 1:578. Visualized with countplot and pie chart.

**2. EDA: Amount & Time-of-day analysis**
- Amount distribution: Fraud mean $122 vs Non-Fraud $88. Fraud transactions have lower amounts but some high outliers. Boxplot shows difference.
- Time-of-day: Converted Time to Hour (Time/3600 %24). Plotted stacked histogram. Fraud occurs more at night (low activity hours).

**3. Why accuracy is misleading**
Dummy model predicting all as Non-Fraud gets 99.827% Accuracy but 0% Recall for fraud. Accuracy hides failure on minority. Must use Precision, Recall, F1, AUC-ROC. For fraud, missing fraud (False Negative) costs money, so Recall matters more than Accuracy.

**4. Class imbalance handling technique**
Applied 2 techniques:
- `class_weight='balanced'` in both models (penalizes misclassifying minority)
- SMOTE oversampling: `from imblearn.over_sampling import SMOTE` -> resamples train set from 0.172% fraud to 50% fraud for better learning.
Fallback if imblearn not installed: uses only class_weight.

**5. Train/test split with stratification**
`train_test_split(test_size=0.20, random_state=42, stratify=y)` + `StandardScaler` for Amount and Time. Stratification ensures fraud % same in train (0.172%) and test (0.172%) - without stratify fraud may be 0 in test.

**6. Train 2 models**
- Logistic Regression (`class_weight='balanced', max_iter=1000`) - Fast, linear, ideal for real-time.
- Random Forest (`n_estimators=100, class_weight='balanced'`) - Ensemble, non-linear, higher precision.

**7. Evaluate using Precision, Recall, F1, AUC-ROC**
- Metrics: classification_report, confusion_matrix, roc_auc_score, roc_curve
- Logistic: AUC ~0.97, Recall_Fraud ~0.90, Precision_Fraud ~0.08 (high recall, low precision)
- Random Forest: AUC ~0.98, Recall_Fraud ~0.82, Precision_Fraud ~0.85 (balanced)
- Plotted confusion matrix heatmap and ROC curve comparing both.

**8. Which metric matters most - Recall vs Precision trade-off**
Most important = **RECALL**. FN = missed fraud = direct loss. FP = genuine flagged as fraud = can verify via OTP. Bank prefers High Recall 90%+ even with some false alarms. We choose F1 and AUC for model selection but monitor Recall_Fraud daily. Random Forest gives best trade-off.

**9. Feature importance**
- Logistic coefficients: V14, V17, V12, V10 have highest negative/positive weights.
- Random Forest importance: V14 (~18%), V17, V12, V10, Amount are top 5.
- Insight: These V features represent anonymized transaction patterns most predictive of fraud.

**10. Scalability: 1 million transactions per hour**
- Current: 284k total. 1M/hour = 277/sec.
- Logistic: ~0.1ms per prediction -> 10k/sec per machine - can handle real-time.
- Random Forest 100 trees: ~2ms per pred -> ~500/sec per core - needs 4 cores or reduce to 10 trees or use XGBoost/ONNX.
- Solution: Kafka + Spark Streaming for ingestion, model served via FastAPI on Kubernetes auto-scaling, Tier-1 Logistic for real-time blocking (<100ms latency), Tier-2 RF for secondary review. Retrain weekly to handle drift. Cost: Use AWS Lambda.

## Comparison Table
| Model | Accuracy | Precision (Fraud) | Recall (Fraud) | F1 (Fraud) | AUC-ROC | Speed |
|-------|----------|-------------------|----------------|------------|---------|-------|
| Logistic Regression | 0.97 | 0.08 | 0.90 | 0.15 | 0.97 | Very Fast |
| Random Forest | 0.999 | 0.85 | 0.82 | 0.83 | 0.98 | Medium |

## Conclusion
**Best for Deployment: Random Forest** for balanced Precision+Recall. For strict real-time 1M/hour, use **Logistic Regression as Tier-1** (fast) + Random Forest as Tier-2 (accurate). Two-tier system handles scale, latency <100ms, and catches 90% frauds.

Future: Try XGBoost, Isolation Forest, real-time feature store, and monitoring dashboard.

## Files
- T_ARCHANA_TASK3.ipynb
- creditcard.csv
- README.md
- fraud_model_comparison.csv (output)