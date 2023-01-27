# **Dataset: Airline Delay and Cancellation Data(2016 - 2018.csv)**
<img src="https://github.com/drshahizan/Python-big-data/blob/main/Project/BigMac/Pyspark.png"  width="320" height="100"><img src="https://github.com/drshahizan/Python-big-data/blob/main/Project/BigMac/vaex.png" width="320" height="100"><img src="https://github.com/drshahizan/Python-big-data/blob/main/Project/BigMac/koalas.png" width="320" height="100">


## _Group 3_
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Muhammad Imran Hakimi Bin Mohd Shukri </th>
    <th>A20EC0213</th>
  </tr>
  <tr>
    <th>Afif Hazmie Arsyad Bin Agus</th>
    <th>A20EC0176</th>
  </tr>
    <tr>
    <th>Kong Jia Rou</th>
    <th>A20EC0198</th>
  </tr>
    <tr>
    <th>Rasmin Kaur Sandhu</th>
    <th>A19ET0216</th>
  </tr>
</table>

---
**Introduction**
---
Welcome to our Python project where we will be comparing the use of three popular libraries: Koalas, PySpark, and Vaex. These libraries are widely used in the data science community for data manipulation and analysis. In this project, we will be exploring the strengths and limitations of each library by applying them to a specific dataset. Koalas is a powerful library that allows for easy data manipulation with a familiar pandas-like syntax. PySpark is a library that allows for efficient distributed data processing with the use of Spark. Finally, Vaex is a library that is known for its efficient handling of large datasets. Through this project, we will be comparing the performance and functionality of these libraries to see which one is the best fit for our specific use case. Let's dive in and see how these libraries compare!

---
## Dataset Information

For this project we decided to use a medical dataset [Airline.csv](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2014.csv). 

#### Attribute Information:
| Acronym | Description |
| --- | --- |
| **BusinessYear** |   The year for which the rate information applies.  |
|**StateCode** |  The two-letter code for the state in which the health insurance plan is offered.  |
| **IssuerId** | A unique identifier for the insurer offering the health insurance plan. |
| **SourceName** |  The source of the rate information (e.g. the insurer, the state insurance department). |
| **VersionNum** | A version number for the rate information.  |
| **ImportDate** |  The date on which the rate information was imported into the Marketplace database.   |
| **IssuerId2** | A unique identifier for the insurer offering the health insurance plan.  |
| **FederalTIN** | Federal income taxes  |
| **RateEffectiveDate** |  The date for which the rate information is effective.   |
|**RateExpirationDate** |  The expire date for the rate. |
| **PlanId** | A unique identifier for the health insurance plan. |
| **RatingAreaId** | The age of the insured person for which the rate information applies.  |
| **Tobacco** | The rate information applies to tobacco users or non-tobacco users. |
| **Age** |   The age of the insured person for which the rate information applies.  |
| **IndividualRate** |  The monthly premium (cost) for the health insurance plan for an individual.  |
| **IndividualTobaccoRate** | The monthly premium for the health insurance plan for an individual tobacco user.  |
| **Couple** | The monthly premium for the health insurance plan for a couple.  |
|**PrimarySubscriberAndOneDependent** |  The primary subscriber for the health insurance plan and one dependent. |
| **PrimarySubscriberAndTwoDependents** | The primary subscriber for the health insurance plan and two dependent. |
| **CoupleAndOneDependent** | The monthly premium for the health insurance plan for a couple and one dependent. |
| **CoupleAndTwoDependents** | The monthly premium for the health insurance plan for a couple and two dependents.  |
| **CoupleAndThreeOrMoreDependents** |  The monthly premium for the health insurance plan for a couple and three or more dependents.   |
| **RowNumber** | The row number of rate information.  |
