# 🏠 House Prices – Advanced Regression Techniques (Kaggle)

This repository contains my solution to the **Kaggle: House Prices – Advanced Regression Techniques** competition. The goal of this project is to predict the final sale price of residential homes in Ames, Iowa using advanced regression techniques, proper preprocessing, and feature engineering.

---

## 📌 Competition Overview

* **Competition**: House Prices – Advanced Regression Techniques
* **Platform**: Kaggle
* **Problem Type**: Supervised Regression
* **Dataset**: Ames Housing Dataset
* **Target Variable**: `SalePrice`
* **Evaluation Metric**: **RMSE on log-transformed SalePrice**

The dataset contains **79 explanatory variables** describing various aspects of residential homes such as location, size, quality, condition, and amenities.

---

## 🎯 Objective

For each house in the test dataset, predict the **final sale price**. The predictions are evaluated using:

> **Root Mean Squared Error (RMSE)** between the logarithm of predicted prices and actual prices.

This means the model is trained on:

```python
log(SalePrice)
```

and predictions are converted back using the exponential function.

---

## 📂 Dataset Description

The repository uses the official Kaggle dataset files:

* `train.csv` – Training data (features + target `SalePrice`)
* `test.csv` – Test data (features only)
* `sample_submission.csv` – Sample submission format
* `data_description.txt` – Detailed explanation of all features

---

## 🛠️ Approach & Methodology

### 1️⃣ Data Loading

* Loaded datasets directly from Kaggle input directory
* Verified shapes and column consistency

### 2️⃣ Target Transformation

* Applied **log1p transformation** to `SalePrice` to stabilize variance

### 3️⃣ Feature Handling

* **Numerical features**:

  * Missing values filled using median
  * Standardized using `StandardScaler`

* **Categorical features**:

  * Missing values filled using most frequent value
  * Encoded using `OneHotEncoder` with `handle_unknown='ignore'`

### 4️⃣ Pipeline Design

* Used `ColumnTransformer` and `Pipeline` to ensure:

  * No data leakage
  * Identical preprocessing for train and test sets

### 5️⃣ Model Selection

* Started with a Ridge Regression baseline
* Tuned regularization using **RidgeCV**
* Experimented with **ElasticNetCV** and validated performance using cross-validation

### 6️⃣ Model Evaluation

* Used **5-fold cross-validation**
* Metric: Negative Root Mean Squared Error

---

## 🤖 Models Used

* **Ridge Regression (RidgeCV)** – Primary and best-performing linear model
* **ElasticNetCV** – Tested but slightly underperformed for this setup

> Note: Gradient Boosting and tree-based models are potential future improvements.

---

## 📈 Results

* **Best Public Leaderboard Score**: ~`0.135`
* Achieved using:

  * Proper preprocessing
  * Log-transformed target
  * Cross-validated regularization

This score represents a solid baseline for the competition and demonstrates correct application of machine learning best practices.

---

## 📤 Submission Format

Predictions are saved in the following format:

```csv
Id,SalePrice
1461,169000.1
1462,187724.12
```

---

## 🚀 How to Run

1. Clone the repository
2. Open the notebook in Kaggle or Jupyter
3. Run all cells in order
4. Generate `submission.csv`
5. Upload the file to Kaggle

---

## 🧠 Key Learnings

* Importance of log-transforming skewed targets
* Power of simple linear models with proper preprocessing
* Cross-validation is more reliable than leaderboard scores
* Feature understanding matters more than model complexity

---

## 🔗 Competition Link

Kaggle Competition:
[https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)

---

## ✍️ Author

**Rahul Shetye**
Aspiring Data Scientist | Machine Learning Enthusiast

---

