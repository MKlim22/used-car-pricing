# Used Car Price Analysis

## Project overview
This project focuses on analyzing factors that influence used car prices using Python.
The goal is to explore relationships between vehicle features (such as engine size, horsepower, body style, and drivetrain) and car prices through data cleaning, exploratory data analysis (EDA), and visualization, and predictive modeling.

The dataset comes from the IBM skills Network and contains technical specifications and prices of used cars.

---

## Dataset
- Source: IBM Skills Network
- Rows: 205
- Columns: 26
- Target variable: 'price'

## Key features:
- Engine size
- Horsepower
- Curb weight
- Body style
- Drive wheels
- Fuel efficiency (city & highway MPG)

---

## Tools & Libraries
- Python
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- Jupyter Notebook

---

## Data Cleaning
The following steps were performed:
- Replaced `"?"` values with `NaN`
- Converted selected columns to numeric types
- Removed rows with missing `price`
- Filled missing values:
    - Median for `normalized-looses`
    - Mean for numerical features (`bore`, `stroke`, `horsepower`, `peak-rpm`)
    - Mode for `num-of-doors`
- Verified data types and missing values after cleaning

---

## Exploratory Data Analysis (EDA)

### Correlation Analysis
A correlation matrix was created to identify variables most strongly related to price.

Top positive correlations with price:
- Engine size
- Curb weight
- Horsepower
- Vehicle width

Negative correlations:
- City MPG
- Highway MPG

---

## Visualizations

### Engine size vs Price
A strong positive linear relationship indicates that cars with larger engines tend to be more expensive.

### Horsepower vs Price
Higher horsepower is generally associated with higher vehicle prices.

### Price vs Drive Wheels
Rear-wheel drive cars tent to have a higher median price compared to front-wheel drive vehicles.

### Price vs Body Style
Convertibles and hardtops generally show higher prices, while hatchbacks and wagons are typically more affordable.

---

## Key Insights
- Engine size and horsepower are strong predictors of car price
- Heavier and wider cars tend to be more expensive
- Fuel-efficient cars usually have lower price
- Drivetrain and body style have a noticeable impact on pricing

---

## Model Development

The modeling phase focused on predicting car prices using both numerical and categorical features.

## Data Preparation
- Target variable: `price`
- Removed rows with missing target values
- Train-test split:
    - 80% training set
    - 20% test set
- Automatic separation of:
    - Numerical features
    - Categorical features


### Preprocessing Pipeline
A unified preprocessing pipeline was built using `ColumnTransformer`.

**Numerical features:**
- Median imputation for missing values
- Standarization using `StandardScaler`

**Categorical features:**
- Most frequent value imputation
- One-hot encoding (`handle_unknown="ignore"`)

The same preprocessing steps were applied consistently across all models.

---

## Models Evaluated
The following regression models were trained and compared:
- Linear Regression
- Ridge Regression (L2 regularization)
- Lasso Regression (L1 regularization)
- Random Forest Regressor

Each model was combined with the preprocessing pipeline using `Pipeline`.

---

## Model Evaluation
Models were evaluate using:
- R² score
- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)

Evaluation was performed on:
- Training set
- Test set
- 5-fold cross-validation

### Test Set Performance (summary)
- **Random Forest** achieved the highest R² and lowest RMSE
- Regularized linear models (Ridge, Lasso) performed better than plain Linear Regression
- Random Forest showed the best overall generalization performance

---

## Cross-Validation
5-fold cross-validation was used to assess model stability.

Random Forest:
- Highest mean CV R²
- Lowest mean CV RMSE
- Relatively low variance across folds

Based on cross-validation results, **Random Forest** was selected as the final model.

---

## Final Model Performance
**Best model:** Random Forest Regressor  

Final evaluation on the test set:
- R² ≈ 0.93  
- RMSE ≈ 2978  
- MAE ≈ 1889  

This indicates strong predictive performance with a relatively low average prediction error.

---

## Diagnostic Analysis
- **Predicted vs Actual plot** shows good alignment along the diagonal
- **Residual plot** shows no strong systematic patterns
- Slightly higher variance is visible for higher-priced vehicles

Overall, residuals suggest a well-fitted model.

---

## Feature Importance (Random Forest)
Feature importance analysis revealed that the most influential features were:
- Engine size
- Horsepower
- Curb weight
- Vehicle width
- Fuel efficiency (MPG)

These results are consistent with insights from EDA.

---

## Model Persistence
The final trained pipeline was saved using `joblib`, allowing the model to be reused for future predictions without retraining.

## How to run
1. Clone the repository
2. Open `used_cars_analysis.ipynb` in Jupyter Notebook
3. Run all cells sequentially

## Future improvements
- Hyperparameter turning for the Random Forest model
- Testing additional ensemble models (e.g. Gradient Boosting)
- Feature engineering (interaction terms, binning)
- Expanding the dataset to improve generalization