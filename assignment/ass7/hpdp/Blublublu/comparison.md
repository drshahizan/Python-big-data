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
+ [Dataset Selection](#dataset-selection)
+ [Library Chosen](#library-chosen)
  + [Pandas](#pandas)
  + [DASK](#dask)
  + [Vaex](#vaex)
+ [Comparison Between Libraries](#comparison-libraries)
  + [Installation of Libraries](#installation)
  + [Dataset Loading](#loading)
+ [Conclusion](#conclusion)

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

### Dataset Loading <a name = "loading"></a>
Library 1: **Pandas**
```ruby
from google.colab import files

# Load the dataset
file_path = '/content/airline-delay-analysis/airline delay analysis/2018.csv'
df = pd.read_csv(file_path, encoding='ISO-8859-1')
```
Time Consumed: 

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
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

### Explore Dataset <a name = "explore"></a>
#### Check the Datatypes
Library 1: **Pandas**
```ruby
df.dtypes
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf.dtypes
```
Time Consumed: 

Library 3: **Vaex**
```ruby
# Check the datatypes

```
Time Consumed: 

#### Display the first 10 rows of the dataset
Library 1: **Pandas**
```ruby
df.head(10)
```
Time Consumed: 

Library 2: **Dask**
```ruby
first_10_rows = ddf.head(10)
print(first_10_rows)
```
Time Consumed: 

Library 3: **Vaex**
```ruby 

```
Time Consumed: 

#### Obtain description of the dataset
Library 1: **Pandas**
```ruby
df.describe()
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf.describe().compute()
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Obtain information of the dataset
Library 1: **Pandas**
```ruby
df.info()
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf.info()
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Check missing data
Library 1: **Pandas**
```ruby
df.isna().sum()
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf.isna().sum().compute()
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Identifying Multicollinearity and Variable Selection
Library 1: **Pandas**
```ruby
import matplotlib.pyplot as plt
import seaborn as sns

corrmat = df.corr()
f, ax = plt.subplots(figsize=(12, 9))
sns.heatmap(corrmat, vmax=.8, square=True, xticklabels=corrmat.columns, yticklabels=corrmat.columns)
plt.show()
```
Time Consumed: 

Library 2: **Dask**
```ruby
import matplotlib.pyplot as plt
import seaborn as sns
corrmat = ddf.corr()
f, ax = plt.subplots(figsize=(12, 9))
sns.heatmap(corrmat, vmax=.8, square=True, xticklabels=corrmat.columns, yticklabels=corrmat.columns);
plt.show()
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Converting the 'FL_DATE' column to datetime format
Library 1: **Pandas**
```ruby
df['FL_DATE'] = pd.to_datetime(df['FL_DATE'])
df.dtypes
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf['FL_DATE'] = ddf['FL_DATE'].astype('datetime64[ns]')
ddf.dtypes
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Return number of rows
Library 1: **Pandas**
```ruby
len(df)
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf.shape[0].compute()
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Create a new column to represent the status of the flight
Library 1: **Pandas**
```ruby
df['STATUS'] =df['ARR_DELAY'].apply(lambda x: 0 if x <= 15 else 1 if x <= 30 else 2 if x <= 60 else 3 if x <= 120 else 4)
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf['STATUS'] = ddf['ARR_DELAY'].apply(lambda x: 0 if x <= 15 else 1 if x <= 30 else 2 if x <= 60 else 3 if x <= 120 else 4)
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Replace values in the 'CANCELLATION_CODE' column
Library 1: **Pandas**
```ruby
df['CANCELLATION_CODE'].replace(['A', 'B', 'C', 'D'], [0, 1, 2, 3])
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf['CANCELLATION_CODE'].replace(['A', 'B', 'C', 'D'], [0, 1, 2, 3])
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Drop unnecessary column
Library 1: **Pandas**
```ruby
df = df.drop(columns=['DEP_DELAY', 'ARR_TIME','CRS_ARR_TIME', 'ACTUAL_ELAPSED_TIME', 'CRS_ELAPSED_TIME', 
                      'DIVERTED','CANCELLED','DISTANCE','OP_CARRIER_FL_NUM','Unnamed: 27'])
```
Time Consumed: 

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
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### Display first 20 rows of the dataset
Library 1: **Pandas**
```ruby
df.head(20)
```
Time Consumed: 

Library 2: **Dask**
```ruby
ddf.head(20)
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

### Exploratory Analysis and Visualization
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
Time Consumed: 

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
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

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
Time Consumed: 

```ruby
import datetime as dt

# Select cancelled flights
CancelFlights = df[(df.STATUS == 4)]

# Group by month and plot the count of cancelled flights
CancelFlights['CANCELLATION_CODE'].groupby(CancelFlights['FL_DATE'].dt.month).count().plot()
plt.show()
```
Time Consumed: 

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
Time Consumed: 

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

```
Time Consumed:

####  3. Delayed flights - We will explore the facts and insights about the delayed flights
Library 1: **Pandas**
```ruby
Delayedflights = df[(df.STATUS >= 1) &(df.STATUS < 3)]
sns.distplot(Delayedflights['ARR_DELAY'])
plt.show()
```
Time Consumed: 
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
Time Consumed: 

Library 2: **Dask**
```ruby
Delayedflights = ddf[(ddf.STATUS >= 1) &(ddf.STATUS < 3)]
```
Time Consumed: 
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

```
Time Consumed: 

#### 4. Delay reasons - We will going to explore the causes of flights delays.
Library 1: **Pandas**
```ruby
df2 = Delayedflights.filter(['FL_DATE', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'], axis=1)
df2['FL_DATE'] = pd.to_datetime(df2['FL_DATE'])  # Convert 'FL_DATE' to Pandas datetime format if not already done
df2 = df2.groupby(df2['FL_DATE'].dt.month)[['CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']].sum().plot()
df2.legend(loc='upper center', bbox_to_anchor=(0.5, 1.25), ncol=3, fancybox=True, shadow=True)
plt.show()
```
Time Consumed: 

Library 2: **Dask**
```ruby
df2 = Delayedflights.compute().filter(['FL_DATE','CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'], axis=1)
df2 = df2.groupby(df2['FL_DATE'].dt.month)['CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY'].sum().plot()
df2.legend(loc='upper center', bbox_to_anchor=(0.5, 1.25), ncol=3, fancybox=True, shadow=True)
plt.show()
```
Time Consumed: 

Library 3: **Vaex**
```ruby

```
Time Consumed: 

#### 5. Relationship between variables - We will going to explore the relationships between thses variables, especially on the causes of the dalayed flights.
Library 1: **Pandas**
```ruby
cols = ['ARR_DELAY', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']
delay_pd = Delayedflights[cols]
sns.pairplot(delay_pd, height=2.5)
plt.show()
```
Time Consumed: 
```ruby
df['OP_CARRIER'].value_counts().plot.bar()
plt.title('Delay Distribution by Carrier')
plt.show()
```
Time Consumed: 

Library 2: **Dask**
```ruby
sns.set()
cols = ['ARR_DELAY', 'CARRIER_DELAY', 'LATE_AIRCRAFT_DELAY', 'NAS_DELAY', 'WEATHER_DELAY', 'SECURITY_DELAY']
delay_pd = Delayedflights[cols].compute()
sns.pairplot(delay_pd, size = 2.5)
plt.show()
```
Time Consumed: 

```ruby
ddf['OP_CARRIER'].value_counts().compute()
```
Time Consumed: 

```ruby
ddf['OP_CARRIER'].value_counts().compute().plot.bar()
plt.title('Delay Distribution by Carrier')
```
Time Consumed: 


Library 3: **Vaex**
```ruby

```
Time Consumed: 

## Conclusion <a name = "conclusion"></a>


## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

