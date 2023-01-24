<h1 align="center">
  <img src="https://user-images.githubusercontent.com/120556342/211182736-a99ae2f7-2f1c-488a-a388-9cb2efc2afa1.png">
  <br>
</h1>
<h1>
Pandas vs Datatable on Health Insurance Marketplace Dataset🏥</h1>
This assignment will show the comparison between Pandas and Datatable in performing various operations and the visualization about the comparison will be shown. 

## **Group Members**
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>ADAM WAFII BIN AZUAR</th>
    <th>A20EC0003</th>
  </tr>
  <tr>
    <th>HONG PEI GEOK</th>
    <th>A20EC0044</th>
  </tr>
    <tr>
    <th>MIKHEL ADAM BIN MUHAMMAD EZRIN</th>
    <th>A20EC0237</th>
  </tr>
    <tr>
    <th>QAISARA BINTI ROHZAN</th>
    <th>A20EC0133</th>
  </tr>
</table>

## **About Datatable**
Datatable is the premier package for manipulating large tabular datasets. Large datasets can be aggregated quickly, columns can be added/updated/removed with low latency, ordered joins can be made quickly, and file reading can be done quickly.<br><br>
Among the features we wish to compare pandas with datatable are:
1. Read file
2. Compute metrics of a column
3. Find unique count of a column
4. Groupby Aggregation
5. Sorting

## **About Pandas**
Pandas is a popular library in Python for data manipulation and analysis. It provides data structures such as Series (1-dimensional) and DataFrame (2-dimensional) that allow you to manipulate and analyze data in a similar way to a spreadsheet. It also has functions for handling missing data, reading and writing data to different file formats, and merging, grouping, and reshaping data. Pandas is widely used in data science and is a powerful tool for working with structured data. Let me know if you have any specific questions about using pandas.
1. Read File
2. Sorting
3. Description

## *Conclusion*
We can concluded that datatable is way more faster compared to pandas in doing these tasks. Pandas can be quite slow when working with large datasets, especially when using certain operations such as groupby or pivot tables. While datatable, on the other hand, is a newer library that was specifically designed for performance and handling large datasets. It uses a different data structure (a multi-dimensional array) and a unique data processing engine to improve performance. It also has a similar syntax and functionality to pandas, making it easy to learn for users already familiar with pandas. In summary, eventhough the dataset we are using is cannot be considered as a large dataset we still believe that datatable may be a better choice. On the other hand, if we need a wide range of data manipulation and analysis functionality, pandas may be more suitable. All in all it always depends on our objectives for the datatset.


## **Dataset**
The dataset can be downloaded from Kaggle: <a href="https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv">Rate.csv</a>
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
