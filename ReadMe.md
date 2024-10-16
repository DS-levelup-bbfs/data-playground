## Description

#### Can we predict if a credit card transaction is fraudulent?

Credit card company *BBD Bank* needs to identify fraudulent transactions. Using synthetically generated data, you will build a ML model that predicts whether a transaction is fraudulent or not.

#### Where's the data?

The data is split into four datasets (separate files): You will use the  **train data** , along with other data to build your model, and **test data** to make your predictions using your model.
Go to the **Data** page for more information on the data sets.

#### How to create your first model and make your submission:

#### Step 1.

Create your model using Kaggle Notebooks, Google Colab or Jupyter Notebooks

#### Step 2.

Upload your CSV submission file to Kaggle via the "Submit Predictions" button in the upper-righthand corner of this page.

#### Evaluation

It is your job to predict for each transaction, ****whether it will result in TX_FRAUD (1) or not (0). Your predictions should be a probability between 0 and 1.0****. Submissions are evaluated on [AUC](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc), which is a number between 0 and 1, where 0.0 means 100% of the predictions are wrong, and 1.0 means 100% of the predictions are correct. Randomly guessing should give a score of 0.5. The submission file should contain a header and have the following format: ``TX_ID,TX_FRAUD 121212121212,0.30 3434343434,1.0 ...`` You can download an example submission file (csv) on the Data page.

### BI Challenge

# Business Intelligence Challenge

## Goal

The goal of this challenge is to explore the available dataset from a payments business perspective to draw conclusions and gather insights that could be of interest to Tony who is the head of payment for BBD Bank.

Share your dashboard/notebook/visualizations at the end competition deadline.

## How you will be evaluated

Your team will be given 5 minutes to present your dashboard/insights at the end of the hackathon, and you will be evaluated by judges based on:

1. **Business Impact** : what is the potential business impact of your dashboard or insights?
2. **Storytelling** : the effectiveness of a story or theme across your dashboard/visualizations/insights
3. **Creativity** : how creative were you in the use of data, visualizations, tooling?

## Getting Started

As a starting point, you can explore the data using Excel/PowerBI or a Jupyter notebook

### Tips On Improving ML Models

## How can I improve my predictions? My rank is not going up.

### Feature selection

* try selecting the features that you think are most important to the model

### Model selection and hyperparameter tuning

* have you tried choosing different classification models? have you tried tuning some of its hyperparameters? Check out the docs on each of the models below:
  * [`logistic_reg`](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create)
  * [`boosted_tree_classifier`](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create-boosted-tree)
  * [`dnn_classifier`](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create-dnn-models)
  * [`automl_classifier`](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create-automl)

You can also learn how to use [BigQuery ML&#39;s automated HP tuning capabilities in this blogpost](https://cloud.google.com/blog/topics/developers-practitioners/access-free-training-and-learn-how-automate-hyperparameter-tuning-find-best-model).

### Feature engineering

* could the day of week have an impact on purchasing patterns? use the [EXTRACT](https://cloud.google.com/bigquery/docs/reference/standard-sql/timestamp_functions#extract) function to retrieve the year/month/day/hour/minute/etc. from a TIMESTAMP column
* can you multiple, divide, add, or subtract numerical features to create new features?
* can you augment the weight of outliers by squaring numerical features, or on the other hand, taking the square root?
* could combinations of features impact purchasing patterns more than individual columns? You can use [ML.FEATURE_CROSS](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-preprocessing-functions#mlfeature_cross) to create interactions on category variables
* would it help to scale quantitative variables using [ML.STANDARD_SCALER](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-preprocessing-functions#mlstandard_scaler)?
* are numerical features too granular? Could you bucketize them using [ML.QUANTILE_BUCKETIZE](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-preprocessing-functions#quantile_bucketize)?
* check out all of the [pre-processing features built into BigQuery ML](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-preprocessing-functions)

### Ensembling models

* the combination of multiple model outputs may be better than any single model alone. As a simple example, you can try to take the mean/median of the probability outputs of ML.PREDICT across multiple models. For example, for a specific row, if model_1 and model_2 predict 0.5 and 1.0 respectively, then the averaged prediction would be 0.75.
