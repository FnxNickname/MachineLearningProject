# Network Intrusion Detection - Machine Learning Project

## Overview
This repository contains a machine learning pipeline designed for **Network Intrusion Detection**. The project utilizes network traffic data, drawing from established intrusion datasets like KDD99 or NSL-KDD, to classify network connections as either 'Normal' or as one of four specific attack types: DoS, Probe, R2L, and U2R.

## Repository Contents
* **`KDDTrain+.txt`**: The training dataset used for model training and resampling.
* **`KDDTest+.txt`**: The testing dataset used to evaluate model generalization on unseen data.
* **`ML.ipynb`**: The Jupyter Notebook containing the full data science pipeline, from exploratory data analysis to model evaluation.
* **`ML video.mp4`**: A video presentation summarizing the business case, dataset, implemented models, and final results.

## Methodology
In accordance with the project guidelines, this pipeline progresses from standard implementations to advanced optimizations:

* **Data Preprocessing**: Includes mapping specific attack labels to their broader attack classes, dropping irrelevant features, one-hot encoding categorical variables, and standardizing numerical features using `StandardScaler`. Outliers identified via Z-scores were intentionally retained as they frequently represent valid network attack signatures.
* **Handling Imbalance**: Applied the Synthetic Minority Over-sampling Technique (SMOTE) exclusively on the training set to prevent bias toward the majority classes.
* **Dimensionality Reduction**: Utilized Principal Component Analysis (PCA) to visualize and identify the number of components required to retain 95% of the data's variance.
* **Standard Models**: Evaluated baseline algorithms seen in class, including Logistic Regression and Decision Trees.
* **Advanced Models**: Implemented and optimized Random Forest and XGBoost classifiers. Hyperparameters for the Random Forest were tuned using `RandomizedSearchCV`.
* **Ensemble Learning**: Constructed a Soft Voting Classifier that combines the predictive power of the tuned Random Forest and XGBoost to improve overall decision-making.

## Results & Evaluation
The models were evaluated on the original, unaltered test data to accurately reflect real-world intrusion detection performance. Evaluation metrics included Accuracy and Weighted F1-Score.

| Model | Test Accuracy | F1-Score |
|---|---|---|
| XGBoost | 0.7711 | 0.7322 |
| Voting Ensemble | 0.7703 | 0.7309 |
| Decision Tree | 0.7641 | 0.7248 |
| Logistic Regression | 0.7636 | 0.7224 |
| Random Forest (Tuned) | 0.7613 | 0.7201 |

**Conclusion**: Tree-based ensemble methods (XGBoost) and Voting Classifiers demonstrate the strongest performance for detecting network intrusions, providing a better balance of precision and recall across various attack types compared to simpler linear models.

---
*Completed as part of the Machine Learning Personal Project (Groups of 2 students).*
