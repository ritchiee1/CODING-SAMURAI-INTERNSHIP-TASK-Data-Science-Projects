# Titanic Dataset Exploratory Data Analysis (EDA) & Survival Prediction

A Python project analyzing the Titanic dataset to uncover patterns and build a predictive model for passenger survival using **Logistic Regression**. The pipeline includes EDA, data cleaning, feature engineering, wrapper-based feature selection (RFE), model training, and evaluation.

---

## Table of Contents
1. [Project Scope](#project-scope)  
2. [Project Objectives](#project-objectives)  
3. [Expected Outcome](#expected-outcome)  
4. [Document Purpose](#document-purpose)  
5. [Use Case](#use-case)  
6. [Data Source](#data-source)  
7. [Data Cleaning and Processing](#data-cleaning-and-processing)  
8. [Data Analysis & Feature Engineering](#data-analysis--feature-engineering)  
9. [Feature Selection](#feature-selection)  
10. [Model Building & Evaluation](#model-building--evaluation)  
11. [Results (Confusion Matrix & Classification Report)](#results-confusion-matrix--classification-report)  
12. [Insights](#insights)  
13. [Conclusion](#conclusion)  
14. [Author](#author)

---

## Project Scope
Perform EDA on the Titanic dataset and build a reproducible classification pipeline to predict passenger survival. The project focuses on practical preprocessing, a compact engineered feature set, and an interpretable baseline model.

---

## Project Objectives
- Clean the dataset and handle missing values and outliers.  
- Engineer informative features (Title from `Name`).  
- Encode categorical variables and scale numeric variables.  
- Use wrapper-based feature selection (RFE) to select a compact feature set.  
- Train and evaluate a Logistic Regression model and report results.

---

## Expected Outcome
- Identify features most predictive of survival.  
- Produce a trained, evaluated model with clear performance metrics.  
- Provide actionable insights and future directions for model improvement.

---

## Document Purpose
This README documents the methods, results, and insights from the Titanic EDA and prediction pipeline for technical review and portfolio presentation.

---

## Use Case
- Demonstrates end-to-end ML workflow for classification problems.  
- Provides interpretable baseline suitable for educational and interview contexts.  
- Can be extended for deployment (Streamlit/Flask) or benchmarking against other models.

---

## Data Source
- **Kaggle:** Titanic — Machine Learning from Disaster.  
- Link: https://www.kaggle.com/c/titanic

---

## Data Cleaning and Processing
- **Initial data shape:** 891 rows, 11 columns (PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Embarked).  
- **Missing values handling:**  
  - `Age` → imputed with **median**.  
  - `Embarked` → imputed with **mode** (most frequent).  
  - `Cabin` → dropped due to excessive missingness.  
- **Irrelevant features removed:** `PassengerId`, `Name`, `Ticket` (after feature extraction).  
- **Outliers:** `Fare` outliers capped using IQR-based winsorization.  
- **Scaling:** `Age` and `Fare` standardized using `StandardScaler`.

---

## Data Analysis & Feature Engineering
### EDA Insights
- **Gender:** Women had a higher survival rate than men.  
- **Pclass:** 1st class passengers had higher survival than 3rd class.  
- **Age:** Younger passengers had slightly higher survival chances.  
- **Fare:** Higher fares associated with greater survival probability.  
- **Missing Values:** `Age` imputed with median, `Embarked` with mode, `Cabin` dropped.

### Feature Engineering
- **Title extraction** from `Name` into categories: `Mr`, `Mrs`, `Miss`, `Master`, `Rare`.  
  - `Mlle`/`Ms` → `Miss`, `Mme` → `Mrs`, rare titles grouped into `Rare`.  
- `Pclass` and `Title` converted to categorical prior to encoding.  
- **Encoding:**  
  - Ordinal encoding used for `Pclass`, `Sex`, `Embarked`.  
  - One-hot encoding for `Title` → `Title_Mr`, `Title_Mrs`, `Title_Miss`, `Title_Master`, `Title_Rare`.

---

## Feature Selection
- **Method:** Recursive Feature Elimination (RFE) with Logistic Regression (estimator `max_iter=1000`).  
- **RFE (n_features_to_select=9) selected features:**  
## Model Training
- **Model:** Logistic Regression (scikit-learn).  
- **Train/Test split:** 80% train, 20% test (`random_state=29`).  
- Model trained on the RFE-selected feature set.

---

## Model Evaluation & Results

### Accuracy (Test)
- **Test Accuracy:** **83.24%**

### Confusion Matrix (Test)
Computed with `confusion_matrix(y_test, y_pred)`:

|               | Predicted No (0) | Predicted Yes (1) |
|---------------|------------------:|------------------:|
| **Actual No** |               103 |                17 |
| **Actual Yes**|                13 |                46 |

- **Interpretation:**  
- True Negatives (TN) = 103  
- False Positives (FP) = 17  
- False Negatives (FN) = 13  
- True Positives (TP) = 46

### Classification Report (Test)
Computed with `classification_report(y_test, y_pred)`:

| Class | Precision | Recall | F1-Score | Support |
|-------:|---------:|-------:|---------:|--------:|
| 0 (Did Not Survive) | 0.89 | 0.86 | 0.87 | 120 |
| 1 (Survived)        | 0.73 | 0.78 | 0.75 | 59  |
| **Accuracy**        |      |      | **0.83** | 179 |
| **Macro Avg**       | 0.81 | 0.82 | 0.81 | 179 |
| **Weighted Avg**    | 0.84 | 0.83 | 0.83 | 179 |

- **Notes:** The model is stronger at predicting non-survivors (class 0) with higher precision; recall for survivors (class 1) is acceptable but can be improved if minimizing FN is critical.

---

## Feature Importance (Interpretation)
- RFE retained features that provided the strongest discriminatory signal for a linear classifier.  
- **High-impact features:**
- `Sex` — largest predictive factor; women more likely to survive.  
- `Pclass` & `Fare` — socio-economic indicators positively correlated with survival.  
- `Title_*` — captures social status and age-related cues beyond raw `Name`.  
- `SibSp`, `Parch` — family/group effects influencing survival probability.

---

## Final Insights & Key Observations
- A compact nine-feature model yields **83.24%** accuracy with strong interpretability.  
- **Title** extraction meaningfully improved separability for the linear model.  
- Logistic Regression produced balanced performance and is an effective, explainable baseline.  
- Error profile: more confident and precise in predicting non-survivors; some survivors were missed (FN = 13).

---

## Future Work & Recommendations
- **Model benchmarking:** Evaluate tree-based ensembles (Random Forest, XGBoost, LightGBM) on the same selected features.  
- **Hyperparameter tuning:** Use `GridSearchCV`/`RandomizedSearchCV` for `C`, penalty, solvers.  
- **Threshold tuning / class weights:** If recall for survivors is prioritized, adjust decision threshold or class weights.  
- **Cross-validation:** Use stratified k-fold CV to verify stability of the 83.24% result.  
- **Calibration & ROC-AUC:** Add ROC curves, AUC, and calibration plots for probability assessment.  
- **Deployment:** Build a simple Streamlit/Flask app and persist the trained model with `joblib` for demo and interaction.  
- **Experiment tracking:** Use MLflow or W&B to log runs and parameters.


