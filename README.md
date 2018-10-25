# Credit-card Default Risk
#### by Perry S.

### Problem Statement

   Given a dataset with demographic and borrowing history data for accounts classified as defaulting or not defaulting in October-2005, can I build a supervised model that performs better than identifying only members of the negative non-default class (baseline model) while minimizing the misclassification of either class?  In the context of credit-card lending, if I can predict accounts as belonging to the defaulting class, I want to also minimize the number of predicted defaulters who did not actually default that October (lost revenues) while minimizing the number of predicted non-defaulters who did end up defaulting (lost profits).
   
### Executive Summary

   I explored a widely-available dataset published in 2009 from research on defaults in the Taiwan credit-card lending market for this project.  I engineered two sets of monthly data for credit leverage and billing coverage, based on the credit-limit, billing and payments data provided for each of the six months prior to the defaulting observed in October-2005.  I trained five separate regression/decision-tree/machine-learning models using a portion of the dataset and tested the same on a held portion to validate the model performances. I looked at the top-three models more closely to determine which model might deliver the right balance of minimal misclassification, and in doing so highlighted the data-columns that were the strongest predictors of the default accounts.  I conclude that this classification-trees model will offer the optimal results if deployed in production to solve the default-classification problem stated above.
     
   
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


### Features Engineered


| New Features | Value | Description |
| --- | --- | --- |
| 'LIMIT_BAL' | (integer) | Credit limit |

### Feature Importances


| Order | LofReg Weightings | Weights |
| --- | --- | --- |
| 1 | Sep-History status | value |


| Order | CaRT Importances | Importances |
| --- | --- | --- |
| 1 | Sep-Billing | value

![Evaluation](https://git.generalassemb.ly/perry90034/credit/blob/master/cap_Pshyr/images/eval.jpg)

### Conclusion

   Of the best three models examined in detail, I found the Classification-Trees model to offer the best balance of minimizing the Miss and Fall-Out rates.  As a reult, this is the model that I recommend that you implement and deploy for production.