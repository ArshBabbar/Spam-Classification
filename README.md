# 📩 SMS Spam Detection System

## Model Description

This project focuses on the design and implementation of an **NLP-based SMS spam detection system** using supervised machine learning. The **UCI SMS Spam Collection dataset** was used for training and evaluation. Data preprocessing included **lowercasing, noise and punctuation removal, tokenization, stop-word removal, and stemming** using NLTK.

Feature extraction was performed using **CountVectorizer with unigram and bigram models**, converting text messages into numerical feature vectors. A **Multinomial Naive Bayes classifier** was trained and optimized using **GridSearchCV with cross-validation** to tune the smoothing parameter (`alpha`). The trained model was tested on real-world SMS messages and saved using **Joblib** for reuse.

This project demonstrates practical skills in **Natural Language Processing (NLP), text classification, feature engineering, model optimization, and deployment-ready machine learning systems**.

---

## Why Use This Model?

Email and SMS systems are constantly targeted by **spam, phishing, and scam messages**. Manual filtering is inefficient and error-prone. This project provides an **automated machine learning–based solution** that classifies SMS messages as **spam or legitimate** with high accuracy.

---

## Dataset Used

- **Dataset Name:** SMS Spam Collection  
- **Source:** UCI Machine Learning Repository  
- **Type:** Text-based SMS messages  
- **Features:** Raw SMS message text  
- **Target:** Binary classification  
  - `0` → Not Spam (Ham)  
  - `1` → Spam  

> Note: The dataset is publicly available from the UCI Machine Learning Repository and is intended for research and educational use.

---

## Technologies & Tools Used

- **Programming Language:** Python  
- **Libraries:**
  - Pandas
  - NumPy
  - Scikit-learn
  - NLTK
  - Joblib  
- **Model Used:** Multinomial Naive Bayes  
- **Platform:** Jupyter Notebook / Local Python Environment  

---

## Methodology

1. Downloaded and extracted the SMS Spam Collection dataset.  
2. Loaded the dataset into a Pandas DataFrame.  
3. Checked and removed duplicate records.  
4. Performed text preprocessing:
   - Lowercasing  
   - Punctuation and noise removal  
   - Tokenization  
   - Stop-word removal  
   - Stemming  
5. Reconstructed cleaned text for feature extraction.  
6. Converted text into numerical features using **CountVectorizer (unigrams + bigrams)**.  
7. Built a machine learning pipeline with:
   - Vectorizer  
   - Multinomial Naive Bayes classifier  
8. Tuned hyperparameters using **GridSearchCV with 5-fold cross-validation**.  
9. Evaluated the model on real-world test messages.  
10. Saved and reloaded the trained model using **Joblib**.  

---

## Results

- Achieved **high accuracy and precision** in spam classification.  
- Successfully detected spam with **probability-based confidence scores**.  
- Demonstrated real-time prediction capability on unseen messages.  

---

## Disclaimer

This project is intended **strictly for academic and educational purposes** to demonstrate the application of **machine learning and NLP in spam detection**. It is not designed as a commercial anti-spam product.
