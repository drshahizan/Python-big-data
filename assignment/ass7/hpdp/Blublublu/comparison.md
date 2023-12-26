<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Assignment 7: Comparison between libraries

**Group Name: Blublublu**
|No.|NAME|MATRICS NO.|
|---|---|---|
|1.|ANG YI QIN|A20EC0163|
|2.|LAU YEE CHI|A21EC0042|
|3.|LIEW YVONNE|A21EC0045|
|4.|SOO WAN YING|A20EC0227|

## Table of Content
+ [Introduction](#introduction)
- [Dataset Selection](#dataset-selection)
- [Library Chosen](#library-chosen)
  - [Pandas](#pandas)
  - [DASK](#dask)
  - [Vaex](#vaex)
- [Comparison Between Libraries](#comparison-libraries)
  - [Installation of Libraries](#installation)
- [Conclusion](#conclusion)

## Introduction <a name = "introduction"></a>
In this project, we're exploring and analyzing the [Airline Delay Analysis](https://www.kaggle.com/datasets/sherrytp/airline-delay-analysis?select=airline+delay+analysis) dataset from Kaggle. This dataset contains a lot of information about airline flights, including dates, airlines, delays at departure and arrival, reasons for delays, and other operational details. Our main goal in this project is to use the pandas library, a powerful tool in Python for working with data, to thoroughly investigate and understand this airline delay dataset. The project aims to uncover insights into various facets of airline operations, including on-time performance, operational metrics, and delay resolution.

## Dataset Selection <a name = "dataset-selection"></a>
### **Airline Delay Analysis**

**Dataset used**: [Airline Delay Analysis](https://www.kaggle.com/datasets/sherrytp/airline-delay-analysis)

- The U.S. Department of Transportation's (DOT) Bureau of Transportation Statistics tracks the on-time performance of domestic flights operated by large air carriers. I came across this useful data from DOT's database at working and figured this would be a really helpful dataset: Summary information on the number of on-time, delayed, canceled, and diverted flight.
- The datasets contain daily airline information covering from flight information, carrier company, to taxing-in, taxing-out time, and generalized delay reason of exactly 10 years, from 2009 to 2019. The DOT's database is renewed from 2018, so there might be a minor change in the column names. In this assignment, we use dataset of flight information in **2018** to do EDA and visualization.
-The flight delay and cancellation data were collected and managed by the DOT's Bureau of Transportation Statistics, only included data related to time-analysis on each flight.

**Explanation of Columns of Dataset:**
| Column               | Explanation                                                                                       |
|----------------------|---------------------------------------------------------------------------------------------------|
| FL_DATE              | The date of the flight.                                                                           |
| OP_CARRIER           | The operating carrier or airline code.                                                            |
| ORIGIN               | The code for the origin airport.                                                                  |
| DEST                 | The code for the destination airport.                                                             |
| CRS_DEP_TIME         | The scheduled departure time.                                                                    |
| DEP_TIME             | The actual departure time.                                                                       |
| TAXI_OUT             | The time it takes for the aircraft to taxi from the departure gate to the runway.                  |
| WHEELS_OFF           | The time the aircraft's wheels leave the ground.                                                  |
| WHEELS_ON            | The time the aircraft's wheels touch the ground upon arrival.                                     |
| TAXI_IN              | The time it takes for the aircraft to taxi from the runway to the arrival gate.                    |
| ARR_DELAY            | Arrival delay, i.e., the difference between scheduled and actual arrival time.                    |
| CANCELLATION_CODE    | Code indicating the reason for flight cancellation.                                               |
| AIR_TIME             | The time the aircraft spends in the air.                                                          |
| CARRIER_DELAY        | Delay attributed to the airline.                                                                  |
| WEATHER_DELAY        | Delay attributed to weather conditions.                                                           |
| NAS_DELAY            | Delay attributed to the National Airspace System.                                                 |
| SECURITY_DELAY       | Delay attributed to security reasons.                                                             |
| LATE_AIRCRAFT_DELAY  | Delay attributed to a previous flight using the same aircraft arriving late.                      |
| STATUS               | The status of the flight.                                                                         |

## Library Chosen <a name = "library-chosen"></a>
This document presents an exploratory data analysis (EDA) on a dataset using three different libraries: Pandas, Dask, and Vaex. The goal is to compare the performance of these libraries in terms of time execution for typical EDA tasks.
### Pandas <a name = "pandas"></a>
1. Pandas:
- Description:
  - Pandas is a powerful and widely used data manipulation library for Python. It provides easy-to-use data structures, such as DataFrame, for handling and analyzing structured data.
  - It is built on top of NumPy and is designed to work seamlessly with other scientific computing libraries.

- Key Features:
  - DataFrame: A two-dimensional, tabular data structure with labeled axes (rows and columns).
  - Wide range of data manipulation and analysis functions.
  - Excellent support for handling missing data.
  - Integrates with other Python libraries for data visualization and analysis.

- Use Cases:
  - Data cleaning and preprocessing.
  - Exploratory Data Analysis (EDA).
  - Data visualization.

- Website: [Pandas](https://pandas.pydata.org/)


### DASK <a name = "dask"></a>
- Description:
  - Dask is a parallel computing library designed to enable parallel and distributed computing in Python. It extends the functionality of Pandas to handle larger-than-memory datasets.
  - Dask operates seamlessly with existing Python libraries and integrates well with Pandas, NumPy, and other scientific computing tools.

- Key Features:
  - Parallel and distributed computing: Enables scalable data processing on clusters.
  - Dask DataFrame: Mimics Pandas DataFrame but operates on larger-than-memory datasets.
  - Lazy evaluation: Delays computation until necessary, optimizing memory usage.
  - 
- Use Cases:
  - Scalable data processing for large datasets.
  - Parallel computing for complex tasks.
  - Handling out-of-memory computations.

- Website: [Dask](https://www.dask.org/)


### Vaex <a name = "vaex"></a>
- Description:
  - Vaex is a high-performance Python library designed for handling and analyzing large datasets. It is particularly focused on lazy, out-of-core computation to efficiently process data that doesn't fit into memory.
  - Vaex aims to provide a DataFrame-like interface while optimizing for performance.

- Key Features:
  - Memory-mapped storage: Efficiently handles large datasets without loading them entirely into memory.
  - Lazy evaluation: Delays computations until necessary for optimized performance.
  - Parallel processing: Utilizes multi-core systems for faster computations.

- Use Cases:
  - Analyzing and processing large datasets.
  - Handling big data efficiently.
  - High-performance computations with lazy evaluation.

- Website: [Vaex](https://vaex.io/)

## Comparison Between Libraries <a name = "comparison-libraries"></a>

### Installation of Libaries <a name = "installation"></a>
Library 1: **Pandas**
- Installing the Pandas package:
```
!pip install pandas
```

Library 2: **Dask**
- Installing the Dask package:
```
!pip install "dask[complete]"
```
- Importing the Dask library:
```
import dask.dataframe as dd
```
Library 3: **Vaex**
- Installing the Vaex package:
```
!pip install vaex
```
- Importing the Vaex library:
```
import vaex
```

## Conclusion <a name = "conclusion"></a>


## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

