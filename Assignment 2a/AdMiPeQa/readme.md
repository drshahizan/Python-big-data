![image](https://user-images.githubusercontent.com/120556342/211182736-a99ae2f7-2f1c-488a-a388-9cb2efc2afa1.png)
# **Python Datatable library on Health Insurance Marketplace Dataset**
This assignment will explain about the basic concept of Datatable and code to code implementation.

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

## **Datatable**
Datatable is the premier package for manipulating large tabular datasets. Large datasets can be aggregated quickly, columns can be added/updated/removed with low latency, ordered joins can be made quickly, and file reading can be done quickly.<br><br>
Among the features we wish to implement with datatable are:
1. Fast data reading from CSV and other formats.
2. Efficient algorithms for sorting/grouping/joining.
3. Minimal amount of data copying, copy-on-write semantics for shared data.
4. Use "rowindex" views in filtering/sorting/grouping/joining operators to avoid unnecessary data copying.

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
