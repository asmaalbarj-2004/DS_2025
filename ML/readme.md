
# Wine Quality Study 
### Predicting Wine Quality from Physicochemical Properties  
### Based on UCI Machine Learning Repository (Red & White Vinho Verde)

---

## 1. Introduction

This study investigates the *Wine Quality* datasets from the UCI Machine Learning Repository. These datasets contain physicochemical measurements of Portuguese “Vinho Verde” wines — both **red** and **white** varieties.

The primary objective is to **model wine quality** based on these measurable characteristics, and to evaluate the performance of predictive models for **classification** (good vs. bad wine) and **regression** (predict the quality score).

This expanded analysis is based on the methodology described in:  
*Cortez et al., 2009 — Modeling wine preferences by data mining from physicochemical properties.*

---

## 2. Dataset Description

### 2.1 Overview

| Attribute | Value |
|----------|--------|
| **Dataset type** | Multivariate |
| **Subject area** | Business / Food quality |
| **Associated tasks** | Classification & Regression |
| **Instances** | 4898 (white wine) |
| **Features** | 11 physicochemical inputs + 1 output (quality) |
| **Feature type** | Real-valued |

The study focuses on the **white wine dataset** (4,898 instances).  
A second dataset exists (red wine), containing 1,599 samples.

### 2.2 Available Variables

Physicochemical input features include:

- Fixed acidity  
- Volatile acidity  
- Citric acid  
- Residual sugar  
- Chlorides  
- Free sulfur dioxide  
- Total sulfur dioxide  
- Density  
- pH  
- Sulphates  
- Alcohol  

**Output variable:**  
- **Quality** (integer score between 0 and 10, based on sensory evaluation)

---

## 3. Study Objectives

### Main goal:  
Predict wine quality based on physicochemical measurements.

### This study covers:

1. **Data loading and summarization**  
2. **Binary transformation of the quality variable**  
   - Bad wine = quality ≤ 5  
   - Good wine = quality ≥ 6  
3. **Exploratory data analysis (EDA)**  
   - Distribution of features  
   - Correlation matrix  
   - Class imbalance  
4. **Building predictive models**  
   - k-NN baseline  
5. **Discussion & possible extensions**

---

## 4. Data Summary

### 4.1 Number of samples and features

The white wine dataset contains:

- **N = 4,898 samples**
- **d = 11 input features**

### 4.2 Quality distribution

The original quality scores are **not balanced**:

Most wines score between 5 and 7.  
Few samples are rated very low (quality = 3) or very high (quality = 9).

### 4.3 Binary classification

To simplify the classification task:

- **Bad wine (0)**: quality ≤ 5  
- **Good wine (1)**: quality ≥ 6  

Result: the dataset remains imbalanced, with more "normal" wines than extreme ones.

---

## 5. Exploratory Data Analysis

### 5.1 Boxplots

Boxplots of all physicochemical features reveal:

- Some features (e.g., sulfur dioxide, residual sugar) show **large variance**.  
- Alcohol and density appear to be **important discriminators** of wine quality.  
- Multiple features exhibit **outliers**, possibly representing unique wine batches.

### 5.2 Correlation Matrix

Significant correlations include:

- Density ↔ Residual sugar (**positive correlation**)  
- Alcohol ↔ Density (**negative correlation**)  
- Volatile acidity ↔ Quality (**negative correlation**)  

Alcohol content and acidity tend to be strong indicators of wine quality.

---

## 6. Data Splitting (Train / Validation / Test)

A stratified split ensures the class proportions remain consistent across subsets:

- **Training (Xa, Ya): ~1630 samples**
- **Validation (Xv, Yv): ~1630 samples**
- **Test (Xt, Yt): ~1630 samples**

Shuffling the data prevents bias due to potential ordering in the original dataset.

---

## 7. Classification Model — k-NN

A baseline **k-nearest neighbors** classifier is used:

- **k = 3**
- Distance: Euclidean
- Trained on **training set**
- Evaluated on **validation set**

### Results

| Metric | Value |
|--------|--------|
| **Validation Accuracy** | ~0.74 (approx.) |
| **Error Rate** | ~0.26 |
<img src="téléchargement (1).png" style="height:260px;margin-right:200px"/>
<img src="téléchargement (2).png" style="height:260px;margin-right:200px"/>

*Interpretation:*  
k-NN performs reasonably well, but further improvements are possible.

---

## 8. Discussion and Potential Improvements

### Imbalanced data
The dataset contains far more "average" wines (qualities 5–7).  
Methods to address this:

- Class balancing  
- SMOTE oversampling  
- Adjusted evaluation metrics (F1, ROC-AUC)

### Feature relevance
Not all physicochemical features contribute equally.  
Feature selection methods could improve performance:

- Recursive Feature Elimination (RFE)  
- LASSO Regression  
- PCA

### Alternative models
More powerful algorithms should be tested:

- Random Forest  
- Gradient Boosting  
- SVM  
- Neural Networks

These models typically outperform k-NN in this dataset.

### Regression option
The original problem is a **regression task**, predicting the quality score directly.  
Regressors like XGBoost or Random Forest Regressor can achieve better interpretation and prediction.

---

## 9. Conclusion

This study explored the *Wine Quality* dataset using:

- Full data analysis  
- Statistical exploration  
- Feature correlations  
- Binary classification  
- k-NN baseline model  

The results show that:

- Wine quality is predictable using physicochemical measurements  
- Alcohol, density, and acidity are key factors  
- k-NN provides a baseline accuracy around 74%  
- Advanced models and feature selection could enhance prediction quality  

The dataset remains a valuable benchmark for machine learning applications in the food & beverage industry and demonstrates how objective measurements can predict subjective sensory evaluations.


