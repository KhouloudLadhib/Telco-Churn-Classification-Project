# Telco Churn Classification Project

## Overview

### Goal
This python code analyzes data of a fictional telco company that provided home phone and internet services to 7043 customers in California in Q3. The goal is build a classification model that could predict if a customer will churn or not. Below are the questions that the project answers.

* What is the distribution of churn value?
* What is the count of male vs. female by churn value?
* What is the mean churn value count by contract type?
* Is there a relationship between churn value and monthly charges?
* What's the most popular payment method?
* Do more people enroll in device protection?
* Do most people go paperless?
* What are the top 5 reasons why customers churn?
* What is the most correlated factor to churn value?

### Data
The initial dataset contains 7042 rows, each representing a customer, and 33 columns.

#### Variables
##### Demographics
CustomerID: A unique ID that identifies each customer.  
Count: A value used in reporting/dashboarding to sum up the number of customers in a filtered set.  
Gender: The customer’s gender: Male, Female  
Age: The customer’s current age, in years, at the time the fiscal quarter ended.  
Senior Citizen: Indicates if the customer is 65 or older: Yes, No  
Married: Indicates if the customer is married: Yes, No  
Dependents: Indicates if the customer lives with any dependents: Yes, No. Dependents could be children, parents, grandparents, etc.  
Number of Dependents: Indicates the number of dependents that live with the customer.  

##### Location
CustomerID: A unique ID that identifies each customer.  
Count: A value used in reporting/dashboarding to sum up the number of customers in a filtered set.  
Country: The country of the customer’s primary residence.  
State: The state of the customer’s primary residence.  
City: The city of the customer’s primary residence.  
Zip Code: The zip code of the customer’s primary residence.  
Lat Long: The combined latitude and longitude of the customer’s primary residence.  
Latitude: The latitude of the customer’s primary residence.  
Longitude: The longitude of the customer’s primary residence.  

##### Population
ID: A unique ID that identifies each row.  
Zip Code: The zip code of the customer’s primary residence.  
Population: A current population estimate for the entire Zip Code area.  
 
##### Services
CustomerID: A unique ID that identifies each customer.  
Count: A value used in reporting/dashboarding to sum up the number of customers in a filtered set.  
Quarter: The fiscal quarter that the data has been derived from (e.g. Q3).  
Referred a Friend: Indicates if the customer has ever referred a friend or family member to this company: Yes, No  
Number of Referrals: Indicates the number of referrals to date that the customer has made.  
Tenure in Months: Indicates the total amount of months that the customer has been with the company by the end of the quarter specified above.  
Offer: Identifies the last marketing offer that the customer accepted, if applicable. Values include None, Offer A, Offer B, Offer C, Offer D, and Offer E.  
Phone Service: Indicates if the customer subscribes to home phone service with the company: Yes, No  
Avg Monthly Long Distance Charges: Indicates the customer’s average long distance charges, calculated to the end of the quarter specified above.  
Multiple Lines: Indicates if the customer subscribes to multiple telephone lines with the company: Yes, No  
Internet Service: Indicates if the customer subscribes to Internet service with the company: No, DSL, Fiber Optic, Cable.  
Avg Monthly GB Download: Indicates the customer’s average download volume in gigabytes, calculated to the end of the quarter specified above.  
Online Security: Indicates if the customer subscribes to an additional online security service provided by the company: Yes, No  
Online Backup: Indicates if the customer subscribes to an additional online backup service provided by the company: Yes, No  
Device Protection Plan: Indicates if the customer subscribes to an additional device protection plan for their Internet equipment provided by the company: Yes, No  
Premium Tech Support: Indicates if the customer subscribes to an additional technical support plan from the company with reduced wait times: Yes, No  
Streaming TV: Indicates if the customer uses their Internet service to stream television programing from a third party provider: Yes, No. The company does not charge an additional fee for this service.  
Streaming Movies: Indicates if the customer uses their Internet service to stream movies from a third party provider: Yes, No. The company does not charge an additional fee for this service.  
Streaming Music: Indicates if the customer uses their Internet service to stream music from a third party provider: Yes, No. The company does not charge an additional fee for this service.  
Unlimited Data: Indicates if the customer has paid an additional monthly fee to have unlimited data downloads/uploads: Yes, No  
Contract: Indicates the customer’s current contract type: Month-to-Month, One Year, Two Year.  
Paperless Billing: Indicates if the customer has chosen paperless billing: Yes, No  
Payment Method: Indicates how the customer pays their bill: Bank Withdrawal, Credit Card, Mailed Check  
Monthly Charge: Indicates the customer’s current total monthly charge for all their services from the company.  
Total Charges: Indicates the customer’s total charges, calculated to the end of the quarter specified above.  
Total Refunds: Indicates the customer’s total refunds, calculated to the end of the quarter specified above.  
Total Extra Data Charges: Indicates the customer’s total charges for extra data downloads above those specified in their plan, by the end of the quarter specified above.  
Total Long Distance Charges: Indicates the customer’s total charges for long distance above those specified in their plan, by the end of the quarter specified above.  

##### Status
CustomerID: A unique ID that identifies each customer.  
Count: A value used in reporting/dashboarding to sum up the number of customers in a filtered set.  
Quarter: The fiscal quarter that the data has been derived from (e.g. Q3).  
Satisfaction Score: A customer’s overall satisfaction rating of the company from 1 (Very Unsatisfied) to 5 (Very Satisfied).  
Satisfaction Score Label: Indicates the text version of the score (1-5) as a text string.  
Customer Status: Indicates the status of the customer at the end of the quarter: Churned, Stayed, or Joined  
Churn Label: Yes = the customer left the company this quarter. No = the customer remained with the company. Directly related to Churn Value.  
Churn Value: 1 = the customer left the company this quarter. 0 = the customer remained with the company. Directly related to Churn Label.  
Churn Score: A value from 0-100 that is calculated using the predictive tool IBM SPSS Modeler. The model incorporates multiple factors known to cause churn. The higher the score, the more likely the customer will churn.  
Churn Score Category: A calculation that assigns a Churn Score to one of the following categories: 0-10, 11-20, 21-30, 31-40, 41-50, 51-60, 61-70, 71-80, 81-90, and 91-100  
CLTV: Customer Lifetime Value. A predicted CLTV is calculated using corporate formulas and existing data. The higher the value, the more valuable the customer. High value customers should be monitored for churn.  
CLTV Category: A calculation that assigns a CLTV value to one of the following categories: 2000-2500, 2501-3000, 3001-3500, 3501-4000, 4001-4500, 4501-5000, 5001-5500, 5501-6000, 6001-6500, and 6501-7000.  
Churn Category: A high-level category for the customer’s reason for churning: Attitude, Competitor, Dissatisfaction, Other, Price. When they leave the company, all customers are asked about their reasons for leaving. Directly related to Churn Reason.  
Churn Reason: A customer’s specific reason for leaving the company. Directly related to Churn Category.  

Source: https://community.ibm.com/community/user/businessanalytics/blogs/steven-macko/2019/07/11/telco-customer-churn-1113

### Methodology
In order to create the best predictive model, 3 different classification models are build: Logistic Regression, K-Nearest Neighbors (KNN) and Support Vector Machines (SVM). GridSearchCV are used to chose the optimal parameters for the models. Only 10% is used for the test set since the dataset is big.

### Findings
Females and males seem to churn at about the same rate. Customers with monthly contracts and people with higher monthly charges seem to be more prone to leaving.  

Electronic checks is the most popular payment method for the customers of this company. Most people who have internet services do not enroll in device protection. Most people choose paperless billing.  

The top 5 churn reasons according to the customers by order of number of respondents:
1. Attitude of support person  
2. Competitor offered higher download speeds  
3. Competitor offered more data  
4. Don't know  
5. Competitor made better offer  

The logistic regression model is the best performing model in this case with an f-1 accuracy of 90% versus 85% and 89% for KNN and SVM respectively.