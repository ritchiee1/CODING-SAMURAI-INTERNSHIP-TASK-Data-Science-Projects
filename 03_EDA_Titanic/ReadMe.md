# Titanic Dataset Exploratory Data Analysis (EDA) Project

A Python project analyzing the Titanic dataset to uncover patterns and insights into passenger survival.  

## Table of Contents
1. [Project Scope](#project-scope)  
2. [Project Objectives](#project-objectives)  
3. [Expected Outcome](#expected-outcome)  
4. [Document Purpose](#document-purpose)  
5. [Use Case](#use-case)  
6. [Data Source](#data-source)  
7. [Data Cleaning and Processing](#data-cleaning-and-processing)  
8. [Data Analysis](#data-analysis)  
9. [Data Visualization](#data-visualization)  
10. [Insights](#insights)  
11. [Conclusion](#conclusion)  

---

## Project Scope
This project involves performing exploratory data analysis (EDA) on the Titanic dataset to identify survival patterns. The analysis focuses on cleaning data, handling missing values and outliers, examining distributions, and visualizing relationships among variables.  

---

## Project Objectives
- Perform data cleaning (handling missing values, irrelevant features, and outliers).  
- Explore distributions of numerical and categorical features.  
- Examine relationships between passenger characteristics and survival.  
- Generate a correlation matrix to evaluate feature relationships.  
- Provide insights that can support predictive modeling tasks.  

---

## Expected Outcome
The analysis is expected to highlight:  
- Which factors influenced survival the most (e.g., gender, class, age).  
- The effect of socioeconomic status on survival chances.  
- Key correlations among passenger features.  

---

## Document Purpose
This document serves as a guide to the Titanic EDA project, outlining its scope, methodology, and findings. It provides both technical and non-technical readers with clear insights from the dataset.  

---

## Use Case
The insights derived from this project can be used for:  
- Building predictive models (e.g., classification of survival).  
- Understanding historical survival factors on the Titanic.  
- Demonstrating exploratory data analysis skills in a real-world dataset.  

---

## Data Source
The dataset was obtained from the **Kaggle Titanic - Machine Learning from Disaster competition**, which contains passenger details such as Age, Sex, Fare, Passenger Class, Number of Siblings/Spouses, and Survival status.  

---

## Data Cleaning and Processing
### Handling Missing Values:
- `Age`: Imputed with median values.  
- `Embarked`: Imputed with the most frequent value.  
- `Cabin`: Dropped due to excessive missing values.  

### Handling Outliers:
- Detected extreme outliers in `Fare` using boxplots.  
- Outliers were capped at the 99th percentile to reduce skewness.  

---

## Data Analysis
The analysis was conducted using **Pandas, NumPy, Matplotlib, and Seaborn**.  
It included both univariate and bivariate analyses, as well as multivariate correlation.  

---

## Data Visualization
Several visualizations were created:  

### 1. Univariate Analysis
- **Histograms** for numerical columns (`Age`, `Fare`, `SibSp`, `Parch`) showed passenger distributions.  
- **Countplots** for categorical columns (`Sex`, `Embarked`, `Pclass`, `Survived`) displayed frequency counts.  
- Outliers in `Fare` were visualized using a **boxplot**.  

### 2. Bivariate Analysis
- **Survival by Sex**: Women had higher survival rates than men.  
- **Survival by Pclass**: First-class passengers had the highest survival rate, third-class the lowest.  
- **Survival by Embarked**: Passengers embarking at 'C' (Cherbourg) had better survival chances.  
- **Age vs Survival**: Younger passengers had slightly higher chances of survival.  
- **Fare vs Survival**: Higher fare correlated with higher survival probability.  

### 3. Multivariate Analysis
- **Correlation Heatmap** revealed:  
  - Strong negative correlation between `Pclass` and `Fare`.  
  - Positive correlation between `Fare` and `Survived`.  
  - Weak correlation between `Age` and `Survived`.  

---

## Insights
- **Gender**: Survival was heavily influenced by gender, with females more likely to survive.  
- **Class**: Socioeconomic status (Pclass) significantly affected survival, favoring higher-class passengers.  
- **Age**: Children had a slightly higher survival rate, though the relationship was weaker.  
- **Fare**: Passengers who paid higher fares had higher chances of survival.  
- **Embarked**: Port of embarkation had some effect, with 'C' showing the best survival outcomes.  

---

## Conclusion
The Titanic dataset reveals that **gender and passenger class were the strongest indicators of survival**. Women and wealthier passengers had better chances, while men in lower classes faced the lowest survival rates.  
This exploratory data analysis sets the foundation for future **feature engineering and predictive modeling**.  

---

## Author
**Jetevu Richard**  

## Link  
🔗 [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic)  