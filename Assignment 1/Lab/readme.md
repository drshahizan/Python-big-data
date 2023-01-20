## 🥼Group Members : Lab

<table>

<tr>

  <th>Name</th>

  <th>Matric</th>

<tr>  

  <th>Nurarissa Dayana Binti Mohd Sukri</th>

  <th>A20EC0120</th>

 </tr>

 <tr>

   <th>Sakinah Al'izzah Binti Mohd Asri</th> 

   <th>A20EC0142</th>

 </tr>

 </table>
 
## Fraudulent Transaction Analysis and Prediction 💳

This file contains fraudulent transaction analysis. Fraudulent transaction is an unauthorized use of an individual's account or payment information by a third party to make a purchase or transfer funds without the individual's knowledge constitutes a fraudulent transaction. The victim of a fraudulent transaction may lose money, personal property, or personal information. This theft can have severe consequences that extend beyond monetary losses. This study will examine the fraudulent transaction data of a financial institution and provide insight into the findings.

## Dataset

Using the dataset, we develop a model for predicting fraudulent transactions at a financial institution and then create an actionable plan based on the model's insights. The case data is available in *CSV* format, with 11 columns and 6362620 rows. The file size is *493.53 MB*. The purpose of this study is to comprehend how financial fraud operates and how it can be prevented in the future.

The dataset is found from kaggle datasets: [Fraudulent Transactions Dataset](https://www.kaggle.com/datasets/chitwanmanchanda/fraudulent-transactions-data)

## Dataset Dictionary:

|Attribute|Description|
|:--------|:----------|
|`step`|maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation) |
|`type`|CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER |
|`amount`|amount of the transaction in local currency|
|`nameOrig`|customer who started the transaction|
|`oldbalanceOrg`|initial balance before the transaction|
|`newbalanceOrig`|new balance after the transaction|
|`nameDest`|customer who is the recipient of the transaction|
|`oldbalanceDest`|initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants)|
|`newbalanceDest`|new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants)|
|`isFraud`|This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system|
|`isFlaggedFraud`|The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction|
