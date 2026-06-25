# The Main Cardiovascular Age Prediction Model Analysis
This repository contains the best-performing model catboost hyperparameter search results,  code of prediction of cardiovascular age on the entrite Non-CVD cohort defined in the manuscript, age-bias correction steps, as well as statistical code for downstream association analysis of defined CardioAG (model predicted cardiovascular age - choronological age, post bias correction) with incodent CVD outcomes, and assoition of selected lifestyle factors with CardioAG.

## Cardiovascular aging model prediction
### Step 1: Data Partitioning

The dataset was divided into a training cohort (Cheadle center) and an independent external test cohort (Reading and Newcastle centers). Individuals with missing  feature sets were excluded prior to analysis.

### Step 2: Model Specification and Hyperparameters
A CatBoost regression model was used to predict chronological age based on multimodal cardiovascular features. Hyperparameters were selected from a previously performed optimization procedure with saved results (<a href="hyperparameter_search_results_catboost.csv">**hyperparameter_search_results_catboost.csv**</a>) and fixed for all subsequent analyses.

### Step 3: Cross-Validation and Out-of-Fold Prediction
A 10-fold cross-validation scheme was applied to the training cohort. In each fold, models were trained on 9 folds and validated on the remaining fold. Out-of-fold predictions were aggregated across all folds to obtain unbiased predictions for the entire training cohort, which were later used for age-bias estimation.

### Step 4: Final Model Training and Validation
The final model was retrained using the full training cohort and evaluated on the independent external test cohort, which remained completely unseen during model development. Model performance was evaluated using mean absolute error (MAE), coefficient of determination (R²), and Pearson correlation coefficient (r).

### Step 5: Age-Bias Correction
To account for systematic age-dependent prediction bias, out-of-fold predictions obtained from 10-fold cross-validation on the training cohort were first used to compute prediction errors relative to chronological age (age gap). A linear Gaussian model was then fitted to characterize how these residual errors vary as a function of age. The estimated age-dependent bias component was subsequently applied to adjust model predictions across the full study cohort. The resulting bias-corrected prediction difference was defined as CardioAG.

## Downstream Statistical Analysis of CardioAG
### Lifestyle Association Analysis
Associations between lifestyle factors and CardioAG were evaluated using linear regression models in the Non-CVD cohort. Each lifestyle exposure was modeled separately, with CardioAG as the dependent variable.

### Survival Analysis
Cox proportional hazards regression was applied to evaluate the association between CardioAG and incident cardiovascular disease outcomes as defined in the manuscript. The proportional hazards assumption was assessed for all models using Schoenfeld residuals.

Two hierarchical models were fitted:

Model 1 (Unadjusted): CardioAG as the sole predictor.

Model 2 (Adjusted): CardioAG additionally adjusted for chronological age, sex, body mass index (BMI), and diabetes mellitus.

### Incremental Prognostic Value of CardioAG
To evaluate the added prognostic contribution of CardioAG, likelihood ratio tests were performed comparing nested Cox models. A base model including established risk factors (age, sex, BMI, diabetes) was compared against an extended model additionally incorporating CardioAG. This analysis was repeated using CardioAG derived from modality-specific biomarker subsets to assess the incremental predictive value of each modality or their combinations.

### Statistical Software
All downstream statistical analysis in this repository were conducted using R (version>= 4.3.2), including the following packages:

survival, lmtest, dplyr



