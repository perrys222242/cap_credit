# Credit-card Default Risk
#### by Perry S.

### Problem Statement

   Given a dataset with demographic and borrowing history data for accounts classified as defaulting or not defaulting in October-2005, can I build a supervised model that performs better than identifying only members of the negative non-default class (baseline model) while minimizing the misclassification of either class?  In the context of credit-card lending, if I can predict accounts as belonging to the defaulting class, I want to also minimize the number of predicted defaulters who did not actually default that October (lost revenues) while minimizing the number of predicted non-defaulters who did end up defaulting (lost profits).
   
### Executive Summary

   I explored a widely-available dataset published in 2009 from research on defaults in the Taiwan credit-card lending market for this project.  I engineered two sets of monthly data for credit leverage and billing coverage, based on the credit-limit, billing and payments data provided for each of the six months prior to the defaulting observed in October-2005.  I trained five separate regression/decision-tree/machine-learning models using a portion of the dataset and tested the same on a held portion to validate the model performances. None of the models scored appreciably better than the baseline model.  I looked at the top-three models more closely to determine which model might deliver the right balance of minimal misclassification, and in doing so highlighted the data-columns that were the strongest predictors of the default accounts.  I conclude that this classification-trees model will offer the optimal results if deployed in production to solve the default-classification problem stated above.
     
   
### Research

Exchange Rate in 2005 is about NT$ 33.15 : US$ 1.00 (sell) or NT$ 1.00 : US$ 0.0302 (buy).
(https://www.xe.com/currencytables/?from=USD&date=2005-10-01)
  
e-mail: 140910@mail.tku.edu.tw
Prof. I-Cheng Yeh
Department of Civil Engineering
Tamkang University,

Actual default rate in Taiwan is about 3.6% of total accounts.
(https://pdfs.semanticscholar.org/38b2/a5ebd02be4b2c32ade85445acf4b49fb198c.pdf)

   
### Report Contents

This technical report is divided into seven notebooks with the following topics:

| Notebook | Description |
| --- | --- |
| 1 | Preprocessing |
| 2 | Data Exploration |
| 3 | Feature Engineering |
| 4 | Modeling: Neural-networks, Keras-Front-end |
| 5 | Modeling: Neural-networks, TensorFlow |
| 6 | Modeling: Other Classifiers |
| 7 | Evaluation |


### Updated Data Dictionary   
   
| Feature | Value | Description |
| --- | --- | --- |
| 'LIMIT_BAL' | (integer) | Credit limit |
| Gender | 1 | Male |
| Gender | 2 | Female |
| Education-level | 1 | Graduate school |
| Education-level | 2 | College |
| Education-level | 3 | High school |
| Education-level | 4 | Other |
| Marital-status | 0 | Other |
| Marital-status | 1 | Married |
| Marital-status | 2 | Single |
| Marital-status | 3 | Divorced |
| 'AGE' | (integer) | 21 to 79 |
| Repayment-status ('PAY_#') | -2 | No consumption  |
| Repayment-status ('PAY_#') | -1 | Paid in full |
| Repayment-status ('PAY_#') | 0 | Use of revolving credit |
| Repayment-status ('PAY_#') | 1 | Late 1 month |
| Repayment-status ('PAY_#') | 2 | Late 2 months |
| Repayment-status ('PAY_#') | 3 | Late 3 months |
| Repayment-status ('PAY_#') | 4 | Late 4 months |
| Repayment-status ('PAY_#') | 5 | Late 5 months |
| Repayment-status ('PAY_#') | 6 | Late 6 months |
| Repayment-status ('PAY_#') | 7 | Late 7 months |
| Repayment-status ('PAY_#') | 8 | Late 8 months (or more?) |
| 'BILL_AMT#' | (integer) | Previous monthly bills |
| 'PAY_AMT#' | (integer) | Previous monthly payments |
| 'default payment next month' | 0 | False |
| 'default payment next month' | 1 | True |


### Findings

(a) 35 duplicate rows found and dropped.
(b) Although "gender," 'EDUCATION' and 'MARRIAGE' are numeric columns, their discrete values should be encoded into separate features.


### Features Engineered


| New Features | Description |
| --- | --- |
| 'leverage_#' | Ratio of monthly billing-amount to credit-limit |
| 'bill_to_pay#' | Ratio of monthly billing-amount to monthly payment-amount |


### Top Feature Importances/Weights


| Order | LofReg Weightings | Weights |
| --- | --- | --- |
| 1 | Sep-Payment status | 0.6 |
| 2 | Sep-Bill/Payment | 0.2 |
| 3 | Aug-Bill/Limit | 0.16 |
| 40 | Credit limit | -0.17 |
| 41 | Sep-Payment amount | -0.23 |
| 42 | Sep-Bill/Limit | -0.32 |


| Order | CaRT Importances | Importances |
| --- | --- | --- |
| 1 | Aug-Bill-amount | 0.016
| 2 | Credit limit | 0.015
| 3 | Sep-Payment-amount | 0.0122
| 4 | Sep-Bill-amount | 0.0120
| 5 | Jul-Payment-amount | 0.011


### Comparing the Top-3 Models

![Evaluation](https://git.generalassemb.ly/perry90034/credit/blob/master/cap_Pshyr/images/eval.jpg)

For this anomaly-detection problem, we are not so much wanting to know how much more accurate a model is at classifying default-prone accounts because none of the top models performs significantly better than the baseline model.  We are more interested in the balance between minimizing false-negatives (actual losses) and minimizing false-positives (lost business).  Such comparison of the three models above suggests that the Classification-Trees models offers a better balance than either the neural-networks and logistic-regression models.


### Conclusion

   My problem statement asked if I can predict credit-card accounts that would default while controlling for the two types of misclassifications. Although none of my models scored appreciably better than the baseline model, I believe that using a Classification-Trees model offers the best results. The dataset is clearly unbalanced and with the Default class as the minority, our preferred model delivered a 57.4% True-Positive rate which is a significantly better result than our baseline model which predicts only Non-Defaults. The top feature importances for the Classification-Trees model were associated with the Payment-history, Payment-amounts and August-September-related features. This confirms that it trained well for falling average payments leading up to the defaults in the October period, which suggests increasing financial strain on accountholders.