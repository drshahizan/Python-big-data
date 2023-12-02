## 🏥 Case Study 2 : Koalas Vs Pandas Library on Health Insurance Marketplace Dataset

![image](https://user-images.githubusercontent.com/99240177/212251329-77469daa-6e5a-464d-915d-a8cb4be0c674.png)

  
**Group Members:**

<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>AHMAD MUHAIMIN BIN AHMAD HAMBALI</th>
    <th>A20EC0006</th>
  </tr>
  <tr>
    <th>NAYLI NABIHAH BINTI JASNI</th>
    <th>A20EC0105</th>
  </tr>
    <tr>
    <th>SAKINAH AL’IZZAH BINTI MOHD ASRI</th>
    <th>A20EC0142</th>
  </tr>
    <tr>
    <th>LEE JIA XIAN</th>
    <th>A20EC0200</th>
  </tr>
</table> 


Koalas is a data science library that implements the pandas APIs on top of Apache Spark so that data scientists can use their favourite APIs on datasets of any size.The file will compare koalas and pandas to see which libraries are more efficient to use in the health insurance marketplace dataset. The following operations and visualisations will be used to perform the comparison:

  ● Comparison between read CSV

  ● Comparison between mean from one column

  ● Comparison between bar chart

  ● Comparison between counting of null values 

  ● Comparison between calculation of numerical data

  ● Comparison between histogram

## Dataset

The Health Insurance Marketplace Public Use Files contain information on health and dental plans available through the US Health Insurance Marketplace to individuals and small businesses. We chose rate.csv as our analysis datase from the combined csv file because it has the biggest file size (1.97 GB).

The dataset can be downloaded from Kaggle: <a href="https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv">Health Insurance Marketplace from Rate dataset</a>


The dataset we are using is the rate.csv file in the Health Insurance Marketplace Public Use Files from Kaggle: https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv.


&emsp;The rate.csv file is one of several CSV (comma-separated values) files that make up the Health Insurance Marketplace Public Use Files (PUF) dataset. The file contains information about the rates, or prices, of healthcare plans available on the individual market through the Health Insurance Marketplace also known as "Obamacare" marketplace. The dataset is collected by U.S Department of Health and Human Services (HHS) and provided by the Centers for Medicare & Medicaid Services (CMS)

&emsp;It provides detailed information about health plans, and pricing information available through the marketplace and its help researchers, consumer advocates, and policy makers to study and analyze trends in the individual health insurance market, understand the options, and costs associated with obtaining health coverage through the marketplace.

&emsp;It contains information about the different plans offered by insurance companies, including the type of coverage, deductibles, and out-of-pocket limits, and pricing information, such as monthly premiums, and financial assistance available to eligible individuals and families.

The rate.csv file contains the following columns:

  1. **BusinessYear**: The year of the plan
  2. **StateCode**: The code of the state where the plan is offered
  3. **IssuerId**: The unique identifier of the insurance company that offers the plan
  4. **SourceName**: The source of the rate information (e.g. the insurer, the state insurance department).
  5. **VersionNum**: A version number for the rate information.
  6. **ImportDate**: The date on which the rate information was imported into the Marketplace database.
  7. **PlanId**: Unique identifier of the plan
  8. **RatingAreaId**: The identifier of the geographic region where the rate applies
  9. **Tobacco**: Whether the rate applies to tobacco users or not
  10. **Age**: The age group for which the rate is specified
  11. **IndividualRate**: The monthly premium for an individual who selects the plan
  12. **IndividualTobaccoRate**: The monthly premium for an individual who selects the plan and uses tobacco
  13. **Couple**: The monthly premium for a couple who selects the plan
  14. **PrimarySubscriberAndOneDependent**: The monthly premium for a primary subscriber and one dependent who select the plan
  15. **PrimarySubscriberAndTwoDependents**: The monthly premium for a primary subscriber and two dependents who select the plan
  16. **PrimarySubscriberAndThreeOrMoreDependents**: The monthly premium for a primary subscriber and three or more dependents who select the plan
  17. **CoupleAndOneDependent**: The monthly premium for a couple and one dependent who select the plan
  18. **CoupleAndTwoDependents**: The monthly premium for a couple and two dependents who select the plan
  19. **CoupleAndThreeOrMoreDependents**: The monthly premium for a couple and three or more dependents who select the plan

Overall, the rate.csv dataset is an important resource that provides valuable information about the health insurance marketplace, which can be used to improve access to affordable health coverage for individuals and families.

