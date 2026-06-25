# The Main Cardiovascular Age Prediction Model Analysis
This repository contains the best-performing model catboost hyperparameter search results,  code of prediction of cardiovascular age on the entrite Non-CVD cohort defined in the manuscript, age-bias correction steps, as well as statistical code for downstream association analysis of defined CardioAG (model predicted cardiovascular age - choronological age, post bias correction) with incodent CVD outcomes, and assoition of selected lifestyle factors with CardioAG.

## Cardiovascular aging model prediction
### Step 1: 
Split the data into train and test data set and loading the best hyperparameter set from the search results (<a href="hyperparameter_search_results_catboost.csv">**hyperparameter_search_results_catboost.csv**</a>)

### Step 2: 
Get the model predictions of the train data through 10-fold cross validation for age-bias calculation

## Step 3:
Retraining the model on the entire training data and get the final predictions on the entire study cohort

## Step 4:
Fit the age-bias regression and get bias coeffients

## Step 5:
Correct the age-bias for final model predictions for all study cohort



