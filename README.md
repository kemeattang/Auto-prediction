# auto-prediction
The following questions where answered with this code
1.Model in predicting price
2.Evaluating the model using RMSLE

Every step involved :
preprocessing:
imputation with medians, because it's simple to implement and often works well in practice. alternatives: dropping the values, imputing with models
one hot encoding for categorical variables. alternatives: mean target value
model selection
I tried only very simple models because the dataset is small
I selected the model based on the test error
hyper parameters
I (almost) did not tune any parameters. The proper approach would be to do it via taking a part of the traning set as a valiation set and use it for tuning the parameters, or doing k-fold CV
evaluation criteria
I used RMSLE because it's often used when dealing with prices: it penalizes more the mistakes for low prices and less for high prices. Alternatives are other evaluation metrics for regression such as RMSE, MAE and others
B. Describe how you would improve the model in Question 3 if you had more time.
More feature engineering
Right now I use features almost as is, but it is possible to derive mode features from the existing ones.
For example, feature interactions like length $\times$ width $\times$ height or make $\times$ body-style
Proper CV
Here I use only the held out dataset for model evaluation AND model selection. In this case I only compared two models, so it is OK. However, if there are more models and some of them need parameter tuning, a proper Cross-Validation framework is needed. Something like K-fold on the train data should be enough
Better handling of missing values. E.g. with models
More models
SVR
Tree based like Random Forest or GBM - but I'd need to be careful with these, because there is little data, so they could easily overfit
