# Hyperparameter Tuning for Cardiovascular Age Prediction Models

This repository provides the complete implementation of hyperparameter optimization pipelines for seven machine learning (ML) and deep learning (DL) models used for cardiovascular age prediction. All models were systematically tuned using consistent cross-validation and Optuna-based optimization strategies to ensure fair comparison of predictive performance. Model selection was based on validation and test dataset performance, and the best-performing model (CatBoost) was subsequently used to construct the final multimodal cardiovascular aging framework described in the manuscript.

The repository includes reproducible code for:

CatBoost (<a href="/Catboost_hyperparameter_tuning.py">**Catboost_hyperparameter_tuning.py**</a>)
ElasticNet regression (ElesticNet_hyperparameter_tuning.py)
Support Vector Regression (SVR, SVM_hyperparameter_tuning.py)
LightGBM (LightGBM_hyperparameter_tuning.py)
XGBoost (XGBoost_hyperparameter_tuning.py)
Deep Neural Network (DNN, DNN_hyperparameter_tuning.py)
Retrieval-Augmented Neural Network for Tabular Data (TabR, TabR_hyperparameter_tuning.py)

Hyperparameter Optimization Framework
General Setup
Framework: Optuna (https://optuna.org/)
Cross-validation: 10-fold 
Optimization metric: Mean R² across validation folds
Pruning: MedianPruner (early stopping of underperforming trials)
trials: 200 trials for ML and 100 trials for DL models
Output: optimal hyperparameters set with best R² value

Required environments
Python (version >=3.10)
numpy
pandas
scikit-learn
optuna
catboost
lightgbm
xgboost
torch
pytorch-tabr
