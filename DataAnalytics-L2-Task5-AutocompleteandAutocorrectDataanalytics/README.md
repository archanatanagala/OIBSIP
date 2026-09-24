# TASK 5: Autocomplete and Autocorrect Data Analytics
Oasis Infobyte | Data Analytics Internship | T ARCHANA

## Objective
To analyse and implement the efficiency and accuracy of autocomplete and autocorrect algorithms using NLP on a large text corpus.

## Dataset
Primary: NLTK Gutenberg austen-emma.txt (150k+ words)
Fallback: Self-sourcing corpus 5000x repeat - simulates 5 books
File: corpus.txt

## Tech Stack
Python, pandas, NLTK, pyspellchecker / Custom Levenshtein, matplotlib

## Installation
pip install nltk pandas matplotlib pyspellchecker
python -m nltk.downloader punkt gutenberg stopwords

No-install fallback available - custom functions included.

## Steps Done

1. Corpus Collection
Used nltk.corpus.gutenberg.raw('austen-emma.txt') with fallback self-sourcing.

2. NLP Preprocessing
Lowercasing, Punctuation removal, Tokenisation using nltk.word_tokenize, Stopword removal using nltk.corpus.stopwords, n-grams using nltk.util.ngrams

3. Autocomplete - Bigram + Prefix Model
Bigram: P(w2|w1) stored in defaultdict(Counter)
Prefix: Words starting with prefix ranked by frequency

4. Tested Autocomplete - 12 prefixes
lov, beau, hap, wond, capt, em, frie, char, fami, daugh, mr, mrs
Example: lov -> love, lovely, lover

5. Autocorrect - Edit Distance Method
Method: Levenshtein distance 1 + word frequency
pyspellchecker primary, custom Levenshtein + difflib fallback

6. Tested Autocorrect - 20 words
lovve->love, beuatiful->beautiful, happpy->happy, teh->the, recieve->receive etc.

7. Performance Metrics
Autocomplete: Precision@3 0.83, Recall@3 0.90, F1 0.86, Latency 0.45ms
Autocorrect: Accuracy 85%, Precision 0.85, Recall 0.85, F1 0.85, Latency 2.1ms
Throughput: 2200 queries/sec per core, handles 1M/hour (277 qps)

8. Algorithm Comparison
Bigram: Fast Simple Low Memory, Latency 0.3ms
Trigram: More Context Better Accuracy, Needs more data 0.8ms
pyspellchecker: Fast O(1) needs install
Custom Levenshtein: No dependency explainable but slower
Best: Bigram + SymSpell for production

9. Visualisation
Bar Chart Top 20 Frequent Words
Confusion Matrix Before vs After Correction

10. Discussion vs Google Keyboard (Gboard)
Our Limitations: Limited vocab 2000 words, No neural model, No personalization, No keyboard proximity model

Gboard Production: On-device Neural LM, Trie + FST <10ms, Personalized federated learning, Swipe voice emoji, 1B+ users

Scalability 1M/hour: Use Trie + LRU cache + SymSpell precompute + FastAPI + Redis + Auto-scaling

## Files
T ARCHANA_TASK 5.ipynb - Main notebook
corpus.txt - Corpus
README.md

## Result
85% accuracy <5ms latency, all 10 checklist points completed.

Author: T ARCHANA | Oasis Infobyte Data Analytics Intern
#oasisinfobyte #dataanalytics #nlp