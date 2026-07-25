# Titanic Survival Prediction with Decision Tree

This project is a machine learning application designed to predict the survival of passengers on the Titanic using the **Decision Tree Classifier**. For comparison, the performance is also evaluated against the **K-Nearest Neighbors (KNN)** algorithm.

## 📋 Project Overview
The notebook demonstrates a comprehensive data science workflow, including:
- **Data Cleaning:** Removing duplicates and handling missing values.
- **Preprocessing:** Label encoding for categorical variables and feature scaling.
- **Model Training:** Implementing Decision Tree and KNN classifiers.
- **Evaluation:** Measuring performance using accuracy scores.
- **Visualization:** Plotting the decision-making logic of the Tree model.

## 🛠️ Technologies Used
- **Python 3.x**
- **Pandas**: Data manipulation and analysis.
- **Scikit-learn**: Machine learning algorithms and preprocessing tools.
- **Matplotlib**: Data visualization and tree plotting.
- **Jupyter Notebook**: Interactive development environment.

## 📂 Dataset
The project utilizes the `titanic.csv` dataset, which includes passenger details such as:
- **Pclass**: Passenger Class (1, 2, or 3)
- **Sex / Age**: Demographic information.
- **SibSp / Parch**: Family relations on board.
- **Fare**: Ticket price.
- **Survived**: Target variable (0 = No, 1 = Yes).

## 🚀 Key Steps in the Notebook
1. **Handling Missing Values:** Automatically identifies null values and fills them with the most frequent value (Mode) of each column.
2. **Feature Engineering:** Converts categorical text data into numerical format using `LabelEncoder`.
3. **Data Scaling:** Uses `StandardScaler` to ensure all features contribute equally to the model's distance calculations.
4. **Classification:** 
   - Trains a **KNN** model with 5 neighbors.
   - Trains a **Decision Tree** model with a fixed random state for reproducibility.
5. **Visualization:** Generates a detailed graphical representation of the Decision Tree to understand the survival criteria.

## 📊 Results
The notebook outputs the accuracy for both models:
- **KNN Accuracy**: (Check notebook output)
- **Decision Tree Accuracy**: (Check notebook output)

## 🔧 Installation & Usage
1. Clone the repository:
```bash
   git clone https://github.com/Rezajediyatmonfared/Titanic-Decision-Tree.git
   

