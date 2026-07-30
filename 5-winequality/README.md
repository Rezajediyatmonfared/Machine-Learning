# Wine Quality Analysis and Prediction

This project analyzes the red wine quality dataset using data preprocessing, clustering, classification, and feature selection. The goal is to explore the structure of the dataset, group wines into clusters, train machine learning models, and improve feature selection using a Genetic Algorithm.

## Project Objectives

- Load and inspect the wine quality dataset
- Preprocess and scale the features
- Analyze correlations between variables
- Apply K-Means clustering
- Train KNN and Decision Tree classifiers
- Compare model performance
- Use a Genetic Algorithm for feature selection
- Evaluate models before and after feature selection

## Dataset

The dataset used in this project is `winequality-red.csv`.

It contains physicochemical properties of red wine samples, such as:

- fixed acidity
- volatile acidity
- citric acid
- residual sugar
- chlorides
- free sulfur dioxide
- total sulfur dioxide
- density
- pH
- sulphates
- alcohol

The target variable is `quality`, which represents the wine quality score.

## Libraries Used

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

## Workflow

### 1. Load and Inspect Data

The dataset is loaded using pandas, and basic inspection is performed:

- `head()`
- `isnull().sum()`
- `info()`

### 2. Feature Scaling

The features are processed in two steps:

- `StandardScaler` for standardization
- `MinMaxScaler` for normalization

This helps prepare the data for clustering and classification models.

### 3. Correlation Analysis

A heatmap is used to visualize correlations between all numeric variables in the dataset. This helps identify relationships between features and the target variable.

### 4. Manual Feature Selection

A few important features are selected manually:

- `alcohol`
- `sulphates`
- `citric acid`

### 5. K-Means Clustering

The elbow method is used to find a suitable number of clusters. Then K-Means is applied to the normalized data.

The cluster labels are added to the dataset and visualized using a scatter plot.

### 6. Classification Models

The generated cluster labels are used as target classes for classification.

Two models are trained and evaluated:

- K-Nearest Neighbors (KNN)
- Decision Tree

Their accuracies are compared.

### 7. Decision Tree Visualization

The trained Decision Tree is visualized using `plot_tree()` to show how the model splits the data.

### 8. Genetic Algorithm for Feature Selection

A Genetic Algorithm is used to select the best features for a regression task.

- The target is `quality`
- The model used in the fitness function is `LinearRegression`
- Cross-validation with `r2` score is used to evaluate each feature subset

The selected features are then used again for classification.

### 9. Model Comparison Before and After GA

KNN and Decision Tree are retrained using the features selected by the Genetic Algorithm.

A comparison table is printed to show model performance before and after feature selection.

## Results

The project provides:

- cluster visualization
- model accuracy comparison
- feature selection results
- performance comparison after GA

## Conclusion

This project demonstrates a complete machine learning workflow on the red wine quality dataset. It combines preprocessing, clustering, classification, and evolutionary feature selection to analyze the data and compare model performance.

## How to Run

1. Place `winequality-red.csv` in the same folder as the script
2. Install required packages:
```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   

