# Used-Car-Dataset-ML

## Objective
Build a model to predict entry prices of used cars using Python on Jupyter Notebook limited to 4 input variables using the used cars dataset from Kaggle, collected by Austin Reese, which contains 45K+ used car seller entries and 26 input variables from Craigslist.

## Description
We first tested Linear Regression as an experiment for comparison. A Random Forest Regression was then used in conjunction with a randomised search cross-validation because of its ‘wisdom of the crowds’ approach, whereby multiple decision trees are combined into a final tree and despite each decision tree having a high variance, combining all of them reduces the resulting variance. Moreover, Random Forests are accommodating to categorical and numerical variables, are less sensitive to missing data, and handle outliers well. Lastly, Random Forests display feature importances, which is useful to help us narrow down our variables from nine (‘manufacturer’, ‘drive’, ‘transmission’, ‘type’, ‘fuel’, ‘paint color’, ‘state’, ‘year’, and ‘odometer’) to four. For our practical, we measure the performance of our model based on the accuracy on both the training and test set, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE) - both measure the average of errors as defined by the differences between the predicted values and actual values. 
Our linear regression model performs equally well (46% accuracy) on both train and test with nine variables, indicating that overfitting is not an issue. We use this as a comparison of performance for our Random Forest with its default n_estimators = 100, which yields a higher accuracy on training (96.7%) than on test (78%). Our MAE and RMSE scores tend to be relatively high but improves with the Random Forest model.
We use the sklearn feature_selection() to identify the variables that influence our model the most and accordingly narrow down our variables to four (‘manufacturer’,‘type’, ‘year’, and ‘odometer’) before running our model again. We also try to improve our accuracy by performing hyper-parameter tuning, which helps us validate our model before evaluating over the test set. We choose to train 20 models over 5 folds of cross- validation (100 models total). From this, we can identify the optimal number for the max_depth of trees and number of estimators at each node split. Since we already know our max_features as four variables, we do not need to tune it. Running our Random Forest Regressor with these conditions yields an accuracy of ~ 44% on the training and test set. The reduction in variables has conversely affected our accuracy and error rates but the hyper tuning indicates that our model is no longer overfitting since our training and test sets have similar accuracies.
Conclusively, while our Random Forests performed reasonably, we can likely improve accuracy and reduce errors through a combination of feature engineering and further transforming our data set. Our final scatter plot, however, displays a plateau rather than a linearity in values indicating that Random Forests are unable to extrapolate outside unseen data. As such, Random Forests may better suited for classification problems where data is not linear or bound by a time series and extrapolation is not required, and we can experiment with other supervised learning regression models.
