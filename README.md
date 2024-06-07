# Predicting-Customer-Churn-For-A-Leading-Telecom_Company

## Motivation
Customer churn, also known as customer attrition or turnover, is the loss of clients or customers. It is a critical metric for businesses because retaining existing customers is often much less expensive than acquiring new ones. By predicting the likelihood of a customer churning, companies can identify a small subgroup of at-risk customers and focus retention efforts on them, potentially preventing churn and maintaining revenue.

## Dataset Source and Information
The dataset used for this analysis contains information on 7,043 customers from a telecommunications company in California during Q2 2022. Each record represents one customer and includes details about demographics, location, tenure, subscription services, and status for the quarter (whether they joined, stayed, or churned).

The dataset can be found on the Maven Analytics website and on Kaggle:

- [Maven Analytics Dataset](https://www.mavenanalytics.io/)
- [Kaggle Link](https://www.kaggle.com/)

## About the Data
The dataset includes the following information:

- **Demographics:** Gender, age, marital status, number of dependents, etc.
- **Location:** City, zip code, latitude, longitude
- **Services:** Phone service, multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV, streaming movies, streaming music, unlimited data
- **Account Information:** Tenure, contract type, payment method, paperless billing, monthly charges, total charges
- **Status:** Customer status for the quarter (joined, stayed, churned)

## Solution Approach
### 1. Reading and Understanding the Dataset
We start by importing the necessary libraries and loading the dataset. We explore the dataset to understand its structure and identify any missing or null values.

### 2. Data Preprocessing and Cleaning
- **Handling Null Values:** We replace null values for various columns with appropriate values based on logical assumptions (e.g., 'No Internet', 'No Phone Service').
- **Dropping Irrelevant Columns:** Columns like Customer ID, Churn Category, and Churn Reason are dropped as they are not relevant for prediction.
- **Categorical Encoding:** We convert categorical variables into a suitable format for machine learning models using one-hot encoding.
- **Finding Outliers:** We use box plots to identify outliers in numerical columns and address them accordingly.

### 3. Feature Selection
We use a combined feature selection strategy:
- **Univariate Feature Selection:** `SelectKBest` with ANOVA F-value to select the top 50 features.
- **Sequential Feature Selection:** Forward Sequential Selection to narrow down to the best 25 features.

### 4. Model Training and Evaluation
We train four different classification models on the selected features:
- Random Forest Classifier
- K-Nearest Neighbor (kNN)
- Support Vector Machine (SVM)
- Logistic Regression

The Random Forest Classifier performed the best with a balanced accuracy of 81.58%.

### 5. Accounting for Imbalanced Data
We use a balanced class weight in the Random Forest Classifier to improve performance on imbalanced data, resulting in a balanced accuracy of 82.0%.

### 6. Hyperparameter Tuning
We perform hyperparameter tuning using the following methods:
- Random Search
- Grid Search
- Halving Random Search
- Halving Grid Search

The best performance was achieved using Halving Random Search, with a balanced accuracy of 85.72%.

### 7. Model Evaluation on Test Data
We evaluate the final model on the test data, achieving a balanced accuracy of 85.42%.

### 8. Boosting
We implement HistGradientBoosting, achieving a balanced accuracy of 84.6%, slightly lower than the hyper-tuned Random Forest model.

### 9. Conclusion
Our analysis identified several key variables that influence customer churn, including:
- Family characteristics (age, marital status, number of dependents)
- Location (San Diego)
- Payment method (credit card)
- Contract type
- Charges (monthly, total)
- Internet type
- Certain services (premium tech support, streaming TV, streaming music, online security, online backup)

The Random Forest Classifier, after hyperparameter tuning and accounting for imbalanced data, provided the best results for predicting customer churn.

## Project Repository
The detailed analysis and model training process can be found in the following Colab notebook: [Predicting Customer Churn](https://colab.research.google.com/drive/1ESG-0_R_BaalfDB23EMYnNj8LGRYjXZy?usp=sharing).

For further inquiries or collaboration, please feel free to reach out.
