## Data Validation   
 - recipe: 947 unique values, no missing values, numeric (int64), matches the description. No    cleaning needed.
 - calories: 891 unique values, 52 missing values, numeric (float64). Cleaning missing values    is needed.
 - Carbohydrate : 52 missing values, numeric (float64).Because we do not      know the weight    of the serving, we cannot confirm if     these are in grams, but we assume    they are in    grams. Cleaning missing values is needed.
 - Sugar : 52 missing values, numeric (float64). . Because we do not know the weight of          the serving, we cannot confirm if these are in grams, but we assume they are    in grams.    Cleaning missing values is needed
 - Protein : 52 missing values, numeric (float64). Because we do not know    the weight of      the serving, we cannot confirm if these are in grams, but we assume they are    in            grams.Cleaning missing values is needed.
 - category: 11 unique values values should be 10,no missing values,categorical(object      )    ,need cleaning, change    "Chicken Breast" to "Chicken," the values will be 10.
 - servings: 6 unique values should be 4, no missing values, but stored as an object(string).    Needs  conversion to remove string "as a snack" from values then convert to number.
 - high_traffic: Only 1 unique value ("High"), 373 missing values. Needs further inspection—    likely a binary column where missing values imply "Low" traffic and trim spaces.
 - removing duplicate, ouliners, and missing values after treated dataset.
 
## Exploratory Analysis:  
  - Included (Bar Chart and Histogram) two different graphics showing single variables.
  - Includeed (Heatmap) one graphic showing two variables to represent the relationship           between features.
  - Describe your findings
    - From the bar chart, it is evident that recipes categorized as "High Traffic" have            significantly higher traffic values compared to those in the "Other" category. The total      number of high-traffic recipes exceeds that of other categories.
    - The histograms reveal that all recipes, regardless of their traffic category, share          similar distributions for calories, carbohydrates, sugar, and protein content. However,      there are noticeable differences in the distribution of recipe categories between the       "High Traffic" and "Other" groups.
    - The analysis reveals distinct category preferences between high-traffic and other            recipes. In high-traffic recipes, Potato, Beverages, and Pork are the most popular,          while Chicken, Dessert, and Vegetables receive less engagement. Conversely, in the            "Other" category, Breakfast, Beverages, and Chicken dominate, whereas Potato,                Vegetables, and Meat show minimal representation. Beverages are consistently popular in      both groups, but Breakfast stands out as a key driver in lower-traffic recipes.              Meanwhile, Potato and Pork attract significant engagement in high-traffic recipes but        are far less favored in the "Other" category. These insights highlight how different          food categories appeal to varying audience segments, helping to tailor content for            optimal engagement. 
    - The heatmap illustrates the correlation between various attributes, confirming several key observations. Notably, there is a moderate positive correlation (0.56) between "category" and "high_traffic," suggesting that certain recipe categories are more likely to attract high traffic. The heatmap also shows the correlation between "high_traffic" and various nutritional attributes. There is a weak correlation between "high_traffic" and nutritional components such as calories (0.07), carbohydrates (0.07), sugar (-0.09), and protein (-0.06). These low correlation values indicate that the nutritional content of recipes does not significantly influence their traffic levels.

## Model Development
  - The problem is a supervised binary classification task . The goal is to predict whether a recipe      will lead to high traffic or not based on the provided features (calories, carbohydrate, sugar, protein, category, etc.). This prediction will help the product team decide which recipes to display on the homepage to maximize traffic and subscriptions.

  - Reason for Model Selection
    - Logistic Regression :
Logistic regression is a good baseline model for binary classification tasks due to its simplicity, interpretability, and ability to handle linear relationships between features and the target variable.
It provides a strong starting point for comparison with more complex models.
    - Decision Tree Classifier :
Decision trees are non-parametric models that can capture non-linear relationships in the data. They are also interpretable, making them useful for understanding feature importance.
However, decision trees are prone to overfitting, so tuning parameters like max_depth is essential.
    - Support Vector Classifier (SVC) :
SVC is effective for binary classification problems and can handle both linear and non-linear relationships using kernel functions.
It is computationally efficient for smaller datasets but may require tuning of hyperparameters like C for optimal performance.
  - Code to fit the baseline and comparison models
    - all the codes are in the same file down with titles.
## Model Evaluation
  - Performance Metrics
We evaluated the models using the following metrics:
    - Accuracy : Proportion of correctly classified instances.
    - Precision : Proportion of true positives among predicted positives.
    - Recall : Proportion of true positives among actual positives.
    - F1 Score : Harmonic mean of precision and recall.
    - ROC AUC Score : Measures the ability of the model to distinguish between classes.
   

 - Logistic Regression outperformed all other models, achieving the highest accuracy (0.822), precision (0.856), recall (0.856), F1 score (0.856), and ROC AUC score (0.862). While the Decision Tree model showed the same performance notable improvement after hyperparameter tuning, it still fell short of Logistic Regression, particularly in ROC AUC score 0.86 to 0.81. The Support Vector Classifier, despite some tuning, delivered good performance but did not surpass Logistic Regression in any key metric, highlighting Logistic Regression's overall superiority in this analysis.
 
## Business Metrics
  - Metric Definition
To align with the business goal of predicting popular recipes 80% of the time while minimizing unpopular recommendations, we propose the following metric:

    - Weighted Accuracy : A custom metric that weights recall higher than precision to prioritize identifying popular recipes (high_traffic = "High"). The formula is:
Weighted Accuracy=0.7×Recall+0.3×Precision
  - Model Performance Using Business Metric
Using the weighted accuracy metric:
    - Logistic Regression: 0.7×0.856+0.3×0.856=0.856
    - Decision Tree: 0.7×0.856+0.3×0.856=0.856
    - Support Vector Classifier: 0.7×0.868+0.3×0.829=0.857
  - While the tuned Support Vector Classifier slightly outperforms logistic regression in this metric, logistic regression remains the most balanced and interpretable choice.


## Final summary including recommendations that the business should undertake
- Visualizations revealed significant differences in recipe categories between high-traffic and other recipes.
- High-traffic recipes favored categories like Potato , Beverages , and Pork , while lower-traffic recipes leaned toward Breakfast , Chicken , and Dessert .
- Nutritional attributes (calories, carbohydrates, sugar, protein) showed weak correlations with traffic levels, indicating that these factors alone are not strong predictors of popularity.

- Recommandations
    - Deploy Logistic Regression Model :
Given its superior performance, interpretability, and alignment with business goals, the tuned Logistic Regression model should be deployed to predict high-traffic recipes.
This model will help the product team identify and display recipes that are likely to drive higher traffic and subscriptions.
    - Monitor Weighted Accuracy :
Use the Weighted Accuracy metric to evaluate model performance in production.
Set a minimum threshold of 0.8 to ensure the model meets the business requirement of correctly predicting popular recipes 80% of the time.
    - Leverage Recipe Categories :
Focus on promoting recipes from categories identified as high-traffic drivers: Potato , Beverages , and Pork .
Avoid over-representing less popular categories like Chicken , Dessert , and Vegetables unless they align with specific customer preferences or seasonal trends.
    - Feature Engineering :
Explore additional features such as seasonality , user demographics , and recipe metadata (e.g., keywords, tags) to further improve model performance.
Incorporate feedback loops to capture user interactions (e.g., clicks, shares) and refine predictions over time.
    - Iterative Improvement :
Continuously monitor model performance and retrain periodically with new data to adapt to changing user preferences.
Conduct A/B testing to validate the impact of recommended recipes on website traffic and subscription rates.
    - Enhance Data Collection :
Address gaps in the current dataset, particularly missing nutritional values and ambiguous categorization.
Standardize data collection processes to ensure consistency and completeness for future analyses.



