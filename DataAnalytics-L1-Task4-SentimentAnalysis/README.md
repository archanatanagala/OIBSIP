# TASK 4: Sentiment Analysis on Amazon Fine Food Reviews

## Objective

To build an end-to-end sentiment analysis pipeline that automatically classifies customer reviews and helps identify customer feedback patterns.

## Class Mapping

- Scores 1–2 → Negative
- Score 3 → Neutral
- Scores 4–5 → Positive

## Dataset

- `Reviews.csv`
- Source: Amazon Fine Food Reviews — Kaggle
- Columns used: Text, Score

## Tech Stack

- Python
- Pandas
- NumPy
- NLTK
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
---
- **Language:** Python 3.13.13
- **Libraries:** `pandas`, `scikit-learn`, `matplotlib`, `seaborn`, `wordcloud`, `re`
- **No `nltk` used** - To avoid `ModuleNotFoundError` in offline evaluation, we used `sklearn`'s `ENGLISH_STOP_WORDS` and `regex`.


## Analysis and Workflow

- Loaded and inspected the review dataset.
- Prepared the review text for analysis.
- Cleaned and preprocessed text data.
- Converted review scores into sentiment classes.
- Performed sentiment analysis using NLP techniques.
- Trained and evaluated a sentiment classification model.
- Visualized sentiment-related patterns and results.

## Project Files

- Jupyter Notebook containing the complete sentiment analysis.
- `Reviews.csv` dataset.
- Screenshots/output files.

## Conclusion

This project demonstrates how Natural Language Processing and machine learning can be used to classify customer reviews into positive, neutral, and negative sentiment categories.
