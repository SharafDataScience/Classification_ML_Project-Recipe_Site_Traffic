#  Recipe Site Traffic Prediction

This project is part of a practical data science challenge to help Tasty Bytes, a recipe and meal planning platform, optimize homepage content by predicting which recipes will drive **high user traffic**. The goal is to recommend popular recipes for the homepage based on nutritional and categorical features of each recipe.

---

##  Project Overview

The **business objective** is to increase user engagement and subscriptions by correctly selecting popular recipes to feature. Specifically, we aim to:

- **Predict whether a recipe will result in high traffic**
- Achieve at least **80% accuracy** for predicting high-traffic recipes
- Provide **actionable insights** and a **metric** the business can monitor moving forward

---

##  Data Description

The dataset contains the following fields:

| Column        | Description                                                |
|---------------|------------------------------------------------------------|
| `recipe`      | Unique recipe identifier                                   |
| `calories`    | Number of calories per serving                             |
| `carbohydrate`| Grams of carbohydrate per serving                          |
| `sugar`       | Grams of sugar per serving                                 |
| `protein`     | Grams of protein per serving                               |
| `category`    | Recipe type/category (e.g. Dessert, Meat, Breakfast, etc.) |
| `servings`    | Number of servings produced by the recipe                  |
| `high_traffic`| Whether the recipe led to high traffic on the site ("High")|

---

##  Methodology

###  Data Cleaning & Validation
- Checked for missing or inconsistent values
- Converted categorical variables to appropriate formats
- Validated data ranges for nutritional content

### Exploratory Data Analysis (EDA)
- Visualized distribution of traffic vs recipe features
- Analyzed feature relationships using boxplots, histograms, and bar charts

###  Modeling
- **Baseline model**: Logistic Regression
- **Comparison model**: Random Forest Classifier
- Used stratified train-test splits and cross-validation
- Evaluated with Accuracy, Precision, Recall, and F1-Score

###  Business Metric
- Defined a success metric to monitor prediction accuracy
- Calculated estimated current accuracy on historical data

---

##  Key Findings

- Certain recipe categories (e.g. Desserts, One Dish Meals) are more likely to trigger high traffic
- Nutritional features like sugar and protein content show patterns linked to popularity
- The Random Forest model outperformed the baseline, with accuracy close to the 80% target

---






