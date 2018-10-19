
# Capstone Base-directory
## Credit-card Lender Risk, by Perry Shyr

### Problem Statement

   I will build a supervised machine-learning model to predict the probability of default for 30,000 credit-card customers in Taiwan (Republic of China).  My positive class represents 22% of the sample dataset, which defaulted on their October-2005 bill.
   
### Executive Summary
   
   Credit-card lenders absorb significant losses from consumer defaults.  This capstone revolves around the detection of anomalies in customer demographic and borrowing history to identify credit-card default risk.  It is a binary classification problem with customers who default as the positive class, and unbalanced classes.  For supervised modeling, lenders are probably interested in not just the True-Positive (TP) rate, but also in the False-Negative (FN) and False-Positve (FP) rates. The best Estimator should minimize for both FN's and FP's while generalizing for TP's.
   
   
   Steps
   01.  Convert xls-file to csv.
   02.  Read csv-file as DataFrame, skipping the first row and setting the index as 'ID.
   03.  Exchange rate in 2009: NT$ 30 = USD 1
   04.  Unbalanced classes (78%:22%)
   05.  Education includes 0's (14), 5's (280) and 6's (51).
   06.  Clean Education by rolling 5's and 6's into "Other" and deleting 14 rows with "0".
   07.  Marriage includes "0" values
   08.  Deleted 54 rows.
   09.  Repayment-status 'PAY_0' range is inconsistent with data dictionary
   10.  Repayment-status 'PAY_2'
   11.  Repayment-status 'PAY_3'
   12.  Repayment-status 'PAY_4'
   13.  Repayment-status 'PAY_5'
   14.  Repayment-status 'PAY_6'
   15.  Rename 'default payment next month'-feature to 'Oct-Default'
   16.    REVERSE(>>>Roll "0" values for payment history with "1" values.<<<)
   17.  Need legend on plot.
   18.  Remove duplicate rows
   19.  E-mailed author of paper, confirms expanded dictionary
   20.  No history values of "9 months or more"
   21.
   22.
   23.
   
   
### Research

Exchange Rate in 2005 is about NT$ 33.15 : US$ 1.00 (sell) or NT$ 1.00 : US$ 0.0302 (buy).
(https://www.xe.com/currencytables/?from=USD&date=2005-10-01)

   
e-mail: 140910@mail.tku.edu.tw
Prof. I-Cheng Yeh
Department of Civil Engineering
Tamkang University,


   
### Report Contents

| Notebook | Description |
| --- | --- |
| 1 | Data-exploration |
| 2 | Modeling |
| 3 | Evaluation |


### Data Dictionary   
   
| Feature | Value | Description |
| --- | --- | --- |
| 'LIMIT_BAL' | (integer) | Credit limit |
| Gender | 1 | Male |
| Gender | 2 | Female |
| Education-level | 0 | ? |
| Education-level | 1 | Graduate school |
| Education-level | 2 | College |
| Education-level | 3 | High school |
| Education-level | 4 | Other |
| Education-level | 5 | ? |
| Education-level | 6 | ? |
| Marital-status | 0 | ? |
| Marital-status | 1 | Married |
| Marital-status | 2 | Single |
| Marital-status | 3 | Other |
| 'AGE' | (integer) | 21 to 79 |
| Repayment-status ('PAY_#') | -2 | ? |
| Repayment-status ('PAY_#') | -1 | Current |
| Repayment-status ('PAY_#') | 0 | ? |
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



### Conclusion

