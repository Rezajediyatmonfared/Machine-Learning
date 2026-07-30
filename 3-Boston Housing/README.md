# Regression and Classification Models Lab

A complete machine learning project covering **regression** and **classification** using Python, Scikit-learn, and TensorFlow.  
This project demonstrates the full workflow from **data loading and preprocessing** to **model training, evaluation, and visualization**.

---

## Project Overview

This project is divided into two main parts:

### 1. Regression on Boston Housing Dataset
In this section, different regression techniques are applied to the **Boston Housing** dataset in order to predict house prices (`MEDV`).

Implemented models:

- **Simple Linear Regression**
- **Multiple Linear Regression**
- **Polynomial Regression (Degree 2)**

The regression workflow includes:

- Loading the dataset from an alternative GitHub source
- Splitting data into training and testing sets
- Reconstructing the training DataFrame for analysis
- Performing correlation analysis
- Visualizing the correlation matrix using a heatmap
- Selecting highly relevant features
- Training and evaluating multiple regression models

### 2. Logistic Regression on Social Network Ads Dataset
In this section, a **binary classification** problem is solved using **Logistic Regression**.

The goal is to predict whether a user will purchase a product based on user-related features.

The classification workflow includes:

- Loading the Social Network Ads dataset from GitHub
- Selecting `Age` and `EstimatedSalary` as input features
- Using `Purchased` as the target label
- Splitting the dataset into training and testing sets
- Applying feature scaling
- Training a logistic regression model
- Evaluating the model using:
  - Confusion Matrix
  - Accuracy Score
- Visualizing the confusion matrix with Seaborn

---

## Technologies Used

This project uses the following libraries and tools:

- **Python**
- **NumPy**
- **Pandas**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **TensorFlow**

---

## Project Structure
```bash
project/
│
├── regression_classification.ipynb   # Main notebook
├── README.md                         # Project documentation
└── requirements.txt                  # Required libraries

