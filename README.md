# Customer Churn Prediction Using Machine Learning

## 📌 Project Overview

This project focuses on predicting customer churn in the telecommunications industry using Machine Learning classification algorithms.

The primary objective is to identify customers who are likely to discontinue their services, enabling businesses to take proactive retention measures.

Multiple classification algorithms were evaluated, along with class-imbalance handling techniques, to compare their performance using Accuracy, Precision, Recall, F1-Score, and Confusion Matrix.

---

## 📊 Dataset

The dataset contains customer information from a telecommunications company.

### Features:

- **CustomerID:** Unique identifier for each customer
- **Gender:** Customer gender
- **SeniorCitizen:** Whether the customer is a senior citizen
- **Partner:** Whether the customer has a partner
- **Dependents:** Whether the customer has dependents
- **Tenure:** Number of months the customer has stayed with the company
- **PhoneService:** Whether phone service is subscribed
- **MultipleLines:** Whether multiple phone lines are subscribed
- **InternetService:** Type of internet service
- **OnlineSecurity:** Whether online security service is subscribed
- **OnlineBackup:** Whether online backup service is subscribed
- **DeviceProtection:** Whether device protection service is subscribed
- **TechSupport:** Whether technical support is subscribed
- **StreamingTV:** Whether streaming TV service is subscribed
- **StreamingMovies:** Whether streaming movies service is subscribed
- **Contract:** Customer contract type
- **PaperlessBilling:** Whether paperless billing is enabled
- **PaymentMethod:** Customer payment method
- **MonthlyCharges:** Monthly service charges
- **TotalCharges:** Total charges incurred by the customer
- **Churn:** Target variable
  - `0` – Customer retained
  - `1` – Customer churned

The dataset contains approximately 7,043 customer records, with churn representing a minority class, making it a class-imbalanced classification problem.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Imbalanced-learn
- Flask
- Pickle
- Jupyter Notebook
- HTML
- CSS

---

## 🔍 Project Workflow

1. Data Loading
2. Exploratory Data Analysis (EDA)
3. Data Cleaning
4. Missing Value Analysis
5. Feature Engineering
6. Categorical Feature Encoding
7. Train-Test Split
8. Baseline Model Development
9. Model Comparison
10. Class Imbalance Handling
11. Model Evaluation
12. PCA Experimentation
13. Final Model Selection
14. Model Serialization
15. Flask Application Development

---

## 🤖 Machine Learning Models

The following classification algorithms were implemented and evaluated:

- Decision Tree Classifier
- Random Forest Classifier

Additional experiments were performed using:

- Decision Tree with SMOTEENN
- Random Forest with SMOTEENN
- Random Forest with PCA

---

## ⚖️ Handling Class Imbalance

Due to the imbalance between churn and non-churn customers, SMOTEENN was explored.

### Techniques:

- **SMOTE (Synthetic Minority Over-sampling Technique):** Generates synthetic samples for the minority class.
- **ENN (Edited Nearest Neighbors):** Removes potentially noisy samples based on nearest-neighbor relationships.
- **SMOTEENN:** Combines oversampling with noise removal to improve minority-class learning.

These techniques were used to investigate their impact on customer churn detection performance.

---

## 🔧 Feature Engineering & Preprocessing

- Converted `TotalCharges` into numerical format.
- Handled missing values.
- Grouped customer tenure into intervals.
- Removed irrelevant features such as `customerID`.
- Removed the original `tenure` feature after creating `tenure_group`.
- Converted categorical variables into numerical representations using One-Hot Encoding.
- Encoded the target variable `Churn` into binary values.

---

## 📈 Evaluation Metrics

Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix

Particular emphasis was placed on Recall and F1-Score because failing to identify customers who are likely to churn can result in lost revenue, while excessive false positives can lead to unnecessary retention campaigns.

---

## 🏆 Results

The Random Forest model combined with SMOTEENN demonstrated the strongest reported performance in the experiments.

### Best reported results:

- **Accuracy:** 94.27%
- **Precision:** 94%
- **Recall:** 96%
- **F1-Score:** 95%

### Confusion Matrix

| | Predicted No Churn | Predicted Churn |
|---|---:|---:|
| Actual No Churn | 478 | 40 |
| Actual Churn | 27 | 625 |

Additional experiments were performed using PCA to reduce dimensionality, but the PCA-based model did not improve performance compared with the Random Forest model without PCA.

*Note: The reported results were obtained using a resampling workflow that requires correction to prevent data leakage. These metrics should be revalidated using a proper train-test split before being treated as reliable unseen-data performance.*

---

## 🌐 Application Development

The trained model was saved using Pickle (`model.sav`) and integrated into a Flask web application.

The application allows users to:

- Enter customer information
- Submit customer data through a web form
- Generate churn predictions
- View the predicted churn class
- View the estimated churn probability

### Application Workflow

Customer Input → HTML Form → Flask Backend → Data Preprocessing → Saved ML Model (`model.sav`) → Prediction → Churn / No Churn → Prediction Probability

---

## 📁 Project Structure

ChurnPrediction/
│
├── Churn Analysis - EDA.ipynb
├── Churn Analysis - Model Building.ipynb
├── app.py
├── model.sav
│
├── WA_Fn-UseC_-Telco-Customer-Churn.csv
├── tel_churn.csv
├── first_telc.csv
│
├── templates/
│   └── home.html
│
└── README.md

---

## 🔮 Future Improvements

- Implement a robust Stratified Cross-Validation pipeline.
- Apply SMOTEENN exclusively to training data to prevent data leakage.
- Perform systematic hyperparameter optimization using GridSearchCV or RandomizedSearchCV.
- Compare additional models such as XGBoost, LightGBM, and CatBoost.
- Evaluate models using ROC-AUC and PR-AUC.
- Optimize classification thresholds based on business costs.
- Improve probability calibration.
- Implement feature importance and SHAP-based explainability.
- Save preprocessing and model components together using a Pipeline.
- Improve input validation and feature consistency in the Flask application.
- Deploy the application using Streamlit, Flask, or a cloud platform.
- Monitor model performance and data drift.
- 
