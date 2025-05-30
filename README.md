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

### Final Result

- Logistic Regression outperformed all other models, achieving the highest accuracy (0.822), precision (0.856), recall (0.856), F1 score (0.856), and ROC AUC score (0.862). While the Decision Tree model showed the same performance notable improvement after hyperparameter tuning, it still fell short of Logistic Regression, particularly in ROC AUC score 0.86 to 0.81. The Support Vector Classifier, despite some tuning, delivered good performance but did not surpass Logistic Regression in any key metric, highlighting Logistic Regression's overall superiority in this analysis.
- Visualizations revealed significant differences in recipe categories between high-traffic and other recipes.

- High-traffic recipes favored categories like Potato , Beverages , and Pork , while lower-traffic recipes leaned toward Breakfast , Chicken , and Dessert .

- Nutritional attributes (calories, carbohydrates, sugar, protein) showed weak correlations with traffic levels, indicating that these factors alone are not strong predictors of popularity.

### Dataset & Tools
- Dataset: Provided in the project files recipe_site_traffic_2212.csv  (From DataCamp)
https://www.datacamp.com/datalab/w/4debb5b1-b296-4e33-9b57-200d764adc48/edit?search=recipe_site_traffic_2212.csv
- Tools/Technologies: Python, Pandas, Seaborn, Matplotlib, Scikit-learn, Jupyter Notebook





