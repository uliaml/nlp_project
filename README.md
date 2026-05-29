# Disinformation UA: Real vs Fake News Classification

Binary text classification project for detecting **fake** and **real** Ukrainian news articles using classical NLP and Machine Learning approaches.

## Dataset

The project uses the **Fake News UA** dataset from Kaggle:

[Fake News UA Dataset](https://www.kaggle.com/datasets/sophiamatskovych/fake-news-ua?utm_source=chatgpt.com)

### Dataset characteristics

* Language: Ukrainian
* Task type: Binary text classification
* Classes:

  * `real`
  * `fake`
* Data format: CSV
* Main feature: news text
* Target variable: label (`real/fake`)

The dataset contains Ukrainian news articles collected from different online sources and is intended for misinformation detection tasks.

---

# Project Goal

The goal of the project is to build and evaluate machine learning models for automatic classification of Ukrainian news into:

* **Real news**
* **Fake news**

The project focuses on:

* text preprocessing,
* data cleaning,
* leakage prevention,
* feature extraction,
* model comparison,
* evaluation of classification quality.

---

# Project Pipeline

## 1. Data Loading and Initial Exploration

At the first stage, the dataset was loaded and inspected.

The following checks were performed:

* dataset shape,
* column structure,
* class distribution,
* missing values,
* duplicated samples,
* text examples.

Several descriptive statistics were also calculated:

* text length,
* word count,
* class balance.

### Result

The dataset was relatively balanced and suitable for binary classification after preprocessing and cleaning.

---

# 2. Data Cleaning

Several preprocessing steps were applied to improve text quality.

## Cleaning steps

* lowercasing,
* URL removal,
* punctuation removal,
* special symbols cleanup,
* extra whitespace normalization,
* removal of noisy artifacts.

Additional filtering was applied to:

* empty texts,
* extremely short samples,
* duplicated news articles.

### Result

The preprocessing pipeline significantly reduced textual noise and improved feature consistency.

---

# 3. Exploratory Text Analysis

Text analysis was performed before model training.

The project analyzed:

* most common tokens,
* text length distributions,
* duplicate patterns,
* noisy and low-information samples.

The analysis helped identify:

* repeated fake-news templates,
* duplicated content,
* low-quality records,
* potential leakage risks.

### Intermediate Conclusion

Proper cleaning and duplicate handling are especially important for fake news detection because duplicated articles may artificially inflate model quality.

---

# 4. Train/Test Split and Leakage Prevention

A major focus of the project was preventing data leakage.

The following precautions were implemented:

* train/test split before vectorizer fitting,
* duplicate handling,
* preprocessing fitted only on training data,
* independent transformation of test data.

This ensured realistic model evaluation.

### Result

The evaluation pipeline avoids preprocessing leakage and produces more reliable metrics.

---

# 5. Feature Extraction

Texts were transformed into numerical vectors using classical NLP approaches.

## Methods used

* TF-IDF vectorization
* N-gram features

Different vectorizer configurations were tested to improve classification quality.

### Result

TF-IDF with n-gram features provided strong performance for Ukrainian fake-news classification.

---

# 6. Baseline Models

Several baseline machine learning models were trained and compared.

The project experimented with:

* Logistic Regression
* Naive Bayes
* Linear SVM
* other classical ML classifiers

Evaluation metrics:

* Accuracy
* Precision
* Recall
* F1-score

---

# 7. Main Model — Linear SVM

The best results were achieved using **Linear Support Vector Machine (Linear SVM)**.

Reasons for strong performance:

* effective handling of sparse TF-IDF features,
* good generalization,
* robustness for high-dimensional text classification.

# Final Results

## Top 3 Models Performance

| Model                                           | Accuracy | Macro F1-score |
| ----------------------------------------------- | -------- | -------------- |
| TF-IDF char(3,5) + Balanced Linear SVM          | 0.9338   | 0.9321         |
| TF-IDF char(3,5) + Linear SVM                   | 0.9300   | 0.9276         |
| TF-IDF char(3,5) + RandomForestClassifier       | 0.9237   | 0.9197         |

## Best Result

The best overall performance was achieved by:

* **Linear SVM + optimized TF-IDF features**
* Accuracy: **93.38%**
* Macro F1-score: **93.21%**

The model demonstrated stable performance for both classes and good generalization on unseen Ukrainian news articles.

---

# Key Takeaways

* Classical NLP methods remain highly effective for fake news detection tasks.
* Proper preprocessing and leakage prevention significantly affect final quality.
* TF-IDF + linear classifiers provide strong results even without deep learning models.
* Linear models performed especially well on sparse Ukrainian text features.

---

# Technologies Used

## Libraries

* pandas
* numpy
* scikit-learn
* matplotlib
* seaborn
* nltk

## ML/NLP Techniques

* text preprocessing
* TF-IDF vectorization
* n-grams
* binary classification
* model evaluation

---

# Conclusion

This project demonstrates a complete NLP pipeline for Ukrainian fake news detection using classical machine learning approaches.

The final solution includes:

* data cleaning,
* exploratory analysis,
* leakage-safe preprocessing,
* feature engineering,
* model comparison,
* evaluation of classification performance.

The results show that classical NLP methods combined with Linear SVM can provide strong performance for Ukrainian fake-news classification tasks.
