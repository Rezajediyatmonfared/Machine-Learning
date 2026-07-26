# California Housing Analysis: Comparative Study of Regression Models

This project presents a comparative machine learning analysis on the **California Housing dataset**. The main goal is to predict house prices using different regression models and evaluate their performance through multiple statistical metrics.

In addition to regression, the project also includes a binary classification task using Logistic Regression to identify whether a house belongs to the high-value category.

---

## 📌 Project Overview

This notebook demonstrates a complete machine learning workflow, including:

- Data loading
- Data cleaning
- Missing value handling
- Outlier removal
- Categorical feature encoding
- Feature scaling
- Model training
- Model evaluation
- Final comparison of results

The project compares the performance of the following models:

1. **Simple Linear Regression**
2. **Multiple Linear Regression**
3. **Polynomial Regression**
4. **Logistic Regression** for classification

---

## 📂 Dataset

The dataset used in this project is:

- `housing.csv`

It contains information related to housing districts in California, including both numerical and categorical features.

### Main Features

- `longitude`
- `latitude`
- `housing_median_age`
- `total_rooms`
- `total_bedrooms`
- `population`
- `households`
- `median_income`
- `ocean_proximity`

### Target Variable

For the regression task, the target variable is:

- `median_house_value`

For the classification task, the target is converted into a binary label:

- `1` → house value is greater than or equal to **200,000**
- `0` → house value is less than **200,000**

---

## ⚙️ Workflow

### 1. Data Loading
The dataset is loaded into a Pandas DataFrame for analysis and preprocessing.

### 2. Missing Value Handling
Missing values in the `total_bedrooms` column are filled using the median value of the same column. This helps preserve the dataset size while avoiding bias from extreme values.

### 3. Outlier Removal
Outliers are removed using the **Interquartile Range (IQR)** method. This step improves model performance by reducing the effect of extreme observations.

The following columns are processed for outlier removal:

- `total_rooms`
- `total_bedrooms`
- `population`
- `households`
- `median_house_value`

### 4. Categorical Encoding
The `ocean_proximity` column is transformed into numerical format using **one-hot encoding**.

### 5. Feature Scaling
All input features are standardized using `StandardScaler` to improve model performance and ensure fair comparisons between features with different ranges.

### 6. Train-Test Split
The dataset is divided into training and testing sets using an 80/20 ratio for model evaluation.

---

## 🤖 Models Used

### A. Simple Linear Regression
This model uses only one feature, **median_income**, to predict house prices.

It is useful for understanding the relationship between income and house value in a simple and interpretable way.

### B. Multiple Linear Regression
This model uses all available processed features to predict house prices.

It provides a stronger baseline than simple linear regression by incorporating more information from the dataset.

### C. Polynomial Regression
Polynomial Regression extends linear regression by adding nonlinear feature interactions.

In this project, a **degree-2 polynomial transformation** is used to capture more complex relationships between variables and the target.

### D. Logistic Regression
For classification, house prices are converted into two categories: high-value and low-value.

Logistic Regression is then applied to classify houses into these two groups.

---

## 📊 Evaluation Metrics

### Regression Metrics
The regression models are evaluated using:

- **Mean Squared Error (MSE)**
- **Root Mean Squared Error (RMSE)**
- **Mean Absolute Error (MAE)**
- **R-squared (R²)**

These metrics help compare how well each regression model predicts house prices.

### Classification Metrics
The Logistic Regression model is evaluated using:

- **Accuracy**
- **F1-Score**

These metrics are suitable for measuring overall classification performance and balance between precision and recall.

---

## 🧪 Results and Comparison

The notebook creates a comparison table for the regression models, making it easier to analyze their predictive performance side by side.

It also reports the classification results of Logistic Regression, allowing the project to demonstrate both:

- **continuous value prediction**
- **binary category prediction**

This dual approach makes the notebook a strong example of both regression and classification in one project.

---

## 📁 Project Structure
```bash
California-Housing-Analysis/
│
├── California_Housing_Analysis.ipynb
├── housing.csv
└── README.md

