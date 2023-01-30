# Fraud Detection
Group Members:
1. Amirah Raihanah Binti Abdul Rahim (A20EC0182)
2. Myza Nazifa Binti Nazry (A20EC0219)

For this assignment we have chosen a big data set about Fraud Detection from online transaction. This dataset will detect either the transaction is fraud or not by analyzing the before and after transaction balance.From this data, we will able to detect the amount of fraud, the name of the customer and their balance. To achieve that, data prepping, analysing, visualization, question and answers have been compiled in this file for better understanding. To complete this EDA, there are multiple library used such as Pandas, Matplotlib, seaborn and plotly express.

The dataset size is 186MB and is downloaded from Kaggle. Below attached link to the source dataset;
https://www.kaggle.com/datasets/rupakroy/online-payments-fraud-detection-dataset

---

Attribute Information:

| Attribute | Description |
| --- | --- |
| **step** |    represents a unit of time where 1 step equals 1 hour |
|**type** |   type of online transaction |
| **amount** | the amount of the transaction |
| **nameOrig** |  customer starting the transaction |
| **oldbalanceOrg** |  balance before the transaction |
| **nameDest** |    recipient of the transaction |
| **oldbalanceDest** |   initial balance of 9. recipient before the transaction |
| **newbalanceDest** |   the new balance of recipient after the transaction |
|**isFraud** |   fraud transaction |

For this dataset, we further our investigation based on these questions;
1. Who are the top 10 richest customer who had the biggest lost from the fraud?
2.  Who are the top 10 richest recipient who had biggest gain when fraud occured?
3.  Which customer lost the most money
4.  Top 20 step number that fraud occured
5.  Which customer commit the largest fraud?
---
### Conclusion
1. The top 2 types of transaction that causes fraud is 'cash_out' and 'payment'.
2. The largest amount transferred is made by 'transfer' transaction type. This means that the largest amount of fraud is made by 'transfer'.
3. The biggest loss from fraud is $21182.00
4. The largest gain from fraud is $10000000.00
