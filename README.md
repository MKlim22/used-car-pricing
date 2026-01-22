# Used Car Price Analysis

## Project overview
This project focuses on analyzing factors that influence used car prices using Python.
The goal is to explore relationships between vehicle features (such as engine size, horsepower, body style, and drivetrain) and car prices through data cleaning, exploratory data analysis (EDA), and visualization.

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

## How to Run
1. Clone the repository
2. Open `used_cars_analysis.ipynb` in Jupyter Notebook
3. Run all cells sequentially

---

## Future Improvements
- Build a linear regression model for price prediction
- Feature scaling and encoding categorical variables
- Compare multiple regression models