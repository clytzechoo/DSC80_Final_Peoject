# DSC80_Final_Project
recipe-ratings-analysis

# 🍽️ Recipe Ratings Analysis

Welcome to our DSC 80 Final Project!  
We explore what factors influence the average rating of recipes on food.com using real-world recipe and review data.
https://github.com/clytzechoo/DSC80_Final_Project/edit/main/README.md
---

## 📊 Introduction

Food is an essential part of our daily lives, and cooking serves as a hobby that brings joy and a sense of accomplishment to many. While numerous people are fond of fatty foods due to their delicious taste and the satisfaction they bring when eaten, this type of food, particularly those rich in saturated fat, contains more calories. The health risks associated with them, such as cardiovascular diseases, diabetes, and obesity, cannot be ignored. A Harvard University study published in JAMA Internal Medicine in 2016 showed that a long - term diet high in saturated fat is linked to a 2 - fold increased risk of coronary artery calcification. Another study in Diabetes Care in 2019 found that when consuming more than 1,000 calories per day for five days, insulin sensitivity decreased by 27%.
With this knowledge in mind, we aim to explore the relationship between the rating of a recipe and the amount of calories and saturated fat in it. Our goal is to predict the average rating of a recipe and understand its connection with the calories and saturated fat content in recipes. To achieve this, we are analyzing two datasets that include recipes and ratings posted on food.com since 2008.

The first dataset, **recipes**, contains 83782 rows, indicating 83782 unique recipes, with 10 columns. 

The second dataset, **interactions**, contains 731927 rows and each row contains a review from the user on a specific recipe.

we are investigating whether people rate high calorie recipes and the common calorie recipes on the same scale. To facilitate the investigation of our question, we separated the values in the **'nutrition'** columns into the corresponding columns, **'calories (#)', 'total fat (PDV)', 'sugar (PDV)', scurated fat (PDV)**, etc. PDV, or percent daily value shows how much a nutrient in a serving of food contributes to a total daily diet. Moreover, we calculated the proportion of sacurated fat in terms of calories out of the total calories of a given recipe and stored the information in a new column, **'prop sacurated fat'**. because high scureated fat in here will be referring to the recipes with value **'prop_sugar'** higher than the average 'prop_sugar'. The most relevant columns to answer our question are **'calories(#)', 'scureated fat (PDV)', 'prop scurated fat'**, described above, **'rating'**, which is the rating that user gave on a recipe, and **'avg_rating'**, which are the average of the ratings on each unique recipes.

Our research could lead to future work on diving deeper into how much awareness people have on the negative health effects of high colorie recipes.

## 🧼 Data Cleaning and Exploratory Data Analysis

we conducted the following data cleaning steps:

  1. Left merge **'recipes', 'interactions'** two datasets.
  2. Replace 0 rating to np.nan.
  3. Get average rating for each recipe and add avg_rating to recipes dataset.
  4. Retrieve data from **nutrition** list-like string.
  5. Seperate values for research to series: **calories, total fat, protein, sacurated fat, carbohydrates**.
     
      We applied a **lambda** function then converted the columns to floats.
  6. Add **'prop scurated fat'** to the dataframe.
     
      prop sacurated fat is the proportion of sacurated fat of the total calories in a recipe. We use the values in the **scurated fat (PDV)** column to divide by 100% to get it in the decimal form. Then, we multiply by 20 to convert the values to grams of sacurated fat since 20 grams of scurated fat is the 100% daily value (PDV). We got this value of 20 grams from experimenting on food.com with different amounts of scurated fat in a recipe. The experimentation allows us to understand the nutrition formula used on the website for recipes. Lastly, we multiply by 9 since there are 9 calories in 1 gram of sugar. After all these conversions, we end up with the number of calories of scurated fat, so we can divide by the total amount of calories in the recipe to get the proportion of scurated fat of the total calories. It is convenient to show the values will be between 0 and 1.
  7. Add **'is_high_sacurated_fat'** to the dataframe.

      'is_high_sacurated_fat' is a boolean column checking if proportion of sacurated fat lager than 10% of calories. This step separates the recipes into two groups, ones that are high sacurated fat and ones that are not.
  8. Add **'is_high_calorie'** to the dataframe.

      'is_high_calorie' is a boolean column checking if calories of recipe more than 600. This step separates the recipes into two groups, ones that are high calorie and ones that are not.
  9. Add **'is_vegan'** to the dataframe.

      'is_vegan' is a boolean column checking if **'vegan'** is in tags of recpie. This step separates the recipes into two groups, ones that are vegan and ones that are not.
  10. Add **'is_quick'** to the dataframe.

      'is_quick' is a boolean column checking if **'quick'** is in tags of recpie. This step separates the recipes into two groups, ones that are quick and ones that are not.

**Preview of cleaned data:**


## 📈 Hypothesis Testing

- **Null Hypothesis:** High-calorie and low-calorie recipes have the same average rating.
- **Alternative Hypothesis:** High-calorie recipes have higher average ratings.
- **Result:** P-value ≈ 0.972 → Fail to reject the null.

We found no significant evidence that high-calorie recipes are rated higher.

## 🤖 Prediction Model

We are predicting **average rating** (regression task).

- **Baseline model:** Linear regression with basic features (e.g., calories, steps).
- **Improvement plan:** Add engineered features like proportion of saturated fat, protein content, categorical encodings for tags, and model tuning (e.g., using Random Forest or Lasso). Since we do not find definite conclusion that there is difference between high and low calories recipes from the above hypothesis test, so we decide to investigate on new features: high and low amount of saturated fat recipes have different average ratings.
- **result:**
Sacurated Fat Proportion Results:

  Present mean: 0.164344

  Missing mean: 0.170520

  Observed statistic: 0.006176

  P-value: 0.010989

  Conclusion: Reject null

  Number of Steps Results:

  Present mean: 10.058948

  Missing mean: 11.551936

  Observed statistic: 1.492987

  P-value: 0.000999

  Conclusion: Reject null

  Sacurated Fat Recipes: 4.6317

  Common Recipes: 4.6161

  Observed statstics: 0.0156

  P_value: 0.0020

  Conclusion: Reject null

  High sacurated fat recipes: 48174

  Common recipes: 32999


- **conclusion:** Based on α=0.05, from the hypothesis test above, we reject H0 and have enough evidence that the difference in ratings between high saturated fat and low fat.
## ⚖️ Fairness Analysis

- We use permutation test to create the hypothesis tests above, we reject H0 and have enough evidence that the proportion of saturated fat really affect the results.

Created by balabala~~~~
UC San Diego — Spring 2025
