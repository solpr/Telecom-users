### Telecom Churn Prediction

Any business wants to maximize the number of customers. To achieve this goal, it is important not only to try to attract new ones, but also to retain existing ones. Retaining a client will cost the company less than attracting a new one. In addition, a new client may be weakly interested in business services and it will be difficult to work with him, while old clients already have the necessary data on interaction with the service.

Accordingly, predicting the churn, we can react in time and try to keep the client who wants to leave. Based on the data about the services that the client uses, we can make him a special offer, trying to change his decision to leave the operator. This will make the task of retention easier to implement than the task of attracting new users, about which we do not know anything yet.

You are provided with a dataset from a telecommunications company. The data contains information about almost six thousand users, their demographic characteristics, the services they use, the duration of using the operator's services, the method of payment, and the amount of payment.

The task is to analyze the data and predict the churn of users (to identify people who will and will not renew their contract). The work should include the following mandatory items:

- Description of the data (with the calculation of basic statistics);
- Research of dependencies and formulation of hypotheses;
- Building models for predicting the outflow (with justification for the choice of a particular model) based on tested hypotheses and identified relationships;
- Comparison of the quality of the obtained models.

1. Goal

Building models for predicting outflow.
Which customers are likely to churn? What are the attributes that make you think so?

2. Dataset
There is data available on 5’986 customers. And this task is also available on kaggle (https://www.kaggle.com/radmirzosimov/telecom-users-dataset)

2.1 The features:
customerID - customer id
gender - client gender (male / female)
SeniorCitizen - is the client retired (1, 0)
Partner - is the client married (Yes, No)
tenure - how many months a person has been a client of the company
PhoneService - is the telephone service connected (Yes, No)
MultipleLines - are multiple phone lines connected (Yes, No, No phone service)
InternetService - client’s Internet service provider (DSL, Fiber optic, No)
OnlineSecurity - is the online security service connected (Yes, No, No internet service)
OnlineBackup - is the online backup service activated (Yes, No, No internet service)
DeviceProtection - does the client have equipment insurance (Yes, No, No internet service)
TechSupport - is the technical support service connected (Yes, No, No internet service)
StreamingTV - is the streaming TV service connected (Yes, No, No internet service)
StreamingMovies - is the streaming cinema service activated (Yes, No, No internet service)
Contract - type of customer contract (Month-to-month, One year, Two year)
PaperlessBilling - whether the client uses paperless billing (Yes, No)
PaymentMethod - payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
MonthlyCharges - current monthly payment
TotalCharges - the total amount that the client paid for the services for the entire time
Churn - whether there was a churn (Yes or No)


3. Data Cleaning 


4. Features Importance
Feature selection process of finding and selecting the most useful features in a dataset. Unnecessary features decrease training speed, the model interpretability and the generalization performance on the test set. Estimating the influence of a given feature to a model prediction is importante mainly in large datasets for performance gain by selecting only the most relevant ones.

According to the feature importance analysis produced by the Random Forest algorithm, the following features had the highest predictive power:

1. 
2.
3.

6. Customer classtering

7. Models
...... models have been constructed for application in the problem of this project, namely:

Gradient Boosted
Random Forest
AdaBoost
Logistic Regression



Their respective F1, AUC , measures are listed below:
.....
.....
 ...... produced the highest AUC and the following scores:

  Accuracy: .... % labeled correctly
  Precision: ....%  labeled as churn actually churned (... % were wrongly labeled as churn)
  Recall: ... % that actually churned were labeled as churn (.... % of churn users were labeled as non-churn)
  
8. Conclusion 

9. Tools
Jupyter notebook, Python 3.5.2 (Sklearn, Pandas, Numpy, Matplotlib and Seaborn)

Code: .... (github Link)
