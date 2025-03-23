# PySpark K-Means Clustering on Seeds Dataset

## Overview

This repository demonstrates a complete end-to-end machine learning pipeline using PySpark for K-Means clustering on the UCI Seeds dataset. The project aims to group wheat kernels into clusters corresponding to three different wheat varieties (Kama, Rosa, and Canadian). The implementation covers the entire workflow—from data ingestion and preprocessing to model training, evaluation, and visualization.

## Features

- **Data Ingestion:** Load and verify data from CSV files.
- **Exploratory Data Analysis (EDA):** Inspect data, check for missing values, and explore basic statistics.
- **Data Preprocessing:** Handle missing/irrelevant data and prepare features.
- **Feature Vectorization:** Combine individual feature columns into a single vector using `VectorAssembler`.
- **Feature Scaling:** Standardize features using `StandardScaler` to improve clustering performance.
- **Model Selection:** Evaluate different numbers of clusters (k) using the Silhouette Score.
- **K-Means Training:** Fit a K-Means model on the scaled data.
- **Evaluation & Visualization:** Examine cluster centers and visualize silhouette scores to validate clustering quality.
- **Mind Map:** A clear visual outline of the clustering process.

## File Structure

- **`K_Means_Clustering.ipynb`**: The main Python notebook that implements the clustering pipeline using PySpark.
- **`seeds_dataset.csv`**: The dataset file containing measurements of wheat kernels.
- **`Clustering_Process.drawio`**: An image of the mind map illustrating the clustering process.

## Clustering Steps

Below is a detailed explanation of each step in the clustering process:

### 1. Data Ingestion
- **Read Data:** Load your CSV (or other data sources) into a Spark DataFrame.
- **Schema Verification:** Ensure the schema (column names and types) is correctly inferred.

### 2. Exploratory Data Analysis (EDA)
- **Data Inspection:** Use commands like `show()`, `describe()`, or `summary()` in Spark to view the data.
- **Data Quality Checks:** Identify outliers, missing values, or abnormal distributions that could affect clustering.

### 3. Data Preprocessing
- **Missing Value Handling:** Address missing values by dropping or imputing them.
- **Feature Engineering:** Apply any domain-specific transformations (e.g., log transformations for skewed data).

### 4. Feature Selection
- **Column Relevance:** Decide which columns are most relevant for clustering.
- **Column Removal:** Exclude columns that are unnecessary or could distort the clustering outcome.

### 5. Vectorization
- **Feature Combination:** Use `VectorAssembler` to combine individual features into a single vector column required by Spark ML.
  - Example: `VectorAssembler(inputCols=[...], outputCol="features")`

### 6. Feature Scaling
- **Normalization:** Scale the feature vectors to manage different scales across features.
- **Scaling Tool:** Use `StandardScaler` (or an alternative) to standardize the data.
  - Example: `StandardScaler(inputCol="features", outputCol="scaledFeatures")`

### 7. Model Selection / Hyperparameter Tuning
- **Choosing k:** Iterate over different values of k using evaluation metrics like the Silhouette Score or Elbow Method.
- **Metric Evaluation:** Select the optimal k value based on the best evaluation metric score.

### 8. Train K-Means Model
- **Model Instantiation:** Create a K-Means model using the chosen number of clusters and the scaled features.
  - Example: `KMeans(featuresCol='scaledFeatures', k=chosen_k)`
- **Model Fitting:** Fit the model on the training (or full) dataset.

### 9. Generate Predictions
- **Cluster Assignment:** Transform the dataset with the trained model to obtain cluster assignments.
- **Prediction Column:** A new column (typically called "prediction") is created to store the cluster index for each data point.

### 10. Evaluation & Visualization
- **Quality Assessment:** Evaluate the quality of clusters using metrics like the Silhouette Score.
- **Visualization (Optional):** Use dimensionality reduction techniques (e.g., PCA) to visualize clusters in 2D or 3D.
- **Interpretation:** Analyze cluster centers to gain insights into the characteristics of each cluster.

### 11. Deployment / Next Steps
- **Model Persistence:** Save and load the trained model for production use if necessary.
- **Result Communication:** Share findings through reports, dashboards, or notebooks.
- **Continuous Improvement:** Optionally re-run or fine-tune the pipeline based on new data or additional analysis.

## How to Run

1. **Prerequisites:**
   - [Conda](https://docs.conda.io/en/latest/) installed on your system
   - Apache Spark with PySpark installed (handled by the Conda environment)
   - Python 3.x

2. **Setup:**
   - Clone the repository and navigate to the project directory.
   - Place `seeds_dataset.csv` in the appropriate directory as referenced in the code.

3. **Execution:**
   - **Create the Conda Environment:**  
     Use the provided `environment.yml` file to create and activate the environment:
     ```bash
     conda env create -f environment.yml
     conda activate k_means_clus_gg
     ```
   - **Run the Clustering Script:**  
     Execute the clustering script with Spark:
     ```bash
     spark-submit K_Means_Clustering.py
     ```
   - The script will load and process the data, train the K-Means model, display the cluster centers, and plot the silhouette scores for model evaluation.


## Contributing

Contributions, bug reports, and suggestions are welcome! Please open an issue or submit a pull request to contribute to this project.

## Acknowledgments

- **UCI Machine Learning Repository** for the Seeds dataset.
- **PySpark Documentation** for the extensive examples and resources.
