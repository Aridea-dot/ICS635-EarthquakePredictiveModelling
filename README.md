# Richter’s Predictor: Modeling Earthquake Damage

[![DrivenData Competition](https://img.shields.io/badge/DrivenData-Nepal%20Earthquake-blue)](https://www.drivendata.org/competitions/57/nepal-earthquake/)  
[![License: MIT](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)

Predicting building damage grades (1 = low, 2 = medium, 3 = high) resulting from the 2015 Gorkha earthquake in Nepal. This repository includes data processing, model training, and hypertuning.

---

## Table of Contents
1. [Competition Overview](#competition-overview)  
2. [Data Description](#data-description)  
3. [Workflow Summary](#workflow-summary)  
4. [Folder Structure](#folder-structure)  
5. [Usage Examples](#usage-examples)  
6. [Submission Format](#submission-format)  
7. [References](#references)  

---

## Competition Overview
- **Title:** Richter’s Predictor: Modeling Earthquake Damage  
- **Host:** DrivenData  
- **Participants:** 8,129 (as of April 2025)  
- **Time Remaining:** 1 year  
- **Problem Statement:** Predict the damage grade of buildings affected by the 2015 Gorkha earthquake based on location and construction features.  
- **Metric:** Micro-averaged F1 score  

---

##  Data Description
- **Train Features:** `data/train_values.csv` — building attributes + geographic IDs  
- **Train Labels:** `data/train_labels.csv` — damage grade (1 / 2 / 3)  
- **Test Features:** `data/test_values.csv` — unlabeled for submission  

> **⚠️ Data Access:** Use the DrivenData CLI/API to download datasets. Do **not** share raw data publicly.

---

## 🛠 Workflow Summary
1. **Preprocessing**  
   - Handle missing values & outliers  
   - Encode categorical variables (e.g., wall type, roof type)  
2. **Feature Engineering**  
   - Create four engineered features:  
     - **Area × Floors**  
     - **Height ÷ Families**  
     - **Distance to District Centroid**  
     - **Soil Softness Proxy** (elevation & slope)  
3. **Modeling**  
   - **Baseline Models:** SVM, LightGBM, Decision Tree, Logistic Regression, RandomForest, AdaBoost  
   - **Deep Learning:** ANN, DNN, CNN (tabular), LSTM, Stacking Ensemble  
   - **Hyperparameter Tuning:** Randomized/Grid Search  


---

## Folder Structure
```plaintext
├── data/                    # Raw & processed data
├── notebooks/               # Jupyter notebooks by stage
│   ├── 01_preprocessing.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_baseline_models.ipynb
│   ├── 04_hyperparameter_tuning.ipynb
│
├── scripts/                 # Python scripts (preprocess.py, etc.)
├── models/                  # Saved model artifacts (.pkl, .h5)
├── submissions/             # Sample submission files
└── README.md                # Project documentation (this file)
