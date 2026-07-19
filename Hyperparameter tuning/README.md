# Hyperparameter Tuning for Cardiovascular Age Prediction Models

This repository provides the complete implementation of hyperparameter optimization pipelines for seven machine learning (ML) and deep learning (DL) models used for cardiovascular age prediction. All models were systematically tuned using cross-validation and Optuna-based optimization strategies to ensure fair comparison of predictive performance. Model selection was based on validation and test dataset performance, and the best-performing model (CatBoost) was subsequently used to construct the final multimodal cardiovascular aging framework described in the manuscript.

## The repository includes reproducible code for:

CatBoost (<a href="Catboost_hyperparameter_tuning.py">**Catboost_hyperparameter_tuning.py**</a>)

ElasticNet regression (<a href="ElesticNet_hyperparameter_tuning.py">**ElesticNet_hyperparameter_tuning.py**</a>)

Support Vector Regression (<a href="SVM_hyperparameter_tuning.py">**SVM_hyperparameter_tuning.py**</a>)

LightGBM (<a href="LightGBM_hyperparameter_tuning.py">**LightGBM_hyperparameter_tuning.py**</a>)

XGBoost (<a href="XGBoost_hyperparameter_tuning.py">**XGBoost_hyperparameter_tuning.py**</a>)

Deep Neural Network (<a href="DNN_hyperparameter_tuning.py">**DNN_hyperparameter_tuning.py**</a>)

TabR (<a href="TabR_hyperparameter_tuning.py">**TabR_hyperparameter_tuning.py**</a>)

## Hyperparameter Optimization Framework
### General Setup
Framework: Optuna (https://optuna.org/)

Cross-validation: 10-fold

Model input: Mutimodal cardiovascular aging biomarkers

Optimization metric: Mean R² across validation folds

Pruning: MedianPruner (early stopping of underperforming trials)

Trials: 200 trials for ML and 100 trials for DL models

Output: Optimal hyperparameter set with best R² value

### Required environments
Python (version >= 3.10.0)

optuna (version >= 4.1.0)

numpy (version >= 1.26.0)

pandas (version >= 2.2.3)

scikit-learn (version >= 1.5.2)

catboost (version >=  1.2.7)

lightgbm (version >= 4.6.0) 

xgboost (version >= 2.1.2)

torch (version >= 2.0.0)

pytorch-tabr (version >= 0.1.0)
