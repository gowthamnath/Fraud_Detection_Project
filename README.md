Fraud Detection in Financial Transactions
Project Overview

This project focuses on detecting fraudulent transactions in a large financial dataset using Python, data analysis, and machine learning techniques. The dataset contains over 6 million transactions with features such as transaction type, amount, account balances, and flags for fraud. A machine learning model (Logistic Regression) is implemented to predict whether a transaction is fraudulent.

Additionally, a Streamlit app has been developed to provide an interactive interface for predicting fraud on new transactions.

Dataset

Source: https://www.kaggle.com/datasets/amanalisiddiqui/fraud-detection-dataset?resource=download

Size: 6,362,620 rows × 11 columns

Columns:

step – Time step of the transaction

type – Transaction type (PAYMENT, TRANSFER, CASH_OUT, DEBIT, CASH_IN)

amount – Transaction amount

nameOrig – Sender account

oldbalanceOrg – Initial balance of the sender

newbalanceOrig – New balance of the sender

nameDest – Receiver account

oldbalanceDest – Initial balance of the receiver

newbalanceDest – New balance of the receiver

isFraud – Fraud flag (0: Non-fraud, 1: Fraud)

isFlaggedFraud – Flagged by the system

Exploratory Data Analysis (EDA)

Checked for null values: None found

Transaction distribution:

CASH_OUT and PAYMENT are the most frequent

Fraud occurs mostly in TRANSFER and CASH_OUT transactions

Fraud transactions constitute only 0.13% of total transactions

Analyzed balances for anomalies:

Created features balancedifforg (difference in sender balance) and balancediffdest (difference in receiver balance)

Visualizations include:

Transaction type counts

Fraud distribution per transaction type

Transaction amount distribution (log scale)

Box plots comparing transaction amount vs fraud

Feature Engineering

Dropped columns: nameOrig, nameDest, isFlaggedFraud

Added features:

balancedifforg = oldbalanceOrg - newbalanceOrig

balancediffdest = newbalanceDest - oldbalanceDest

Machine Learning Model

Model: Logistic Regression

Preprocessing:

Numerical features: StandardScaler

Categorical features (type): OneHotEncoder

Handling imbalance: class_weight='balanced'

Train/Test Split: 70% train, 30% test (stratified)

Performance Metrics:

Accuracy: 94.57%

Confusion Matrix:

[[1802769, 103553],
 [    136,    2328]]


Classification Report:

Recall for fraud: 0.94 (good detection of frauds)

Precision for fraud: 0.02 (many false positives due to imbalance)

Streamlit App

Provides an interactive interface to input transaction details:

type, amount, oldbalanceOrg, newbalanceOrig, oldbalanceDest, newbalanceDest

Predicts whether the transaction is fraudulent in real-time

Uses the trained Logistic Regression pipeline
