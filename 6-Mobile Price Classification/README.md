# Mobile Price Classification Project: Clustering, Classification, and Genetic Algorithm Feature Selection

## Project Overview

This project conducts a comprehensive analysis of the "Mobile Price Classification.csv" dataset, focusing on clustering and classification tasks. Additionally, it employs a Genetic Algorithm (GA) for feature selection to optimize a Linear Regression model's performance.

## 1. Introduction and Objectives

The primary goal of this project is to gain a deeper understanding of mobile phone specification data. Key objectives include:

*   **Clustering:** Grouping mobile phones into distinct clusters based on their features (e.g., by price range or quality tier).
*   **Classification:** Training models to predict the cluster assignment for each mobile phone.
*   **GA Feature Selection:** Utilizing a Genetic Algorithm to identify an optimal subset of features to enhance the performance of a Linear Regression model (based on the R-squared metric).
*   **Evaluating GA Impact:** Comparing the performance of classification models (KNN and Decision Tree) before and after applying GA-selected features.

## 2. Dataset

*   **Name:** `Mobile Price Classification.csv`
*   **Description:** This dataset contains information about various mobile phone specifications such as RAM, internal memory, camera resolution, battery, processor, and more. It also includes the `price_range` column, indicating the price tier of the mobile phone (0, 1, 2, 3).

## 3. Tools and Libraries

*   **Programming Language:** Python
*   **Libraries:**
    *   `pandas`: For data loading, manipulation, and analysis.
    *   `numpy`: For numerical computations.
    *   `seaborn` & `matplotlib`: For data visualization (e.g., Heatmap, Scatter Plot).
    *   `scikit-learn`: Includes tools for data preprocessing (Scaling), clustering (KMeans), classification models (KNeighborsClassifier, DecisionTreeClassifier), feature selection (train_test_split), and model evaluation (accuracy_score, cross_val_score).
    *   `warnings`: For managing and filtering warnings (especially in Windows environments).
    *   `arabic_reshaper` & `python-bidi`: (If needed for correct Persian text rendering in plots) For proper display of Persian characters in Matplotlib.

## 4. Implementation Steps

### 4.1. Environment Setup and Data Preprocessing

*   **Import Libraries:** Import all necessary libraries.
*   **Load Data:** Read the `Mobile Price Classification.csv` file using Pandas.
*   **Handle Warnings:** Set warning filters to suppress unnecessary messages, particularly those related to `KMeans` on Windows.
*   **Prepare Variables:**
    *   Separate the `price_range` column as the target variable (`y`).
    *   Separate the `price_range` column for regression purposes (`y_reg`) if needed (though not used in classification, it's relevant for the GA objective).
*   **Feature Scaling:**
    *   Apply `StandardScaler` to standardize the data.
    *   Apply `MinMaxScaler` to the standardized data to ensure all features are within the [0, 1] range. This step is crucial for algorithms like K-Means and KNN.
*   **Exploratory Data Analysis (EDA):**
    *   Generate a correlation heatmap of the features using `seaborn.heatmap` to understand inter-variable relationships.

### 4.2. Clustering Analysis (K-Means)

*   **Determine Optimal Number of Clusters (Elbow Method):**
    *   Run the K-Means algorithm with varying numbers of clusters (e.g., from 1 to 10).
    *   Calculate the sum of squared distances of samples to their closest cluster center (Inertia) for each cluster count.
    *   Plot Inertia against the number of clusters. The "elbow" point on the plot indicates the optimal number of clusters.
*   **Execute K-Means:**
    *   Using the optimal number of clusters (commonly 3 or 4 for this dataset), run the K-Means algorithm (`n_clusters=3`, `random_state=42`).
    *   Add the resulting cluster labels (one for each sample) as a new column named `cluster` to the original DataFrame.
*   **Visualize Clusters:**
    *   Create a scatter plot of `ram` vs. `battery_power`, coloring points by their assigned cluster, to visually inspect the cluster separation.

### 4.3. Classification Models

*   **Objective:** Train models to predict the cluster labels obtained in the previous step.
*   **Models:**
    *   `KNeighborsClassifier` (with `n_neighbors=5`)
    *   `DecisionTreeClassifier` (with `max_depth=5`)
*   **Training and Evaluation:**
    *   Split the data (scaled features) into training and testing sets (`train_test_split`).
    *   Train both models on the training data.
    *   Calculate and store the accuracy (`knn_acc`, `dt_acc`) of each model on the test set. Initial accuracy is expected to be high (close to 1.0).

### 4.4. Genetic Algorithm (GA) for Feature Selection

*   **Objective:** Find a subset of features that optimizes the performance of a `LinearRegression` model based on the `R2` score.
*   **GA Logic:**
    *   **Chromosome Representation:** Each chromosome is a binary array equal in length to the total number of features. A `1` indicates feature selection, and a `0` indicates deselection.
    *   **Fitness Function:** This function (`fitness`) is calculated for each chromosome:
        *   Extracts features selected by the current chromosome.
        *   Trains a `LinearRegression` model using these features.
        *   Calculates the `R2` score using 5-fold cross-validation (`cross_val_score`).
        *   Returns the average `R2` score as the fitness value.
    *   **Initial Population:** A population of random chromosomes is created.
    *   **Generations Loop:** The algorithm runs for a specified number of generations (e.g., 20). In each generation:
        *   **Evaluation:** Fitness is calculated for each individual in the population.
        *   **Parent Selection:** Individuals with the highest fitness (best performance) are selected as parents for the next generation (e.g., top 10 individuals).
        *   **Offspring Generation (Crossover & Mutation):**
            *   **Crossover:** Two parents are chosen, and their chromosomes are combined using a single-point crossover method to create offspring.
            *   **Mutation:** With a small probability (e.g., 10%), a bit in the offspring's chromosome is flipped (0 to 1 or 1 to 0) to maintain diversity.
        *   **New Population Formation:** The new generation of offspring replaces the previous population.
*   **Identify Best Features:** After all generations, the best chromosome (with the highest fitness score) is identified, and its corresponding features (`best_chromosome == 1`) are extracted and stored in `ga_features`.

### 4.5. Post-GA Evaluation

*   **Prepare Data with Selected Features:** A new DataFrame (`X_ga`) is created using only the features selected by the GA.
*   **Split Data Again:** The `X_ga` data is split into training and testing sets.
*   **Retrain Models:**
    *   The `KNeighborsClassifier` is retrained using `X_train` (GA features only) and `y_train`.
    *   The `DecisionTreeClassifier` is retrained similarly.
*   **Calculate Accuracy:** The accuracy of both retrained models is calculated on the test set (`X_test`, `y_test`) and stored in `ga_knn_acc` and `ga_dt_acc`.
*   **Compare Results:** The accuracies of the models before and after GA feature selection are presented in a final `results` DataFrame to show the impact of GA-based feature selection on classification performance.

## 5. Results and Analysis

*   **Initial Performance:** The KNN and Decision Tree models achieved high accuracy (near 1.0) in predicting clusters, suggesting strong patterns in the data or potential overfitting.
*   **GA Impact:** After using GA-selected features:
    *   KNN accuracy significantly decreased (e.g., from 1.0 to 0.355).
    *   Decision Tree accuracy also decreased (e.g., from 1.0 to 0.750).
*   **Interpretation of Accuracy Drop:**
    *   **Initial Overfitting:** The accuracy drop indicates that the initial models might have been overfitted to the noise in the full feature set.
    *   **Mismatched GA Objective:** The GA was designed to optimize the R-squared score for Linear Regression, while performance was evaluated based on KNN/DT classification accuracy. The feature subset optimal for linear regression might not be optimal for these classifiers.
    *   **Feature Importance:** This suggests that many of the discarded features might have been important for the classification task, even if not crucial for linear regression.

## 6. Technical Caveats

*   All code segments are provided with English comments and detailed Markdown explanations.
*   `KMeans` warnings were suppressed for clean execution in Windows environments.

## 7. Potential Improvements

*   **Tune GA Parameters:** Experiment with different mutation rates, population sizes, number of generations, and selection/crossover strategies.
*   **Different Fitness Functions:** Define fitness functions that directly evaluate the classification accuracy of the target models (KNN/DT).
*   **Alternative Feature Selection Methods:** Compare with other techniques like RFE, SelectKBest, etc.
*   **Model Hyperparameter Tuning:** Use Grid Search or Randomized Search to fine-tune the KNN and Decision Tree parameters after feature selection.
*   **More In-depth Analysis:** Investigate the impact of each individual feature on the models more thoroughly.

