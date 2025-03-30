# Airbnb Superhost Prediction Project
References: https://www.kaggle.com/datasets/thedevastator/berlin-airbnb-ratings-how-hosts-
measure-up

## Project Overview: Understanding the Basics and Goals

### What are we trying to find out?
The main research question is:  
**Can we predict whether a host will be a Superhost based on available Airbnb listing data?**

### What do we already know?
Airbnb provides a variety of features related to host performance, listing characteristics, location, and user ratings. Some of these features are known to influence the likelihood of a host becoming a Superhost (e.g., response rate, number of reviews, ratings).

### What are we aiming to achieve?
The aim is to build a machine learning model that can accurately classify whether a host is a Superhost based on relevant features.  
Success is defined as achieving a reasonable accuracy while maintaining generalizability and avoiding overfitting.

### What factors affect our results?
Variables such as rating scores, engagement metrics, and historical review activity are among the strongest predictors. However, features like `Overall Rating` and `Total Ratings Score` were found to be overly dominant, and were intentionally excluded in some model versions to evaluate performance fairly. 

### Is there something new we can use?
I combined traditional feature selection techniques with model-based feature importance, and iteratively refined the feature set to avoid information leakage, as can be seen in the project notebook. I also experimented with several classification algorithms, including Random Forest, AdaBoost, and XGBoost to ensure the best results.



## Project Workflow Summary

### 1. Data Preparation
- Merged multiple sources into one DataFrame
- Reduced large categorical variables
- Cleaned and standardized textual and numeric data
- Transformed and normalized features using `StandardScaler` (`Price`, `Engagemnt level`)

### 2. Exploratory Data Analysis (EDA)
- Visualized distributions and trends using histograms and bar plots(as can be seen in the notebook)
- Analyzed correlations with the target variable `Is Superhost`
- Identified highly correlated features for potential removal

### 3. Data Cleansing
- Handled outliers (though i kept them initially to test model sensitivity)
- Filled missing values using median/mode/mean depending on context

### 4. One-Hot Encoding
- Categorical variables were transformed using `get_dummies()` where needed

### 5. Feature Engineering & Selection
- Created new features (e.g., `Host Years`, `Days Since Review`)
- Normalized selected numeric features
- Performed correlation filtering and removed features with correlation > 0.2
- Manually removed features with overly high predictive power to avoid overfitting

### 6. Handling Imbalanced Data
- Class balance was monitored during evaluation. Due to mild imbalance, no oversampling was applied.

### 7. Model Selection and Fine Tuning
- Compared several classification models: Logistic Regression, Decision Tree, Random Forest, AdaBoost, Gradient Boosting, and XGBoost
- Used separate Validation and Test sets (60%-20%-20%) for reliable model evaluation
- Performed feature-based simplification rather than extensive hyperparameter tuning to avoid overfitting

---

## Project Summary: Deployment and Beneficiaries

### How will we deploy the Machine Learning?
The model can be integrated into an Airbnb-like platform to help identify promising hosts who are likely to become Superhosts. It can also assist in onboarding, training, or rewarding hosts based on predictions.

### Who will use and benefit from the Machine Learning?
- **Platform Administrators:** Can use predictions to guide Superhost verification processes
- **Hosts:** May receive insights on how to improve their chances of becoming Superhosts
- **Guests:** Indirectly benefit from improved host quality and experiences

---

> **Note:** During experimentation,I encountered consistent results with extremely high accuracy (e.g., 99%+). After several tests — removing highly predictive features, reducing correlation thresholds, and evaluating across multiple models — it is possible concluded that the dataset enables highly reliable predictions due to clear patterns in the features. Therefore, the strong results are not a result of data leakage or error, but rather the nature of the data itself.


