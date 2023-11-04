# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
The objective of the analysis is to use machine learning to predict high-risk loans from a given data set. The model created can classify loans as low-risk or "high-risk" based on other variables. This  model could be used to make decisions about loan approvals while minimizing risk.

* Explain what financial information the data was on, and what you needed to predict.
The dataset included some financial variables in a CSV file (lending_data.csv). The provided financial information included loan size, interest rate, borrower income, debt-to-income ratio, number of accounts, derogatory marks on a credit file, and total debt. The dependent variable was loan_status, which indicates if a loan is healthy or high-risk.

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
The dependent variable (loan_status), shows two segments: 0 for healthy loans and 1 for high-risk loans. The value_counts indicated a significantly higher amount of healthy loans vs. high-risk ones. 

* Describe the stages of the machine learning process you went through as part of this analysis.
- Data Splitting: The data set was split into a training set and a testing set.
- Model Training: A LogisticRegression model was used on the original dataset.
- Model fit and evaluation: The model was used to predict loan status on the testing set, and then it was evaluated using balanced accuracy, confusion matrix, and classification report.
- Oversampling: To improve accuracy, RandomOverSampler was used.
- Model re-fit and evaluation: A new model was trained on the resampled dataset to compare against the original model.

* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).
-Logistic Regression: this was used to predict the the outcome of the dependent variable.
-Resampling with RandomOverSampler: This helped to improve the accuracy of the model.
-Performance Metrics: Various ways to evaluate the model were used: balanced accuracy score, confusion matrix, and classification report. 


## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * The model predicts both classes quite accurately. It does better predicting healthy loans than high-risk ones. However, even for high-risk loans the prediction is quite strong based on the balance score, the confusion matrix and the classification report. That said, the fact that the model predicts a high-risk loan 86% of the times (Precision), it is a bit worrisome from the practical point of view. 14% of wrong predictions could lead to missing high-risk loans. The model should continue to be trained with more data to improve its Precision.



* Machine Learning Model 2:
  * The results using the resampled data show improvements compared to the model trained with the test data. The balanced accuracy has improved (95% to 99%), showing a better accuracy for both classes. Also, the number of high-risk loans incorrectly predicted as healthy has declined, as shown in the confusion matrix. While the number of healthy loans predicted as high-risk has increased, this issue can be managed with increased scrutiny by the users. The recall score in the resampled model has shown significant improvements.  The model is quite strong at predicting high-risk loans.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
The original Regression model (train/test data), showed a high accuracy rate. However, it showed a proportion of high-risk loans that could potentially be wrongly classified.
The model with the oversampled data showed an improvement in predicting high-risk loans.  While there was a sligth increase in false positives (healthy loans predicted as high-risk) this could be more acceptable. The key performance metrics, such as the balanced accuracy score and the F1 score for high-risk loans, were better compared to the original model.

* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )
In this context (loan risk prediction), it's crucial to minimize false negatives (predicting a high-risk loan as healthy) as this could result in financial losses, whereas a false positive (predicting a healthy loan as high-risk) might result in missed opportunities.
Considering this, Precision, Recall, and F1 score for high-risk loans are particularly important.

If you do not recommend any of the models, please justify your reasoning.
I would recommend using the model based on the oversampling.