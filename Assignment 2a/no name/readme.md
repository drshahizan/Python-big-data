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

<h1>Data Table as an alternative to Pandas</h1>

![DataTable](https://datatable.readthedocs.io/en/latest/_static/py_datatable_logo.png)

Python package datatable was inspired from its counterpart R package data.table. It was developped with the aim to analyse BigData efficiently. Following is about datatable package.(Taken from datatable github page)

The set of features that we want to implement with datatable is at least the following:

- Column-oriented data storage.

- Native-C implementation for all datatypes, including strings. Packages such as pandas and numpy already do that for numeric columns, but not for strings.

- Support for date-time and categorical types. Object type is also supported, but promotion into object discouraged.

- All types should support null values, with as little overhead as possible.

- Data should be stored on disk in the same format as in memory. This will allow us to memory-map data on disk and work on out-of-memory datasets transparently.

- Work with memory-mapped datasets to avoid loading into memory more data than necessary for each particular operation.

- Fast data reading from CSV and other formats.

- Multi-threaded data processing: time-consuming operations should attempt to utilize all cores for maximum efficiency.

- Efficient algorithms for sorting/grouping/joining.

- Expressive query syntax (similar to data.table).

- LLVM-based lazy computation for complex queries (code generated, compiled and executed on-the-fly).
LLVM-based user-defined functions.

- Minimal amount of data copying, copy-on-write semantics for shared data.

- Use "rowindex" views in filtering/sorting/grouping/joining operators to avoid unnecessary data copying.

- Interoperability with pandas / numpy / pure python: the users should have the ability to convert to another data-processing framework with ease.

- Restrictions: Python 3.5+, 64-bit systems only.

<hr>

<h1>Installation</h1>
<code> !pip install datatable </code>
<br />
and continue by importing 
<br />
<code> import datatable as dt </code>

<hr>

<h1>Content</h1>
1. DataTable-file1
- Implementing the Data Table
<br />
2. DataTable-file2
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
