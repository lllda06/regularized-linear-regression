# Regularized Linear Regression — House Price Prediction

## Project Overview

This project focuses on predicting house sale prices using regularized linear regression models.

The project demonstrates a complete machine learning workflow, including exploratory data analysis, feature engineering, data preprocessing, model training, regularization, hyperparameter selection, and model evaluation.

Two regularization techniques were investigated:

* **Lasso Regression (L1 regularization)**
* **Ridge Regression (L2 regularization)**

## Dataset

The dataset contains information about residential properties and their sale prices.

The target variable is:

* `SalePrice` — house sale price in USD.

The dataset includes numerical and categorical features such as:

* `LotArea`
* `OverallQual`
* `OverallCond`
* `YearBuilt`
* `YearRemodAdd`
* `TotalBsmtSF`
* `GrLivArea`
* `Bath`
* `KitchenQual`
* `GarageArea`
* `DateSold`
* `SaleCondition`

Additional features were created during the analysis, including:

* `HouseAge`
* `YearsSinceRemod`
* `TotalLivingArea`

## Project Workflow

### 1. Exploratory Data Analysis

The dataset was analyzed to understand its structure, distributions, missing values, and relationships between features and the target variable.

A correlation matrix was created for numerical features, and linearly dependent features were removed.

Individual plots were also used to analyze the relationships between `SalePrice` and numerical features.

### 2. Feature Engineering

Additional features were created from existing variables.

For example:

* `HouseAge` represents the age of the house.
* `YearsSinceRemod` represents the number of years since the last renovation.
* `TotalLivingArea` represents the total available living space.

These features provide more meaningful representations of the original data and can help the models capture relevant relationships.

### 3. Data Preprocessing

The dataset was split into training and test sets.

Categorical features were encoded, while numerical features were scaled to a common range before being passed to the models.

### 4. Model Training

Three approaches were evaluated:

* Linear Regression without regularization
* Lasso Regression with L1 regularization
* Ridge Regression with L2 regularization

The regularization parameter `α` was selected by comparing model performance on the test set.

### 5. Model Evaluation

The models were evaluated using:

* **MAE (Mean Absolute Error)**
* **MSE (Mean Squared Error)**
* **R² (R-squared)**

Training and test performance were compared to assess the model's generalization and detect potential overfitting.

## Results

| Model             |   Test R² |
| ----------------- | --------: |
| Linear Regression |     0.624 |
| Lasso             |     0.687 |
| **Ridge**         | **0.717** |

### Lasso Regression

The best regularization parameter was:

**α = 1000**

Test set performance:

* MAE: **21,387.12**
* MSE: **1,674,428,799.05**
* R²: **0.6873**

Lasso reduced the number of active features by setting **102 out of 119 coefficients to zero**, leaving 17 non-zero coefficients. This demonstrates the feature selection capability of L1 regularization.

### Ridge Regression

The best regularization parameter was:

**α = 1000**

Test set performance:

* MAE: **21,986.38**
* MSE: **1,513,299,698.95**
* R²: **0.7174**

Unlike Lasso, Ridge kept all 119 coefficients non-zero while reducing their magnitudes.

## Feature Analysis

The coefficients of the trained models were analyzed to understand the relationships learned by the model.

The three features with the largest positive coefficients were:

* `TotalLivingArea`
* `GrLivArea`
* `OverallQual`

The three features with the largest negative coefficients were:

* `HouseAge`
* `ExterQual_TA`
* `KitchenQual_TA`

The coefficients represent relationships learned by the model and should not automatically be interpreted as causal effects.

## Technologies

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook

## Project Structure

```text
regularized-linear-regression/
│
├── data/
│   └── dataset.csv
│
├── notebooks/
│   └── regularized_linear_regression.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

## Conclusion

The project demonstrates how regularization can improve the generalization of linear regression models for house price prediction.

Among the evaluated models, **Ridge Regression achieved the best test performance with an R² score of 0.7174**.

Lasso also demonstrated an important advantage by automatically selecting relevant features and removing less informative ones through zero-valued coefficients.
