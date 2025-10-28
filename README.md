# 🩺 Health Insurance Premium Prediction Project  

A complete **Machine Learning project** designed to predict **health insurance premium amounts** based on demographic, lifestyle, and medical details.  
This work combines **EDA, Feature Engineering, Model Training, Hyperparameter Tuning**, and **Deployment** using **Streamlit**.

---

## 🧩 Project Overview  

This project has two major parts:

1. **Premium Prediction for Young Individuals (≤ 25 years)**  
   → Developed and trained using `ml_premium_prediction_young_with_gr.ipynb`  
2. **Premium Prediction for Rest of the Population (> 25 years)**  
   → Developed and trained using `ml_premium_prediction_rest_with_gr.ipynb`

Both models were trained, evaluated, and saved (`joblib` format) for use in a **Streamlit-based web app** that predicts insurance cost dynamically.

---

## 📊 Objectives  

- Clean and preprocess raw insurance datasets  
- Engineer medical risk and income-related features  
- Train and compare **Linear Regression**, **Ridge**, and **XGBoost** models  
- Evaluate model performance using **R²**, **RMSE**, and **cross-validation**  
- Deploy final models via **Streamlit UI**

---

## 🧠 Key Steps  

### 1️⃣ Data Cleaning  
- Removed missing values and duplicates  
- Corrected negative values in `number_of_dependants`  
- Handled inconsistent categories in `smoking_status`  

### 2️⃣ Feature Engineering  
- Encoded categorical features using **One-Hot Encoding**  
- Mapped ordinal features like **insurance_plan** and **income_level**  
- Calculated a **Normalized Medical Risk Score** using disease combinations  

### 3️⃣ Outlier Treatment  
- Removed extreme values in `age` and `income_lakhs` using IQR and quantile thresholds  

### 4️⃣ Scaling  
- Scaled numerical columns using **MinMaxScaler**  
- Separate scalers for **young** and **rest** populations  

### 5️⃣ Model Training  
Tested and compared multiple models:
| Model | Dataset | R² (Train) | R² (Test) | RMSE |
|--------|----------|-------------|-------------|-------|
| Linear Regression | Young | 0.9819 | 0.9820 | 394 |
| Ridge Regression | Young | 0.9819 | 0.9820 | 395 |
| XGBoost | Young | 0.9880 | 0.9795 | 395 |
| Linear Regression | Rest | 0.9113 | 0.9100 | 1668 |
| Ridge Regression | Rest | 0.9113 | 0.9101 | 1668 |
| XGBoost | Rest | 0.9625 | 0.9421 | 1668 |

✅ **Final Models Selected:**  
- **Young Group:** Linear Regression (simpler & stable)  
- **Rest Group:** XGBoost (higher accuracy & generalization)

---

## 📁 Artifacts Saved  

| File | Description |
|------|--------------|
| `model_young.joblib` | Trained model for young group |
| `model_rest.joblib` | Trained model for rest group |
| `scaler_young.joblib` | MinMaxScaler for young dataset |
| `scaler_rest.joblib` | MinMaxScaler for rest dataset |

---

## 🌐 Streamlit Web App  

**App Name:** Health Insurance Cost Predictor  

**Features:**  
- Collects user info (Age, Income, BMI, Smoking, Region, etc.)  
- Preprocesses data and calculates normalized risk  
- Chooses correct model based on age  
- Predicts health insurance premium instantly  

**Command to Run:**
```bash
streamlit run app.py
