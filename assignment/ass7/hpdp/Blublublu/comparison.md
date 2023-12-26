<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Assignment 7: Comparison between libraries

**Group Name: Blublublu**
|NO.|NAME|MATRICS NO.|LIBRARY|
|---|---|---|---|
|1.|ANG YI QIN|A21EC0163| Dask|
|2.|LAU YEE CHI|A21EC0042|Dask|
|3.|LIEW YVONNE|A21EC0045|Vaex|
|4.|SOO WAN YING|A21EC0227|Pandas|

## Table of Content
+ [1.0 Introduction](#1-introduction)
+ [2.0 Dataset Selection](#2-dataset-selection)
+ [3.0 Library Chosen](#3-library-chosen)
  + [3.1 Pandas](#31-pandas)
  + [3.2 Dask](#32-dask)
  + [3.3 Vaex](#33-vaex)
+ [4.0 Comparison Between Libraries](#4-comparison-between-libraries)
  + [4.1 Installation of Libraries](#41-installation)
  + [4.2 Dataset Loading](#42-loading)
  + [4.3 Explore Dataset](#43-explore)
    + [4.3.1 Check the Datatypes](#431-check-the-datatypes)
    + [4.3.2 Display the first 10 rows of the dataset](#432-display-the-first-10-rows-of-the-dataset)
    + [4.3.3 Obtain Description of the Dataset](#433-obtain-description-of-the-dataset)
    + [4.3.4 Obtain Information of the Dataset](#434-obtain-information-of-the-dataset)
    + [4.3.5 Check Missing Data](#435-check-missing-data)
    + [4.3.6 Identifying Multicollinearity and Variable Selection](#436-identifying-multicollinearity-and-variable-selection)
    + [4.3.7 Converting the 'FL_DATE' Column to Datetime Format](#437-converting-column-to-datetime-format)
    + [4.3.8 Return Number of Rows](#438-return-number-of-rows)
    + [4.3.9 Create a New Column to Represent the Status of the Flight](#439-create-a-new-column)
    + [4.3.10 Drop Unnecessary Column](#4310-drop-unnecessary-column)
    + [4.3.11 Display First 20 Rows of the Dataset](#4311-display-first-20-rows)
+ [5.0 Exploratory Analysis and Visualization](#5-eda)
+ [6.0 Asking and Answering Questions](#6-asking-answering)
+ [7.0 Conclusion](#conclusion)

## Introduction <a name = "1-introduction"></a>
In this project, we're exploring and analyzing the [Airline Delay Analysis](https://www.kaggle.com/datasets/sherrytp/airline-delay-analysis?select=airline+delay+analysis) dataset from Kaggle. This dataset contains a lot of information about airline flights, including dates, airlines, delays at departure and arrival, reasons for delays, and other operational details. Our main goal in this project is to use the pandas library, a powerful tool in Python for working with data, to thoroughly investigate and understand this airline delay dataset. The project aims to uncover insights into various facets of airline operations, including on-time performance, operational metrics, and delay resolution.

## 2.0 Dataset Selection <a name = "2-dataset-selection"></a>
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

## 3.0 Library Chosen <a name = "3-library-chosen"></a>
This document presents an exploratory data analysis (EDA) on a dataset using three different libraries: Pandas, Dask, and Vaex. The goal is to compare the performance of these libraries in terms of time execution for typical EDA tasks.
### 3.1 Pandas <a name = "31-pandas"></a>
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


### 3.2 Dask <a name = "32-dask"></a>
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


### 3.3 Vaex <a name = "33-vaex"></a>
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

## 4.0 Comparison Between Libraries <a name = "4-comparison-between-libraries"></a>

### 4.1 Installation of Libraries <a name = "41-installation"></a>
Library 1: **Pandas**
- Installing the Pandas package:
```ruby
!pip install pandas
```

Library 2: **Dask**
- Installing the Dask package:
```ruby
!pip install "dask[complete]"
```
- Importing the Dask library:
```ruby
import dask.dataframe as dd
```

Library 3: **Vaex**
- Installing the Vaex package:
```ruby
!pip install vaex
```
- Importing the Vaex library:
```ruby
import vaex
```

### 4.2 Dataset Loading <a name = "42-loading"></a>
Library 1: **Pandas**
```ruby
from google.colab import files

# Load the dataset
file_path = '/content/airline-delay-analysis/airline delay analysis/2018.csv'
df = pd.read_csv(file_path, encoding='ISO-8859-1')
```
Time Consumed: 50.2s

Library 2: **Dask**
```ruby
import dask.dataframe as dd
import opendatasets as od

# Download the dataset
od.download("https://www.kaggle.com/datasets/sherrytp/airline-delay-analysis")

# Specify the file path
file_path = "/content/airline-delay-analysis/airline delay analysis/2018.csv"

# Specify dtype for the problematic column
dtype_spec = {'CANCELLATION_CODE': 'object'}

# Read the CSV file with dtype specification
ddf = dd.read_csv(file_path, dtype=dtype_spec)
```
Time Consumed: 2min 12s

Library 3: **Vaex**
```ruby
df = vaex.from_csv('airline delay analysis/2018.csv', convert=True)
```
Time Consumed: 108 ms

### 4.3 Explore Dataset <a name = "43-explore"></a>
#### 4.3.1 Check the Datatypes <a name = "431-check-the-datatypes"></a>
Library 1: **Pandas**
```ruby
df.dtypes
```
Time Consumed: 321 µs

Library 2: **Dask**
```ruby
ddf.dtypes
```
Time Consumed: 307 µs

Library 3: **Vaex**
```ruby
# Check the datatypes
df.dtypes
```
Time Consumed: 1.85 ms

#### 4.3.2 Display the first 10 rows of the dataset <a name = "432-display-the-first-10-rows-of-the-dataset"></a>
Library 1: **Pandas**
```ruby
df.head(10)
```
Time Consumed: 158 µs

Library 2: **Dask**
```ruby
first_10_rows = ddf.head(10)
print(first_10_rows)
```
Time Consumed: 3.28 s

Library 3: **Vaex**
```ruby 
df.head(10)
```
Time Consumed: 2.82 ms

#### 4.3.3 Obtain Description of the Dataset <a name = "433-obtain-description-of-the-dataset"></a>
Library 1: **Pandas**
```ruby
df.describe()
```
Time Consumed: 6.23 s

Library 2: **Dask**
```ruby
ddf.describe().compute()
```
Time Consumed: 44.8 s

Library 3: **Vaex**
```ruby
df.describe()
```
Time Consumed: 9.52 s

#### 4.3.4 Obtain Information of the Dataset <a name = "434-obtain-information-of-the-dataset"></a>
Library 1: **Pandas**
```ruby
df.info()
```
Time Consumed: 50.7 ms

Library 2: **Dask**
```ruby
ddf.info()
```
Time Consumed: 2.63 ms

Library 3: **Vaex**
```ruby
df.info()
```
Time Consumed: 32.5 ms

#### 4.3.5 Check Missing Data <a name = "435-check-missing-data"></a>
Library 1: **Pandas**
```ruby
df.isna().sum()
```
Time Consumed: 11.7 s

Library 2: **Dask**
```ruby
ddf.isna().sum().compute()
```
Time Consumed: 27.7 s

Library 3: **Vaex**
```ruby
count_na = []  # to count the missing value per column
for col in df.column_names:
    count_na.append(df[col].isna().sum().item())

s = pd.Series(data=count_na, index=df.column_names).sort_values(ascending=True)
s
```
Time Consumed: 1.7 s

#### 4.3.6 Identifying Multicollinearity and Variable Selection <a name = "436-identifying-multicollinearity-and-variable-selection"></a>
Library 1: **Pandas**
```ruby
import matplotlib.pyplot as plt
import seaborn as sns

corrmat = df.corr()
f, ax = plt.subplots(figsize=(12, 9))
sns.heatmap(corrmat, vmax=.8, square=True, xticklabels=corrmat.columns, yticklabels=corrmat.columns)
plt.show()
```
Time Consumed: 10.04 s

Library 2: **Dask**
```ruby
import matplotlib.pyplot as plt
import seaborn as sns
corrmat = ddf.corr()
f, ax = plt.subplots(figsize=(12, 9))
sns.heatmap(corrmat, vmax=.8, square=True, xticklabels=corrmat.columns, yticklabels=corrmat.columns);
plt.show()
```
Time Consumed: 1min 49s

Library 3: **Vaex**
```ruby
import matplotlib.pyplot as plt
import seaborn as sns

corrmat = df.to_pandas_df().corr()
f, ax = plt.subplots(figsize=(12, 9))
sns.heatmap(corrmat, vmax=.8, square=True, xticklabels=corrmat.columns, yticklabels=corrmat.columns)
plt.show()
```
Time Consumed: 34.8 s

#### 4.3.7 Converting the 'FL_DATE' Column to Datetime Format <a name = "437-converting-column-to-datetime-format"></a>
Library 1: **Pandas**
```ruby
df['FL_DATE'] = pd.to_datetime(df['FL_DATE'])
df.dtypes
```
Time Consumed: 594 ms

Library 2: **Dask**
```ruby
ddf['FL_DATE'] = ddf['FL_DATE'].astype('datetime64[ns]')
ddf.dtypes
```
Time Consumed: 11.4 ms

Library 3: **Vaex**
```ruby
df['FL_DATE'] = df['FL_DATE'].astype('datetime64[ns]')
df.dtypes
```
Time Consumed: 57.1 ms

#### 4.3.8 Return Number of Rows <a name = "438-return-number-of-rows"></a>
Library 1: **Pandas**
```ruby
len(df)
```
Time Consumed: 28.6 µs

Library 2: **Dask**
```ruby
ddf.shape[0].compute()
```
Time Consumed: 24 s

Library 3: **Vaex**
```ruby
len(df)
```
Time Consumed: 219 µs

#### 4.3.9 Create a New Column to Represent the Status of the Flight <a name = "439-create-a-new-column"></a>
Library 1: **Pandas**
```ruby
df['STATUS'] =df['ARR_DELAY'].apply(lambda x: 0 if x <= 15 else 1 if x <= 30 else 2 if x <= 60 else 3 if x <= 120 else 4)
```
Time Consumed: 1.99 s

Library 2: **Dask**
```ruby
ddf['STATUS'] = ddf['ARR_DELAY'].apply(lambda x: 0 if x <= 15 else 1 if x <= 30 else 2 if x <= 60 else 3 if x <= 120 else 4)
```
Time Consumed: 95.2 ms

Library 3: **Vaex**
```ruby
df['STATUS'] =df['ARR_DELAY'].apply(lambda x: 0 if x <= 15 else 1 if x <= 30 else 2 if x <= 60 else 3 if x <= 120 else 4)
```
Time Consumed: 736 µs

#### 4.3.10 Drop Unnecessary Column <a name = "4310-drop-unnecessary-column"></a>
Library 1: **Pandas**
```ruby
df = df.drop(columns=['DEP_DELAY', 'ARR_TIME','CRS_ARR_TIME', 'ACTUAL_ELAPSED_TIME', 'CRS_ELAPSED_TIME', 'DIVERTED','CANCELLED','DISTANCE','OP_CARRIER_FL_NUM','Unnamed: 27'])
```
Time Consumed: 231 ms

Library 2: **Dask**
```ruby
ddf = ddf.drop("DEP_DELAY",1)
ddf = ddf.drop("ARR_TIME",1)
ddf = ddf.drop("CRS_ARR_TIME",1)
ddf = ddf.drop("ACTUAL_ELAPSED_TIME",1)
ddf = ddf.drop("CRS_ELAPSED_TIME",1)
ddf = ddf.drop("DIVERTED",1)
ddf = ddf.drop("CANCELLED",1)
ddf = ddf.drop("DISTANCE",1)
ddf = ddf.drop("OP_CARRIER_FL_NUM",1)
ddf = ddf.drop("Unnamed: 27",1) #Empty
```
Time Consumed:  234 ms

Library 3: **Vaex**
```ruby
columns_to_drop = ['ARR_TIME', 'DEP_DELAY','CRS_ARR_TIME', 'ACTUAL_ELAPSED_TIME', 'CRS_ELAPSED_TIME', 'DIVERTED', 'CANCELLED', 'DISTANCE', 'OP_CARRIER_FL_NUM', 'Unnamed: 27']
df = df.drop(columns_to_drop)
```
Time Consumed: 6.3 ms

#### 4.3.11 Display First 20 Rows of the Dataset <a name = "4311-display-first-20-rows"></a>
Library 1: **Pandas**
```ruby
df.head(20)
```
Time Consumed: 282 µs

Library 2: **Dask**
```ruby
ddf.head(20)
```
Time Consumed: 3.01 s

Library 3: **Vaex**
```ruby
df.head(20)
```
Time Consumed: 1.71 ms

### 5.0 Exploratory Analysis and Visualization <a name = "5-eda"></a>
#### 1. Summarize the flights - We will see the percentage of flights that have delayed and cancelled.
Library 1: **Pandas**
```ruby
# Create a DataFrame with 'STATUS' column
status_df = pd.DataFrame(df['STATUS'])

# Plotting Pie Chart
plt.figure(figsize=(16, 8))
plt.subplot(1, 2, 1)
status_counts = status_df['STATUS'].value_counts()
status_counts.plot.pie(
    explode=[0.05, 0.05, 0.05, 0, 0],
    autopct='%1.1f%%',
    shadow=True
)
plt.title('Flight Status Distribution')
plt.ylabel('')

# Plotting Bar Chart
plt.subplot(1, 2, 2)
status_counts.plot.bar(figsize=(16, 8))
plt.title('Flight Status Distribution')

plt.show()

print('Status represents whether the flight was on time (0), slightly delayed (1), highly delayed (2), diverted (3), or cancelled (4)')
```
Time Consumed: 446 ms

Library 2: **Dask**
```ruby
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
f,ax=plt.subplots(1,2,figsize=(50,30))
pd.DataFrame(ddf['STATUS']).value_counts().plot.pie(explode=[0.05,0.05,0.05,0,0],autopct='%1.1f%%',ax=ax[0],shadow=True)
ax[0].set_title('Status')
ax[0].set_ylabel('')
pd.DataFrame(ddf['STATUS']).value_counts().plot.bar(figsize=(8,6), ax=ax[1])
ax[1].set_title('Status')
plt.show()

print('Status represents wether the flight was on time (0), slightly delayed (1), highly delayed (2), diverted (3), or cancelled (4)')
```
Time Consumed: 1min 10s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Create a DataFrame with 'STATUS' column
status_df = pd.DataFrame(pandas_df['STATUS'])

# Plotting Pie Chart
plt.figure(figsize=(16, 8))
plt.subplot(1, 2, 1)
status_counts = status_df['STATUS'].value_counts()
status_counts.plot.pie(
    explode=[0.05, 0.05, 0.05, 0, 0],
    autopct='%1.1f%%',
    shadow=True
)
plt.title('Flight Status Distribution')
plt.ylabel('')

# Plotting Bar Chart
plt.subplot(1, 2, 2)
status_counts.plot.bar(figsize=(16, 8))
plt.title('Flight Status Distribution')

plt.show()

print('Status represents whether the flight was on time (0), slightly delayed (1), highly delayed (2), diverted (3), or cancelled (4)')
```
Time Consumed: 18.5 s

#### 2. Cancelled flights - We are going to investigate the relationship of cancelled flights and the reason behind. We will view the result of analysis through graph by visualization.
Library 1: **Pandas**
```ruby
# Select cancelled flights
CancelFlights = df[(df.STATUS == 4)]

# Create subplots
f, ax = plt.subplots(1, 2, figsize=(20, 8))

# Generate a pie chart of cancellation codes
pd.DataFrame(CancelFlights['CANCELLATION_CODE']).value_counts().plot.pie(
    explode=[0.05, 0.05, 0.05, 0.05],
    autopct='%1.1f%%',
    ax=ax[0],
    shadow=True
)
ax[0].set_ylabel('')

# Generate a bar chart of cancellation codes
pd.DataFrame(CancelFlights['CANCELLATION_CODE']).value_counts().plot.bar(figsize=(8, 6), ax=ax[1])

# Show the plots
plt.show()

# Print legend explaining cancellation codes
print('A = carrier, B = weather, C = NAS, D = security')
```
Time Consumed: 512 ms

```ruby
import datetime as dt

# Select cancelled flights
CancelFlights = df[(df.STATUS == 4)]

# Group by month and plot the count of cancelled flights
CancelFlights['CANCELLATION_CODE'].groupby(CancelFlights['FL_DATE'].dt.month).count().plot()
plt.show()
```
Time Consumed: 335 ms

Library 2: **Dask**
```ruby
CancFlights = ddf[(ddf.STATUS == 4)]

f,ax=plt.subplots(1,2,figsize=(20,8))
pd.DataFrame(CancFlights['CANCELLATION_CODE']).value_counts().plot.pie(explode=[0.05,0.05,0.05,0.05],autopct='%1.1f%%',ax=ax[0],shadow=True)
ax[0].set_ylabel('')
pd.DataFrame(CancFlights['CANCELLATION_CODE']).value_counts().plot.bar(figsize=(8,6), ax=ax[1])
plt.show()

print('A = carrier, B = weather, C = NAS, D=security')
```
Time Consumed: 1min 6s

```ruby
import datetime as dt
CancFlights = ddf[(ddf.STATUS == 4)]
#CancFlights['FL_DATE'] = pd.to_datetime(CancFlights['FL_DATE'])
CancFlights['CANCELLATION_CODE'].groupby(CancFlights['FL_DATE'].dt.month).count().compute().plot()
plt.show()
```
Time Consumed: 

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Select cancelled flights
CancelFlights = pandas_df[(pandas_df.STATUS == 4)]

# Create subplots
f, ax = plt.subplots(1, 2, figsize=(20, 8))

# Generate a pie chart of cancellation codes
pd.DataFrame(CancelFlights['CANCELLATION_CODE']).value_counts().plot.pie(
    explode=[0.05, 0.05, 0.05, 0.05],
    autopct='%1.1f%%',
    ax=ax[0],
    shadow=True
)
ax[0].set_ylabel('')

# Generate a bar chart of cancellation codes
pd.DataFrame(CancelFlights['CANCELLATION_CODE']).value_counts().plot.bar(figsize=(8, 6), ax=ax[1])

# Show the plots
plt.show()

# Print legend explaining cancellation codes
print('A = carrier, B = weather, C = NAS, D = security')
```
Time Consumed: 19.4 s

```ruby
import datetime as dt

# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Select cancelled flights
CancelFlights = pandas_df[(pandas_df.STATUS == 4)]

# Group by month and plot the count of cancelled flights
CancelFlights['CANCELLATION_CODE'].groupby(CancelFlights['FL_DATE'].dt.month).count().plot()
plt.show()
```
Time Consumed: 19.2 s

####  3. Delayed flights - We will explore the facts and insights about the delayed flights
Library 1: **Pandas**
```ruby
Delayedflights = df[(df.STATUS >= 1) &(df.STATUS < 3)]
sns.distplot(Delayedflights['ARR_DELAY'])
plt.show()
```
Time Consumed: 2.75 s
```ruby
df['FL_DATE'] = pd.to_datetime(df['FL_DATE'])

# Set up subplots
fig, ax = plt.subplots(1, 2, figsize=(20, 8))

# Average delay by month
df['ARR_DELAY'].groupby(df['FL_DATE'].dt.month).mean().plot(ax=ax[0])
ax[0].set_title('Average delay by month')

# Number of minutes delayed by month
df['ARR_DELAY'].groupby(df['FL_DATE'].dt.month).sum().plot(ax=ax[1])
ax[1].set_title('Number of minutes delayed by month')

# Show the plot
plt.show()
```
Time Consumed: 991 ms

Library 2: **Dask**
```ruby
Delayedflights = ddf[(ddf.STATUS >= 1) &(ddf.STATUS < 3)]
```
Time Consumed: 8.36 ms
```ruby
sns.distplot(Delayedflights['ARR_DELAY'])
plt.show()
```
Time Consumed: 
```ruby
f,ax=plt.subplots(1,2,figsize=(20,8))
Delayedflights['ARR_DELAY'].groupby(Delayedflights['FL_DATE'].dt.month).mean().compute().plot(ax=ax[0])
ax[0].set_title('Average delay by month')
Delayedflights['ARR_DELAY'].groupby(Delayedflights['FL_DATE'].dt.month).sum().compute().plot(ax=ax[1])
ax[1].set_title('Number of minutes delayed by month')
plt.show()
```
Time Consumed: 

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Select rows from the DataFrame where the status is between 1 and 3.
Delayedflights = pandas_df[(pandas_df.STATUS >= 1) &(pandas_df.STATUS < 3)]
sns.distplot(Delayedflights['ARR_DELAY'])

# Show the plot
plt.show()
```
Time Consumed: 22.1 s

```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Concert datatype of FL_DATE to datetime
pandas_df['FL_DATE'] = pd.to_datetime(pandas_df['FL_DATE'])

# Set up subplots
fig, ax = plt.subplots(1, 2, figsize=(20, 8))

# Average delay by month
pandas_df['ARR_DELAY'].groupby(pandas_df['FL_DATE'].dt.month).mean().plot(ax=ax[0])
ax[0].set_title('Average delay by month')

# Number of minutes delayed by month
pandas_df['ARR_DELAY'].groupby(pandas_df['FL_DATE'].dt.month).sum().plot(ax=ax[1])
ax[1].set_title('Number of minutes delayed by month')

# Show the plot
plt.show()
```
Time Consumed: 19.8 s

#### 4. Delay reasons - We will going to explore the causes of flights delays.
Library 1: **Pandas**
```ruby
df2 = Delayedflights.filter(['FL_DATE', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'], axis=1)
df2['FL_DATE'] = pd.to_datetime(df2['FL_DATE'])  # Convert 'FL_DATE' to Pandas datetime format if not already done
df2 = df2.groupby(df2['FL_DATE'].dt.month)[['CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']].sum().plot()
df2.legend(loc='upper center', bbox_to_anchor=(0.5, 1.25), ncol=3, fancybox=True, shadow=True)
plt.show()
```
Time Consumed: 261 ms

Library 2: **Dask**
```ruby
df2 = Delayedflights.compute().filter(['FL_DATE','CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'], axis=1)
df2 = df2.groupby(df2['FL_DATE'].dt.month)['CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'].sum().plot()
df2.legend(loc='upper center', bbox_to_anchor=(0.5, 1.25), ncol=3, fancybox=True, shadow=True)
plt.show()
```
Time Consumed: 33 s

Library 3: **Vaex**
```ruby
import datetime as dt

# Create a new DataFrame 'df2'
df2 = Delayedflights.filter(['FL_DATE', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'], axis=1)

# Convert datatype of 'FL_DATE' datetime
df2['FL_DATE'] = pd.to_datetime(df2['FL_DATE'])  

# Group the data by month and summing up the delay types for each month.
df2 = df2.groupby(df2['FL_DATE'].dt.month)[['CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']].sum().plot()

# Format of the plot
df2.legend(loc='upper center', bbox_to_anchor=(0.5, 1.25), ncol=3, fancybox=True, shadow=True)
plt.show()
```
Time Consumed: 890 ms

#### 5. Relationship between variables - We will going to explore the relationships between thses variables, especially on the causes of the dalayed flights.
Library 1: **Pandas**
```ruby
cols = ['ARR_DELAY', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']
delay_pd = Delayedflights[cols]
sns.pairplot(delay_pd, height=2.5)
plt.show()
```
Time Consumed: 49.4 s
```ruby
df['OP_CARRIER'].value_counts().plot.bar()
plt.title('Delay Distribution by Carrier')
plt.show()
```
Time Consumed: 673 ms

Library 2: **Dask**
```ruby
sns.set()
cols = ['ARR_DELAY', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']
delay_pd = Delayedflights[cols].compute()
sns.pairplot(delay_pd, size = 2.5)
plt.show()
```
Time Consumed: 1min 53s

```ruby
ddf['OP_CARRIER'].value_counts().compute()
```
Time Consumed: 33.3 s

```ruby
ddf['OP_CARRIER'].value_counts().compute().plot.bar()
plt.title('Delay Distribution by Carrier')
```
Time Consumed: 


Library 3: **Vaex**
```ruby
# Create a new DataFrame 'delay_pd' containingthe specified columns
cols = ['ARR_DELAY', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']
delay_pd = Delayedflights[cols]

# Plot the graph
sns.pairplot(delay_pd, height=2.5)
plt.show()
```
Time Consumed: 1min 30s

```ruby
# Count the occurrences of each unique value in the 'OP_CARRIER' column
df['OP_CARRIER'].value_counts().plot.bar()

plt.title('Delay Distribution by Carrier')
plt.show()
```
Time Consumed: 2.53 s

### 6.0 Asking and Answering Questions <a name = "6-asking-answering"></a>
#### Q1: What percentage of flights experienced delays or cancellations?
Library 1: **Pandas**
```ruby
# Calculate the percentage of delayed flights
delayed_percentage = (df['ARR_DELAY'].notnull().sum() / len(df)) * 100

# Calculate the percentage of cancelled flights
cancelled_percentage = (df['CANCELLATION_CODE'].notnull().sum() / len(df)) * 100

print(f"Percentage of delayed flights: {delayed_percentage:.2f}%")
print(f"Percentage of cancelled flights: {cancelled_percentage:.2f}%")
```
Time Consumed: 149 ms

Library 2: **Dask**
```ruby
import dask.dataframe as dd

# Calculate the percentage of delayed flights
delayed_percentage = (ddf['ARR_DELAY'].notnull().sum() / len(ddf)).compute() * 100

# Calculate the percentage of cancelled flights
cancelled_percentage = (ddf['CANCELLATION_CODE'].notnull().sum() / len(ddf)).compute() * 100

print(f"Percentage of delayed flights: {delayed_percentage:.2f}%")
print(f"Percentage of cancelled flights: {cancelled_percentage:.2f}%")
```
Time Consumed: 2min 11s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Calculate the percentage of delayed flights
delayed_percentage = (pandas_df['ARR_DELAY'].notnull().sum() / len(pandas_df)) * 100

# Calculate the percentage of cancelled flights
cancelled_percentage = (pandas_df['CANCELLATION_CODE'].notnull().sum() / len(pandas_df)) * 100

print(f"Percentage of delayed flights: {delayed_percentage:.2f}%")
print(f"Percentage of cancelled flights: {cancelled_percentage:.2f}%")
```
Time Consumed: 27.2 s

#### Q2: How do taxi-out and taxi-in times relate to overall delays?
Library 1: **Pandas**
```ruby
# Scatter plot to analyze the relationship between taxi-out time and arrival delay
plt.scatter(df['TAXI_OUT'], df['ARR_DELAY'], alpha=0.5)
plt.xlabel('Taxi-Out Time')
plt.ylabel('Arrival Delay')
plt.title('Relationship between Taxi-Out Time and Arrival Delay')
plt.show()
```
Time Consumed: 13 s

Library 2: **Dask**
```ruby
# Scatter plot to analyze the relationship between taxi-out time and arrival delay
plt.scatter(ddf['TAXI_OUT'].compute(), ddf['ARR_DELAY'].compute(), alpha=0.5)
plt.xlabel('Taxi-Out Time')
plt.ylabel('Arrival Delay')
plt.title('Relationship between Taxi-Out Time and Arrival Delay')
plt.show()
```
Time Consumed: 1min 23s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Scatter plot to analyze the relationship between taxi-out time and arrival delay
plt.scatter(pandas_df['TAXI_OUT'], pandas_df['ARR_DELAY'], alpha=0.5)
plt.xlabel('Taxi-Out Time')
plt.ylabel('Arrival Delay')
plt.title('Relationship between Taxi-Out Time and Arrival Delay')
plt.show()
```
Time Consumed: 58.1 s

#### Q3: Are there specific months or seasons when flight cancellations are more frequent?
Library 1: **Pandas**
```ruby
df['Month'] = df['FL_DATE'].dt.month

# Count the number of cancellations per month
cancellations_by_month = df['CANCELLATION_CODE'].notnull().groupby(df['Month']).sum()

# Plot the results
cancellations_by_month.plot(kind='bar')
plt.xlabel('Month')
plt.ylabel('Number of Cancellations')
plt.title('Monthly Analysis of Flight Cancellations')
plt.show()
```
Time Consumed: 1.02 s

Library 2: **Dask**
```ruby
ddf['Month'] = ddf['FL_DATE'].dt.month

# Count the number of cancellations per month
cancellations_by_month = ddf['CANCELLATION_CODE'].notnull().groupby(ddf['Month']).sum()

# Plot the results
cancellations_by_month.compute().plot(kind='bar')
plt.xlabel('Month')
plt.ylabel('Number of Cancellations')
plt.title('Monthly Analysis of Flight Cancellations')
plt.show()
```
Time Consumed: 33.5 s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Assuming df is your Pandas DataFrame
pandas_df['Month'] = pandas_df['FL_DATE'].dt.month

# Count the number of cancellations per month
cancellations_by_month = pandas_df['CANCELLATION_CODE'].notnull().groupby(pandas_df['Month']).sum()

# Plot the results
cancellations_by_month.plot(kind='bar')
plt.xlabel('Month')
plt.ylabel('Number of Cancellations')
plt.title('Monthly Analysis of Flight Cancellations')
plt.show()
```
Time Consumed: 32.4 s

#### Q4: Do delays vary between daytime and nighttime flights?
Library 1: **Pandas**
```ruby
df['Daytime'] = (df['CRS_DEP_TIME'] >= 600) & (df['CRS_DEP_TIME'] < 1800)

# Create a boxplot to compare delays during daytime and nighttime
sns.boxplot(x='Daytime', y='ARR_DELAY', data=df)
plt.xlabel('Daytime vs. Nighttime')
plt.ylabel('Arrival Delay')
plt.title('Comparison of Arrival Delays: Daytime vs. Nighttime')
plt.show()
```
Time Consumed: 1.73 s

Library 2: **Dask**
```ruby
ddf['Daytime'] = (ddf['CRS_DEP_TIME'] >= 600) & (ddf['CRS_DEP_TIME'] < 1800)

# Create a boxplot to compare delays during daytime and nighttime
sns.boxplot(x='Daytime', y='ARR_DELAY', data=ddf.compute())
plt.xlabel('Daytime vs. Nighttime')
plt.ylabel('Arrival Delay')
plt.title('Comparison of Arrival Delays: Daytime vs. Nighttime')
plt.show()

```
Time Consumed: 38.1 s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

pandas_df['Daytime'] = (pandas_df['CRS_DEP_TIME'] >= 600) & (pandas_df['CRS_DEP_TIME'] < 1800)

# Create a boxplot to compare delays during daytime and nighttime
sns.boxplot(x='Daytime', y='ARR_DELAY', data=pandas_df)
plt.xlabel('Daytime vs. Nighttime')
plt.ylabel('Arrival Delay')
plt.title('Comparison of Arrival Delays: Daytime vs. Nighttime')
plt.show()
```
Time Consumed: 32.3 s

#### Q5: Is there a correlation between the air time of a flight and the arrival delay?
Library 1: **Pandas**
```ruby
# Scatter plot to analyze the relationship between air time and arrival delay
plt.scatter(df['AIR_TIME'], df['ARR_DELAY'], alpha=0.5)
plt.xlabel('Air Time')
plt.ylabel('Arrival Delay')
plt.title('Relationship between Air Time and Arrival Delay')
plt.show()
```
Time Consumed: 12.9 s

Library 2: **Dask**
```ruby
# Scatter plot to analyze the relationship between air time and arrival delay
plt.scatter(ddf['AIR_TIME'].compute(), ddf['ARR_DELAY'].compute(), alpha=0.5)
plt.xlabel('Air Time')
plt.ylabel('Arrival Delay')
plt.title('Relationship between Air Time and Arrival Delay')
plt.show()
```
Time Consumed: 1min 33s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Scatter plot to analyze the relationship between air time and arrival delay
plt.scatter(pandas_df['AIR_TIME'], pandas_df['ARR_DELAY'], alpha=0.5)
plt.xlabel('Air Time')
plt.ylabel('Arrival Delay')
plt.title('Relationship between Air Time and Arrival Delay')
plt.show()
```
Time Consumed: 56.7 s

#### Q6: At what times of the day do delays occur most frequently?
Library 1: **Pandas**
```ruby
# Extract the hour from the scheduled departure time
df['Hour'] = df['CRS_DEP_TIME'] // 100

# Group by hour and calculate the average arrival delay
average_delay_by_hour = df.groupby('Hour')['ARR_DELAY'].mean()

# Plotting
plt.figure(figsize=(12, 6))
average_delay_by_hour.plot(marker='o')
plt.xlabel('Hour of the Day')
plt.ylabel('Average Arrival Delay (minutes)')
plt.title('Hourly Analysis of Arrival Delays')
plt.show()
```
Time Consumed: 283 ms

Library 2: **Dask**
```ruby
# Extract the hour from the scheduled departure time
ddf['Hour'] = ddf['CRS_DEP_TIME'] // 100

# Group by hour and calculate the average arrival delay
average_delay_by_hour = ddf.groupby('Hour')['ARR_DELAY'].mean().compute()

# Plotting
plt.figure(figsize=(12, 6))
average_delay_by_hour.plot(marker='o')
plt.xlabel('Hour of the Day')
plt.ylabel('Average Arrival Delay (minutes)')
plt.title('Hourly Analysis of Arrival Delays')
plt.show()
```
Time Consumed: 34.6 s

Library 3: **Vaex**
```ruby
# Convert the dataframe to pandas to plot the graph
pandas_df = df.to_pandas_df()

# Extract the hour from the scheduled departure time
pandas_df['Hour'] = pandas_df['CRS_DEP_TIME'] // 100

# Group by hour and calculate the average arrival delay
average_delay_by_hour = pandas_df.groupby('Hour')['ARR_DELAY'].mean()

# Plotting
plt.figure(figsize=(12, 6))
average_delay_by_hour.plot(marker='o')
plt.xlabel('Hour of the Day')
plt.ylabel('Average Arrival Delay (minutes)')
plt.title('Hourly Analysis of Arrival Delays')
plt.show()
```
Time Consumed: 30.4 s


## 7.0 Conclusion <a name = "conclusion"></a>

**Pandas:**

**Advantages:**

* Ease of Use: Pandas has a user-friendly and intuitive API, making it easy for beginners to get started with data analysis.
* Rich Functionality: It provides a wide range of functions for data manipulation, cleaning, and analysis.
* Ecosystem: Pandas has a large and active community, which means there is extensive documentation and a wealth of resources available.

**Disadvantages:**

* In-Memory Limitations: Pandas is designed for in-memory data processing, so it may struggle with large datasets that don't fit into RAM.
* Limited Parallelism: Pandas lacks built-in support for parallel processing and distributed computing.


**Dask:**

**Advantages:**

* Scalability: Dask is designed to scale from a single machine to a cluster of machines, allowing it to handle larger-than-memory datasets.
* Familiar API: It provides a Pandas-like API, making it easier for Pandas users to transition to Dask.

**Disadvantages:**

* Learning Curve: While Dask's API is similar to Pandas, working with distributed computing and understanding Dask's delayed execution can have a learning curve.
* Overhead: Introducing Dask for small datasets or tasks may incur unnecessary overhead.

**Vaex:**

**Advantages:**

* High Performance: Vaex is optimized for speed and is designed to handle large datasets efficiently.
* Memory-Mapped: It uses a memory-mapped approach for out-of-core processing, allowing it to handle datasets larger than available RAM.
* Lazy Evaluation: Vaex employs lazy evaluation, which can lead to optimized computations.
  
**Disadvantages:**

* Limited Ecosystem: Vaex, while powerful, has a smaller user base compared to Pandas and Dask, which might result in a more limited ecosystem and community support.
* Does not have much built-in function: Vaex does not have many built-in function for plotting the graph for visualization. Users need to convert the Dataframe to Pandas in order to plot graph.

In conclusion, Pandas, with its user-friendly and expressive API, is an excellent choice for small to medium-sized datasets where ease of use is a priority. Dask, on the other hand, shines in scenarios dealing with really big datasets and need to do things at the same time on different parts of the data. It's great for making things faster. If high-performance analytics on large in-memory datasets is needed, Vaex is good because it's built to handle that, especially when the data doesn't fit into the computer's memory. Each one has its own strengths for different situations in data analysis.

## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

