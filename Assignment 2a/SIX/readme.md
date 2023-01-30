![cudf](https://user-images.githubusercontent.com/95162273/211054658-0eea8d0b-b508-4a74-beea-ac392bc9c090.png)

# Alternatives to Pandas for Processing Large Dataset - cuDF

| Name | Matric Number |
| ----- | ----- |
| LEE MING QI | A20EC0064|
| NUR IRDINA ALIAH BINTI ABDUL WAHAB |A20EC0115 |
| SINGTHAI SRISOI| A20EC0147|
| AMIRAH RAIHANAH BINTI ABDUL RAHIM |A20EC0182 |

In this assignment, we will explain the basic concept of cuDF, from installing to basic implementations. We also perform data operations for a better understanding on the library.

## cuDF
**cuDF** is a Python library for working with data stored on a GPU (Graphics Processing Unit). It is designed to be used in conjunction with the NVIDIA RAPIDS ecosystem, which includes libraries for data processing, machine learning, and visualization on the GPU.
cuDF provides many of the same features as Pandas, a popular library for data manipulation and analysis in Python, but is optimized for use on the GPU. This allows it to process large datasets much more quickly than Pandas, which is limited to running on the CPU.

Some of the main features of cuDF include:

* Reading and writing data in various formats (CSV, Parquet, JSON, etc.)
* Data cleaning and transformation tasks (e.g. handling missing values, merging and joining data)
* Statistical analysis and aggregation (e.g. computing mean, median, standard deviation)
* Grouping data
* Sorting and filtering data

cuDF is an important tool for data scientists and analysts who need to work with large datasets and need fast, efficient data manipulation and analysis capabilities. It is particularly well-suited for tasks such as data wrangling, data preparation, and feature engineering, and can be an important part of a data-driven workflow.

## Dataset
&emsp; The dataset we are using is **Rate.csv (1.97 GB)**, which is accessible on Kaggle throught the link. https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv

The dataset contains information on the rates for each health insurance plan offered through the Health Insurance Marketplace in the United States. The Marketplace is a platform that allows individuals and small businesses to shop for and compare health insurance plans, and is a key part of the Affordable Care Act (ACA).

The Rate.csv file includes the following columns:

#### Attribute Information:
| Attributes | Description |
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

--
## Conclusion
cuDF is a powerful library for data manipulation and analysis that is designed to work with data stored on the GPU. It provides many of the same features as Pandas, including the ability to read and write data in various formats, perform data cleaning and transformation tasks, and perform statistical analysis.
One of the main benefits of cuDF is its ability to process large datasets in parallel on the GPU, which can lead to significantly faster performance compared to Pandas and other CPU-based data manipulation libraries. This makes it an excellent choice for working with large datasets that are too large to fit in memory on a single CPU.
Overall, cuDF is a valuable tool for data scientists and analysts who need to work with large datasets and need fast, efficient data manipulation and analysis capabilities. It is particularly well-suited for tasks such as data wrangling, data preparation, and feature engineering, and can be an important part of a data-driven workflow.
