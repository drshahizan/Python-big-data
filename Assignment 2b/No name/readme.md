<h1>Data Table As An Alternative To Pandas (Pandas VS Datatable)</h1> 

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Pandas_logo.svg/2560px-Pandas_logo.svg.png" alt="Pandas" width="200"/>
VS
<img src="https://datatable.readthedocs.io/en/latest/_static/py_datatable_logo.png" alt="Datatable" width="200"/>

Python package datatable was inspired from its counterpart R package data.table. It was developped with the aim to analyse BigData efficiently. We have implemented the datatable solely [here](https://github.com/drshahizan/Python-big-data/tree/main/Assignment%202a/No%20name). 

### Purpose
Datatable is a go-to package for manipulating any large tabular datasets. It is widely used for fast aggregation of large datasets, low latency add/update/remove of columns, quicker ordered joins, and a fast file reader. The distribution provides compatibility and integration with the existing Pandas code. The sample code demonstrates how to perform some basic dataframe operations using Pandas and Datatable. This time, we would like to compare how efficient Data Table over Pandas in terms of handling with Big Data as it claims to be. We will compare the performance difference between the two libraries.

Dataset Source: https://www.kaggle.com/datasets/hhs/health-insurance-marketplace    
File: Rate.csv

## Group Members: 
<table align = "center">
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Madina Suraya binti Zharin</th>
    <th>A20EC0203</th>
  </tr>
  <tr>
    <th>Nur Izzah Mardhiah binti Rashidi</th>
    <th>A20EC0116</th>
  </tr>
    <tr>
    <th>Tan Yong Sheng</th>
    <th>A20EC0157</th>
  </tr>
    <tr>
    <th>Chloe Racquelmae Kennedy</th>
    <th>A20EC0026</th>
  </tr>
</table>

<h2>Installation</h2>
<code> !pip install datatable </code>
<br />
and continue by importing 
<br />
<code> import datatable as dt </code>

<h2>Content</h2>
DataTable-file2
- Implementing and comparing processing time of Data Table with Pandas



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

## Results

![image](https://user-images.githubusercontent.com/77196239/214785740-a1b6f52b-1057-44ab-92b1-e0d635626331.png)

- There are a few processes where DataTable execute faster than Pandas which are read data, printing dataframe, process dataframe time, getting unique values.

- Besides, there is a small difference in execution time for data filtering where DataTable is 8.11 µs while Pandas is 8.34 µs.

- The process with largest different in exection time would be looking for unique values for each columns where Pandas takes 8.34 µs while DataTable only takes 5.72 µs to process the result.

- The remaining processes all shows longer execution time for DataTable compared to Pandas. The longest execution time (10 µs) that DataTable took to process is to sort the data based on age in an increasing order.

<b><i>In conclusion, faster execution time indicates better performance. DataTable has better performance than Pandas in terms of reading data.</i></b>
