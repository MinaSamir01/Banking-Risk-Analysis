# Banking Risk Analysis: EDA, Power BI and Logistic Regression

## 📌 Project Overview

This project analyzes banking client data to support **risk assessment** and identify clients who are more likely to be classified as **high-risk**. The project combines three main data analysis stages:

1. **Exploratory Data Analysis (EDA)** using Python  
2. **Interactive dashboard development** using Power BI  
3. **Predictive modeling** using Logistic Regression  

The main goal is to help a financial institution better understand client behavior, monitor key banking indicators, and predict high-risk clients based on demographic and financial features.

---

## 🎯 Business Problem

Banks need to assess client risk accurately before making decisions related to loans, credit limits, and financial services. Poor risk classification can lead to two major problems:

- Giving credit or loans to clients who may default or delay payments.
- Rejecting clients who are financially capable, resulting in missed business opportunities.

This project addresses this problem by building a data-driven risk analysis workflow that classifies clients into **high-risk** and **low/medium-risk** groups.

---

## ✅ Project Objectives

The project aims to:

- Analyze client demographic and financial data.
- Clean and prepare the dataset for analysis and modeling.
- Explore client behavior using visualizations and statistical summaries.
- Build Power BI dashboards to monitor banking performance and client segments.
- Train a Logistic Regression model to predict whether a client is high-risk.
- Evaluate the model using accuracy, precision, recall, F1-score, confusion matrix, ROC curve, and AUC score.
- Provide business recommendations for improving banking risk management.

---

## 🧰 Tools and Technologies

- **Python**
  - pandas
  - NumPy
  - matplotlib
  - seaborn
  - scikit-learn
  - imbalanced-learn / SMOTE
- **Power BI**
  - Power Query
  - Data Modeling
  - DAX Measures
  - Interactive Dashboards
- **PowerPoint**
  - Final project presentation
- **GitHub**
  - Project documentation and version control

---

## 📊 Dataset Description

The dataset contains client-level banking information, including demographic details, financial balances, banking relationships, and risk classification.

### Key Features

| Feature | Description |
|---|---|
| Age | Client age |
| Estimated Income | Client estimated annual income |
| Credit Card Balance | Outstanding credit card balance |
| Bank Loans | Total bank loan amount |
| Bank Deposits | Total deposits held by the client |
| Checking Accounts | Checking account balance/value |
| Saving Accounts | Saving account balance/value |
| Foreign Currency Account | Foreign currency account value |
| Business Lending | Business lending amount |
| Properties Owned | Number/value of properties owned |
| Nationality | Client nationality category |
| Gender | Client gender |
| Banking Relationship | Relationship type with the bank |
| Investment Advisor | Assigned investment advisor |
| Risk Weighting | Risk category used for analysis and modeling |
| Income Band | Created income segmentation: Low, Medium, High |

The target variable for the machine learning model is based on **Risk Weighting**, where clients are classified as high-risk or low/medium-risk.

---

## 🔄 Project Workflow

```text
Raw Banking Data
        ↓
Data Cleaning and Preprocessing
        ↓
Exploratory Data Analysis
        ↓
Power BI Data Modeling
        ↓
Dashboard Development
        ↓
Logistic Regression Modeling
        ↓
Model Evaluation
        ↓
Business Insights and Recommendations
```

---

## 🧹 Data Cleaning and Preprocessing

The dataset was checked and prepared before analysis.

Main cleaning steps included:

- Checking for missing values.
- Checking for duplicate rows.
- Verifying data types.
- Converting the `Joined Bank` column to datetime format.
- Creating an `Income Band` column to segment clients into:
  - Low Income
  - Medium Income
  - High Income
- Creating a binary target variable for high-risk prediction.

The dataset was found to have:

- No missing values.
- No duplicate rows.
- Corrected date formatting for time-based analysis.

---

## 📈 Exploratory Data Analysis

EDA was performed to understand the structure of the data, identify relationships, and discover useful business insights.

### 1. Income Band Distribution

The majority of clients fall into the **Medium Income** band, followed by Low Income and then High Income.

**Insight:**  
The bank’s client base is mainly concentrated in the medium-income segment, which may influence product design, financial planning, and risk strategy.

---

### 2. Risk Weighting Distribution

Risk Weighting 2, representing moderate risk, was the most common classification. Higher-risk categories had fewer clients.

**Insight:**  
The dataset contains many moderately risky clients, making this group important for risk monitoring and model training.

---

### 3. Nationality Distribution

European clients formed the largest group in the dataset, followed by American and Asian clients.

**Insight:**  
The bank appears to serve a large European client segment, which may be useful for targeted financial products and customer segmentation.

---

### 4. Income Band by Nationality

The analysis showed differences in income distribution across nationalities:

- European clients were more concentrated in the Medium Income band.
- American clients were more evenly distributed between Low and Medium Income bands.
- Asian clients were more concentrated in the Low Income band.

**Insight:**  
Nationality and income band may be useful variables for segmentation and predictive modeling.

---

### 5. Correlation Analysis

The correlation matrix showed important financial relationships:

- **Bank Deposits** and **Saving Accounts** had a strong positive correlation.
- **Checking Accounts** and **Bank Deposits** also had a strong positive relationship.
- The scatter plot between Bank Deposits and Saving Accounts showed a clear positive trend.

**Insight:**  
Clients with larger deposits often also have higher savings, which can help in understanding financial capacity and risk level.

---

## 📊 Power BI Dashboard

The Power BI report was designed to make the analysis interactive and business-friendly.

### Dashboard Pages

The report includes the following pages:

1. **Banking Dashboard Home**
2. **Loan Analysis Dashboard**
3. **Deposit Analysis Dashboard**
4. **Summary Dashboard**
5. **Client-Level Data Dashboard**

---

## 🧱 Power BI Data Model

The Power BI model was designed using a fact-and-dimension structure.

### Main Fact Table

- **Clients - Banking**

This table contains the main client-level banking and financial metrics such as deposits, loans, credit card balances, income, and risk weighting.

### Dimension Tables

- **Banking Relationship**
- **Investment Advisor**
- **Gender**

The model uses relationships between the main client banking table and the dimension tables to allow filtering, slicing, and interactive analysis.

---

## 🧮 DAX Measures

Several DAX measures were created to summarize key banking metrics.

Examples include:

```DAX
Total Clients = COUNTROWS('Clients - Banking')

Total Deposits = SUM('Clients - Banking'[Bank Deposits])

Total Loans = SUM('Clients - Banking'[Bank Loans])

Total Fees = SUM('Clients - Banking'[Total Fees])
```

These measures allow the dashboard to respond dynamically to filters such as gender, banking relationship, and investment advisor.

---

## 📌 Dashboard Key Metrics

The dashboard highlights the following main KPIs:

| Metric | Value |
|---|---:|
| Total Clients | 2,940 |
| Total Deposits | $3.77bn |
| Total Loans | $4.38bn |
| Bank Loans | $1.77bn |
| Business Lending | $2.60bn |
| Total Fees | $158.19M |
| Bank Deposits | $2.01bn |
| Savings Account Amount | $698.73M |
| Checking Account Amount | $963.28M |
| Foreign Currency Amount | $89.65M |
| Credit Card Balance | $9.53M |

---

## 🤖 Machine Learning Model

A **Logistic Regression** model was implemented to classify clients as either:

- **High Risk**
- **Low/Medium Risk**

Logistic Regression was selected because it is suitable for binary classification problems and provides interpretable coefficients that help explain how each feature affects the probability of being high-risk.

---

## ⚖️ Handling Class Imbalance

The dataset had an imbalance between high-risk and low/medium-risk clients.

To address this issue, the model used:

- `class_weight='balanced'` in Logistic Regression
- SMOTE (Synthetic Minority Oversampling Technique)

These methods helped the model pay more attention to the minority class, which is the high-risk client group.

---

## 🧪 Model Evaluation

The model was evaluated using several classification metrics.

### Overall Performance

| Metric | Result |
|---|---:|
| Accuracy | 69% |
| AUC Score | 0.81 |

The model achieved an AUC score of **0.81**, which means it has a good ability to distinguish between high-risk and low/medium-risk clients.

---

## 📉 Confusion Matrix

|  | Actual High Risk | Actual Low/Medium Risk |
|---|---:|---:|
| Predicted High Risk | 72 | 159 |
| Predicted Low/Medium Risk | 26 | 343 |

### Interpretation

- **True Positives:** 72 high-risk clients were correctly identified.
- **True Negatives:** 343 low/medium-risk clients were correctly identified.
- **False Positives:** 159 low/medium-risk clients were incorrectly classified as high-risk.
- **False Negatives:** 26 high-risk clients were missed by the model.

---

## 📋 Classification Report Summary

| Class | Precision | Recall | F1-Score |
|---|---:|---:|---:|
| Low/Medium Risk | 0.93 | 0.68 | 0.79 |
| High Risk | 0.31 | 0.73 | 0.44 |

### Key Interpretation

The model is better at detecting high-risk clients than avoiding false alarms:

- High-risk recall is **73%**, meaning the model captures most actual high-risk clients.
- High-risk precision is **31%**, meaning many clients predicted as high-risk are actually low/medium-risk.
- This trade-off may be acceptable in risk management because missing a truly high-risk client can be more costly than reviewing extra false positives.

---

## 🔍 Model Coefficient Insights

The Logistic Regression coefficients showed how different features affect the probability of being high-risk.

### Important Feature Effects

| Feature | Effect on Risk |
|---|---|
| Age | Negative effect — older clients tend to have lower risk |
| Properties Owned | Negative effect — more owned properties are associated with lower risk |
| Credit Card Balance | Positive effect — higher balances increase risk |
| Foreign Currency Account | Small positive effect |
| Estimated Income | Small positive effect |

---

## 💡 Business Insights

The project produced several useful business insights:

- Medium-income clients represent the largest part of the customer base.
- Moderate-risk clients are the most common risk group.
- European clients dominate the dataset and contribute strongly to loan amounts.
- Bank Deposits and Saving Accounts have a strong positive relationship.
- Business lending represents a large part of the bank’s loan portfolio.
- Foreign currency balances suggest opportunities for international banking services.
- High-fee clients can be targeted for premium or personalized banking services.
- The Logistic Regression model can support early identification of high-risk clients.

---

## ✅ Recommendations

Based on the analysis, the bank could:

- Monitor clients predicted as high-risk more closely.
- Improve credit review processes using model-based risk scoring.
- Offer financial counseling or preventive support to high-risk clients.
- Create tailored loan products for profitable client segments.
- Improve savings account incentives to increase long-term deposits.
- Explore foreign currency products for internationally active clients.
- Use personalized services to retain high-value clients.
- Improve the model in the future by adding repayment history, transaction behavior, and more detailed credit history.

---

## 🧾 Project Summary

This project demonstrates a complete data analysis and machine learning workflow for banking risk analysis. It starts with data cleaning and EDA, continues with Power BI dashboard development, and ends with a Logistic Regression model for predicting high-risk clients.

The project shows how data analytics can support financial institutions in:

- Understanding customer behavior.
- Monitoring key banking metrics.
- Identifying high-risk clients.
- Supporting better credit and risk management decisions.

---

## 👤 Author

**Mina Samir Mounir Gaballah Abadir**

Academic project supervised by **Dr. Nesrine Nabil**  
Faculty of Science, Alexandria University  
2025
