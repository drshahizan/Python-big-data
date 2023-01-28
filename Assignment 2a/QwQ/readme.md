<h1 align="center">
  <img src="https://raw.githubusercontent.com/pola-rs/polars-static/master/logos/polars_github_logo_rect_dark_name.svg">
  <br>
</h1>

<h1 align="center">
  Alternatives to Pandas for Processing Large Dataset - Polars
  <br>
</h1>


<h2 align="center">
  Group Members
  <br>
</h2>

<p align="center">
  <a>MUHAMMAD DINIE HAZIM BIN AZALI</a><br>
  <a>RADIN DAFINA BINTI RADIN ZULKAR NAIN</a><br>
  <a>ADRINA ASYIQIN BINTI MD ADHA</a><br>
  <a>KELVIN EE</a><br>
</p>

<h2 align="center">
  POLARS
  <br>
</h2>

<p align="center">
  <a>The polars library is a Python library for working with large, multi-dimensional datasets. It is designed to be fast, flexible, and easy to use.

  Some of the key features of the polars library include:

  - Support for various data formats: polars can read and write data from various formats such as CSV, JSON, HDF5, and others.

  - Integration with other libraries: polars can work seamlessly with other libraries such as numpy, pandas, and scikit-learn, making it easy to use existing tools and     libraries with polars data.

  - Data manipulation and transformation: polars provides a rich set of functions for manipulating and transforming data, including functions for grouping, filtering,     and aggregating data.

  - Data visualization: polars integrates with various data visualization libraries such as matplotlib, seaborn, and plotly, allowing you to easily create graphs and       plots from your data.

  - Data analysis: polars provides tools for performing various types of data analysis, including statistical analysis, machine learning, and more.

  Overall, the polars library is a powerful tool for working with large datasets in Python, and can be a useful addition to any data scientist's toolkit.</a>
</p> 


<h2>Installing Polars</h2>

Install the latest polars version with:

```sh
pip install polars
```
You can also have a conda package (`conda install polars`), however pip is the preferred way to install Polars.

<h2>
  About Dataset
  <br>
</h2>

For this project we decided to use a medical dataset [Rate.csv](https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv). 

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

<h2>Conclusion</h2>

In conclusion, we can definitely see that Polars is a very fast. If you need to do a lot of data processing on large datasets, you should definitely try Polars.

Future Work: 

   1. [Polars vs Pandas](https://github.com/drshahizan/Python-big-data/tree/main/Assignment%202b/QwQ)
    

