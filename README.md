## Telecom Churn Prediction

Any business wants to maximize the number of customers. To achieve this goal, it is important not only to try to attract new ones, but also to retain existing ones. Retaining a client will cost the company less than attracting a new one. In addition, a new client may be weakly interested in business services and it will be difficult to work with him, while old clients already have the necessary data on interaction with the service.

Accordingly, predicting the churn, we can react in time and try to keep the client who wants to leave. Based on the data about the services that the client uses, we can make him a special offer, trying to change his decision to leave the operator. This will make the task of retention easier to implement than the task of attracting new users, about which we do not know anything yet.

You are provided with a dataset from a telecommunications company. The data contains information about almost six thousand users, their demographic characteristics, the services they use, the duration of using the operator's services, the method of payment, and the amount of payment.

The task is to analyze the data and predict the churn of users (to identify people who will and will not renew their contract). The work should include the following mandatory items:

- Description of the data (with the calculation of basic statistics);
- Research of dependencies and formulation of hypotheses;
- Building models for predicting the outflow (with justification for the choice of a particular model) based on tested hypotheses and identified relationships;
- Comparison of the quality of the obtained models.

### 1. Goal

Building models for predicting outflow.
Which customers are likely to churn? What are the attributes that make you think so?

### 2. Dataset

There is data available on 5’986 customers. And this task is also available on Kaggle (https://www.kaggle.com/radmirzosimov/telecom-users-dataset)

#### 2.1 The features:
- customerID - customer id
- gender - client gender (male / female)
- SeniorCitizen - is the client retired (1, 0)
- Partner - is the client married (Yes, No)
- tenure - how many months a person has been a client of the company
- PhoneService - is the telephone service connected (Yes, No)
- MultipleLines - are multiple phone lines connected (Yes, No, No phone service)
- InternetService - client’s Internet service provider (DSL, Fiber optic, No)
- OnlineSecurity - is the online security service connected (Yes, No, No internet service)
- OnlineBackup - is the online backup service activated (Yes, No, No internet service)
- DeviceProtection - does the client have equipment insurance (Yes, No, No internet service)
- TechSupport - is the technical support service connected (Yes, No, No internet service)
- StreamingTV - is the streaming TV service connected (Yes, No, No internet service)
- StreamingMovies - is the streaming cinema service activated (Yes, No, No internet service)
- Contract - type of customer contract (Month-to-month, One year, Two year)
- PaperlessBilling - whether the client uses paperless billing (Yes, No)
- PaymentMethod - payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
- MonthlyCharges - current monthly payment
- TotalCharges - the total amount that the client paid for the services for the entire time
- Churn - whether there was a churn (Yes or No)


### 3. Data Cleaning 

- changing data types
- checking whether NaN's and/or Null values exist 
- dropping columns, that are not relevant


### 4. Data Analysis and Features Importance

Feature selection process of finding and selecting the most useful features in a dataset. Unnecessary features decrease training speed, the model interpretability and the generalization performance on the test set. Estimating the influence of a given feature to a model prediction is importante mainly in large datasets for performance gain by selecting only the most relevant ones.

- the composition of churn: churn rate= 26.5%
- analysing demographic information with visualization tools: no difference in churn rate regarding gender; churn rate of senior citizens is almost double that of young citizens, customers with a partner churn less than customers with no partner
- analysing customer account information — categorical variables: customers with month-to-month contracts have a higher churn rate; customers who opted for an electronic check as paying method are more likely to leave the company; customers subscribed to paperless billing churn more than those who are not subscribed
- analysing customer account information — numerical variables: the churn rate tends to be larger when monthly charges are high; new customers (low tenure) are more likely to churn; clients with high total charges are less likely to leave the company
- analysing services information - we do not expect phone attributes (PhoneService and MultipleLines) to have significant predictive power; clients with online security churn less than those without it; customers with no tech support tend to churn more often than those with tech support; customer with less extra packages tend to churn more

Mutual information — analysis of linear and nonlinear relationships between categorical columns - according to the mutual_info_score, the following features had the highest predictive power:

1. Contract               
2. OnlineSecurity         
3. TechSupport            


### 7. Models

- set a baseline model: the rate of customers that did not churn (most frequent class 73.5%) was used as a baseline model to evaluate the quality of the models generated; the tested models should outperform the baseline capabilities to be considered for future predictions
- split data into train/ test sets
- define pipeline for preprocessing
- use PyCaret to determine best model
- create a Custom Metric in Pycart - Profit - to select the model that maximizes the business value; on average the monthly cost for customers that churn is higher around $15 per month; if we offer a $180 annual voucher to all the customers flagged by the model as potential churn, we gain $720 per customer in 1 year
  Profit Custom Metric:
  If we predict churn and the real value is churn, we gain ($720 - $180) per customer
  If we predict churn and the real value is not churn, we loose ( - $180) per customer

- select the model that maximizes the business value and the accuracy score
- chose the logistic regression model and tune it with PyCaret
- apply SHAP analysis to determine how significant each factor is in determining the final prediction the model (Logistic Regression) outputs; the following features had the highest predictive power:

1. Monthly Charges
2. Tenure
3. Contract

  
### 8. Conclusion 
- if you apply the Logistic Regression tunned model identified by our analysis and try to retain customers with high probability of churn by offering them vouchers of $180, it's a good starting point and profitable strategy to maximize the business value
- future recommendations: offer more personalized discounts: engage with the product managers, marketing and financial department to offer potential churn customers personalized discounts and packages to deter churning


### 9. Tools
Jupyter notebook, Python 3.5.2 (Sklearn, Pandas, Numpy, Matplotlib and Seaborn), PyCaret, Shap Analysis

Code: https://github.com/solpr/Telecom-users/blob/main/Telecom%20Churn%20Rate.ipynb

