# DSC80_Final_Project
recipe-ratings-analysis

# 🍽️ Recipe Ratings Analysis

Welcome to our DSC 80 Final Project!  
We explore what factors influence the average rating of recipes on food.com using real-world recipe and review data.

---

## 📊 Introduction

We investigate whether characteristics like calorie count and preparation time impact how highly a recipe is rated. Our main goal is to find useful patterns and build a model to predict average ratings based on recipe features.

## 🧼 Data Cleaning and Exploratory Data Analysis

- Parsed the `nutrition` column into separate numeric fields (e.g., calories, sugar, protein).
- Removed invalid ratings (rating = 0).
- Merged recipe data with average user ratings.

**Preview of cleaned data:**
(We will include markdown tables and plots here later.)

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
