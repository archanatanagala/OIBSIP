#  Sentiment Analysis on Amazon Fine Food Reviews - TASK 4

> **Internship Task 4 - T ARCHANA**
> Classify Amazon food reviews into Positive, Negative, Neutral sentiment using NLP.

---

## 📌 Objective
Build an end-to-end sentiment analysis pipeline that can automatically classify customer reviews to help e-commerce platforms in customer feedback analysis.

**Class Mapping:**
- Score 1, 2 → `Negative`
- Score 3 → `Neutral`
- Score 4, 5 → `Positive`

---

##  Dataset
- **File:** `Reviews.csv` (568,454 reviews)
- **Source:** Amazon Fine Food Reviews - Kaggle
- **Columns Used:** `Text`, `Score`
- **Issue Found:** Highly Imbalanced - ~77% Positive reviews

---

## Tech Stack
- **Language:** Python 3.13.13
- **Libraries:** `pandas`, `scikit-learn`, `matplotlib`, `seaborn`, `wordcloud`, `re`
- **No `nltk` used** - To avoid `ModuleNotFoundError` in offline evaluation, we used `sklearn`'s `ENGLISH_STOP_WORDS` and `regex`.

---
