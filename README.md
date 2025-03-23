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

- **`K_Means_Clustering.py`**: The main Python script that implements the clustering pipeline using PySpark.
- **`seeds_dataset.csv`**: The dataset file containing measurements of wheat kernels.
- **`image.png`**: (Optional) An image of the mind map illustrating the clustering process.

## Clustering Process Mind Map

Data Ingestion ├── Load data from source (CSV, Parquet, etc.) └── Verify schema and data types

Exploratory Data Analysis (EDA) ├── Inspect basic statistics (describe, summary) ├── Check for missing/invalid values └── Visualize distributions

Data Preprocessing ├── Handle missing or invalid values (drop, impute, etc.) └── Feature engineering or transformation

Feature Selection ├── Identify relevant columns for clustering └── Drop unnecessary columns

Vectorization └── Use VectorAssembler to combine features into a single vector column ("features")

Feature Scaling └── Use StandardScaler to normalize features (output: "scaledFeatures")

Model Selection / Hyperparameter Tuning ├── Decide on number of clusters (k) │ ├── Use Silhouette Score or Elbow Method │ └── Evaluate different k values └── Choose best k based on evaluation metric

Train K-Means Model ├── Instantiate K-Means with chosen k └── Fit on scaled features

Generate Predictions ├── Use model.transform() to get cluster assignments └── Inspect or save predictions

Evaluation & Visualization ├── Evaluate cluster quality (e.g., Silhouette Score) ├── (Optional) Visualize clusters (2D/3D using PCA) └── Interpret cluster centers

Deployment / Next Steps ├── Persist the model for production use ├── Integrate into data pipelines └── Communicate results and finding


## How to Run

1. **Prerequisites:**
   - Apache Spark (with PySpark installed)
   - Python 3.x
   - Required libraries: `pyspark`, `matplotlib`

2. **Setup:**
   - Place `seeds_dataset.csv` in the `Data/` directory as referenced in the code.
   - Ensure all dependencies are installed.

3. **Execution:**
   - Run the clustering script using the following command:
     ```bash
     spark-submit K_Means_Clustering.py
     ```
   - The script will load the data, process it, and print the cluster centers. It will also display a plot of the silhouette scores to help you determine the optimal number of clusters.

## Contributing

Contributions, bug reports, and suggestions are welcome! Please open an issue or submit a pull request to contribute to this project.

## License

[Include your license information here.]

## Acknowledgments

- **UCI Machine Learning Repository** for providing the Seeds dataset.
- **PySpark Documentation** and the community for excellent resources and examples.

