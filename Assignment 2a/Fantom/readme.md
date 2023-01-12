![cudf](https://user-images.githubusercontent.com/95162273/211054658-0eea8d0b-b508-4a74-beea-ac392bc9c090.png)

# Alternatives to Pandas for Processing Large Dataset - cuDF

## Group Member
1. LEE MING QI

2. NUR IRDINA ALIAH BINTI ABDUL WAHAB

3. SINGTHAI SRISOI

4. AMIRAH RAIHANAH BINTI ABDUL RAHIM

In this assignment, our group has explained about cuDF in two of the uploaded files.

- **File 1** : We are explaining the basic concept of cuDF, from installing to basic implementations. 

- **File 2** : We are comparing the functionality of cuDF with Pandas.

## cuDF
&emsp; **cuDF** is a Python library for working with data stored on a GPU (Graphics Processing Unit). It is designed to be used in conjunction with the NVIDIA RAPIDS ecosystem, which includes libraries for data processing, machine learning, and visualization on the GPU.

&emsp; cuDF provides many of the same features as Pandas, a popular library for data manipulation and analysis in Python, but is optimized for use on the GPU. This allows it to process large datasets much more quickly than Pandas, which is limited to running on the CPU.

Some of the main features of cuDF include:

* Reading and writing data in various formats (CSV, Parquet, JSON, etc.)
* Data cleaning and transformation tasks (e.g. handling missing values, merging and joining data)
* Statistical analysis and aggregation (e.g. computing mean, median, standard deviation)
* Grouping data
* Sorting and filtering data

&emsp; cuDF is an important tool for data scientists and analysts who need to work with large datasets and need fast, efficient data manipulation and analysis capabilities. It is particularly well-suited for tasks such as data wrangling, data preparation, and feature engineering, and can be an important part of a data-driven workflow.

## Dataset
&emsp; The dataset we are using is **Rate.csv (1.97 GB)**, which is accessible on Kaggle throught the link. https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv

&emsp; The dataset contains information on the rates for each health insurance plan offered through the Health Insurance Marketplace in the United States. The Marketplace is a platform that allows individuals and small businesses to shop for and compare health insurance plans, and is a key part of the Affordable Care Act (ACA).

The Rate.csv file includes the following columns:

* **BusinessYear**: The year for which the rate information applies.

* **StateCode**: The two-letter code for the state in which the health insurance plan is offered.

* **IssuerId**: A unique identifier for the insurer offering the health insurance plan.

* **SourceName**: The source of the rate information (e.g. the insurer, the state insurance department).

* **VersionNum**: A version number for the rate information.

* **ImportDate**: The date on which the rate information was imported into the Marketplace database.

* **PlanId**: A unique identifier for the health insurance plan.

* **StandardComponentId**: A unique identifier for the standard component of the health insurance plan.

* **RatingAreaId**: A unique identifier for the rating area (geographic region) in which the health insurance plan is offered.

* **Tobacco**: A flag indicating whether the rate information applies to tobacco users (1) or non-tobacco users (0).

* **Age**: The age of the insured person for which the rate information applies.

* **IndividualRate**: The monthly premium (cost) for the health insurance plan for an individual.

* **IndividualTobaccoRate**: The monthly premium for the health insurance plan for an individual tobacco user.

* **Couple**: The monthly premium for the health insurance plan for a couple.

* **CoupleAndOneDependent**: The monthly premium for the health insurance plan for a couple and one dependent.

* **CoupleAndTwoDependents**: The monthly premium for the health insurance plan for a couple and two dependents.

* **CoupleAndThreeOrMoreDependents**: The monthly premium for the health insurance plan for a couple and three or more dependents.

&emsp; This file can be useful for researchers and policymakers interested in studying trends in the health insurance market, as well as for individuals and small businesses looking for information on the health insurance plans available to them through the Marketplace.
