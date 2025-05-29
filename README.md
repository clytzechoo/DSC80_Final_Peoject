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
- **Improvement plan:** Add engineered features like protein content, categorical encodings for tags, and model tuning (e.g., using Random Forest or Lasso).

## ⚖️ Fairness Analysis

(To be completed in Week 10)

---

Created by balabala~~~~
UC San Diego — Spring 2025
