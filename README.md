# 🛒 SmartKart — Customer Churn Prediction

## End-to-End Machine Learning Pipeline Using Logistic Regression

SmartKart Customer Churn Prediction is a machine learning project designed to identify customers who are likely to leave a retail business.

The project takes a **messy customer dataset** and processes it through a complete machine learning pipeline — from data collection and cleaning to model training, evaluation, interpretation, and generation of a business-ready churn risk report.

The project was developed as part of **Introduction to AI & ML | BBA AI/ML | Chitkara Business School**.

---

## 🎯 Business Problem

Customer churn occurs when customers stop purchasing from or using a business.

For SmartKart, identifying customers who are likely to churn can help the retention team take action before the customer leaves.

The main objective of this project is:

> **Predict which SmartKart customers are likely to churn and identify the factors that contribute to customer churn.**

The model uses customer information such as:

* Age
* Monthly Spend
* Number of Complaints

to predict:

* **0 → No Churn**
* **1 → Churn**

---

## 📊 Dataset

The project uses:

`SmartKart_dirty_100_rows.csv`

The dataset contains **100 customer records** and is intentionally designed to contain real-world data-quality problems, including:

* Missing values
* Duplicate records
* Extra whitespace
* Incorrect data types
* Invalid ages
* Negative spending values
* Extreme outliers

The original dataset contains five columns:

| Column          | Description                              |
| --------------- | ---------------------------------------- |
| `Customer_ID`   | Unique customer identifier               |
| `Age`           | Customer age                             |
| `Monthly_Spend` | Customer's monthly spending              |
| `Complaints`    | Number of customer complaints            |
| `Churn`         | Target variable: 0 = No Churn, 1 = Churn |

---

## 🔄 Machine Learning Pipeline

The notebook follows a complete **15-step machine learning pipeline**:

1. Data Collection
2. Data Understanding
3. Data Cleaning
4. Outlier Detection & Treatment
5. Feature Selection
6. Define Target Variable
7. Encode Target Variable
8. Train-Test Split
9. Feature Standardisation
10. Model Building
11. Model Training
12. Prediction
13. Model Evaluation
14. Model Interpretation
15. Final Business Output

---

## 🧹 Data Cleaning

The raw dataset contains several data-quality issues.

The project handles these issues by:

* Removing duplicate records
* Removing unnecessary whitespace
* Converting `Age` from text to numeric
* Correcting the `"thirty"` value to `30`
* Detecting invalid ages
* Removing negative spending values
* Filling missing values using the median

## After cleaning, the dataset contains **95 records**, with missing values handled.

## 📈 Outlier Treatment

Extreme values are detected using the **IQR (Interquartile Range)** method.

Outliers are capped instead of deleting the entire customer record.

This is applied to:

* `Monthly_Spend`
* `Complaints`

For example, the extreme monthly spending value of `99999` is capped to a reasonable upper boundary, while the complaints outlier of `50` is also treated.

---

## 🧠 Feature Selection

The model uses three business-relevant features:

```text
Age
Monthly_Spend
Complaints
```

`Customer_ID` is excluded because it is an identifier rather than a meaningful predictive feature.

---

## 🎯 Target Variable

The target variable is:

```text
Churn
```

Where:

```text
0 = No Churn
1 = Churn
```

## The target is already numeric, so additional encoding is not required.

## ✂️ Train-Test Split

The cleaned dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

Stratification is used to maintain a similar churn distribution between the training and testing datasets.

A fixed `random_state=42` is also used to make the results reproducible.

---

## ⚖️ Feature Standardisation

`StandardScaler` is used to standardise the numerical features.

The scaler is:

1. Fitted only on the training data
2. Applied to the training data
3. Applied to the test data using the same scaling parameters

This prevents information from the test set from leaking into the training process.

---

## 🤖 Machine Learning Model

The project uses:

### Logistic Regression

Logistic Regression is suitable because customer churn is a **binary classification problem**.

The model predicts:

```text
No Churn
      OR
Churn
```

It also provides a **churn probability**, which can be used to rank customers according to their risk level.

---

## 📏 Model Evaluation

The model is evaluated using standard classification metrics:

* Confusion Matrix
* Accuracy
* Precision
* Recall
* F1-Score
* Classification Report

The notebook indicates approximately:

* **Accuracy:** 89–95%
* **Recall:** approximately 100%
* **Precision:** approximately 83–91%

The exact values are generated when the notebook is executed.

> **Note:** These figures are based on the notebook's documented expected output; run the notebook to reproduce the exact metrics.

---

## 🔍 Model Interpretation

One of the most important parts of the project is understanding **why customers are likely to churn**.

The model's coefficients are analysed to understand the relationship between the features and churn risk.

### Key Business Insights

**Monthly Spend**

A strong negative coefficient indicates that higher monthly spending is associated with lower churn risk.

**Complaints**

A strong positive coefficient indicates that more customer complaints are associated with higher churn risk.

**Age**

Age has a smaller positive relationship with churn risk in this dataset.

### Main Business Takeaway

> **Reducing customer complaints and protecting high-spend customer relationships are important retention strategies for SmartKart.**

---

## 📋 Business-Ready Churn Report

The final output creates:

`smartkart_churn_risk_report.csv`

The report includes:

* Customer ID
* Age
* Monthly Spend
* Complaints
* Actual Churn
* Predicted Churn
* Churn Probability
* Risk Label

Customers are sorted by **churn probability**, allowing the retention team to focus on the highest-risk customers first.

Example risk labels:

```text
Likely to Churn
Not Likely to Churn
```

The notebook also identifies the **Top 5 highest-risk customers** for immediate retention attention.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Google Colab**
* **Jupyter Notebook**
* **Logistic Regression**

---

## 📁 Project Structure

```text
SmartKart-Customer-Churn-Prediction/
│
├── SmartKart (1).ipynb
├── SmartKart_dirty_100_rows.csv
├── smartkart_churn_risk_report.csv
└── README.md
```

---

## ▶️ How to Run

### Option 1 — Google Colab

1. Open `SmartKart (1).ipynb` in Google Colab.
2. Run the notebook from top to bottom.
3. When prompted, upload:

```text
SmartKart_dirty_100_rows.csv
```

4. Execute all cells.
5. The model will clean the data, train Logistic Regression, evaluate predictions, and generate the final churn report.

The notebook specifically instructs users to upload the CSV and run the cells sequentially.

### Option 2 — Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Then start Jupyter:

```bash
jupyter notebook
```

Open:

```text
SmartKart (1).ipynb
```

and run the cells from top to bottom.

---

## 💼 Business Applications

The SmartKart churn prediction system can help a retail business:

* Identify high-risk customers
* Prioritize retention campaigns
* Reduce customer loss
* Analyse customer complaints
* Identify valuable customers
* Create targeted retention offers
* Support data-driven marketing decisions

Instead of treating every customer equally, the business can focus its retention resources on customers with the highest predicted churn probability.

---

## 📌 Project Outcome

This project demonstrates a complete machine learning workflow:

```text
Raw Customer Data
        ↓
Data Inspection
        ↓
Data Cleaning
        ↓
Outlier Treatment
        ↓
Feature Selection
        ↓
Train-Test Split
        ↓
Feature Standardisation
        ↓
Logistic Regression
        ↓
Prediction
        ↓
Model Evaluation
        ↓
Model Interpretation
        ↓
Customer Churn Risk Report
```

The final result is not only a trained machine learning model but also a **business-oriented customer retention tool**.

---

## 🎓 Learning Objectives

This project demonstrates practical understanding of:

* Data preprocessing
* Data cleaning
* Missing-value treatment
* Duplicate removal
* Outlier detection
* Feature selection
* Target-variable preparation
* Train-test splitting
* Feature standardisation
* Logistic Regression
* Classification metrics
* Confusion matrix
* Model interpretation
* Business decision-making using ML

---

## 🚀 Future Improvements

Possible future enhancements include:

* Testing additional classification algorithms
* Hyperparameter tuning
* Cross-validation
* Larger customer datasets
* More customer behavioural features
* ROC-AUC analysis
* Interactive churn dashboard
* Automated retention recommendations
* Deployment as a web application

---

## 👨‍💻 Project Information

**Project:** SmartKart — Customer Churn Prediction
**Domain:** Artificial Intelligence & Machine Learning
**Model:** Logistic Regression
**Problem Type:** Binary Classification
**Dataset Size:** 100 raw customer records
**Primary Goal:** Customer Churn Prediction & Retention Analysis

---

## ⭐ Conclusion

SmartKart demonstrates how machine learning can convert messy customer data into actionable business insights.

By combining data cleaning, statistical preprocessing, Logistic Regression, model evaluation, and customer risk ranking, the project provides a practical approach to identifying customers who may leave and helping businesses take preventive retention action.
# smartkart
SmartKart Customer Churn Prediction using Machine Learning | End-to-end Logistic Regression pipeline for predicting customer churn, analyzing churn drivers, and generating a business-ready customer risk report.
