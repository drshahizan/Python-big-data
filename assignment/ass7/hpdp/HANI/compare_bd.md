<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)


# Assignment 7: Comparison between libraries


| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------: |
| ALYA BALQISS BINTI AZAHAR | A21EC0158 | Pandas |
| MUHAMMAD IQMAL BIN SIS | A21EC0080 | Dask |
| NADIA SYAFIQAH BINTI ZULKIPLI | A21EC0098 | Modin |
| MUHAMMAD HARITH HAKIM BIN OTHMAN | A21EC0205 | Comparison & Summarization |
  

## Introduction

In the dynamic realm of data science, the choice of tools and libraries significantly influences the efficiency and speed of data processing and analysis. As part of our collective endeavor to unravel the intricacies of Exploratory Data Analysis (EDA), our group has embarked on a comprehensive exploration of three powerful Python libraries: Pandas, Dask, and Modin. The primary objective of this project is to discern and compare the effectiveness of these libraries in handling diverse datasets and conducting EDA.

## Dataset Selection
The dataset encompasses property sales records starting from January 1995 up to the most recent monthly data available. It includes diverse transaction types, spanning from residential to commercial properties, offering a comprehensive perspective on the real estate market in England and Wales.

[UK Property Price Data (1995-2023)](https://www.kaggle.com/datasets/willianoliveiragibin/uk-property-price-data-1995-2023-04)

![image](https://github.com/drshahizan/Python-big-data/assets/118237681/a0211df1-e761-4076-893f-3b0a7f3fd2df)


## 1. Exploring The Libraries 

### 1.1 Pandas

Pandas, short for "Panel Data," is a versatile Python library that revolutionizes data manipulation. At its core are two essential data structures – Series and DataFrame. A Series is a labeled one-dimensional array, while a data frame is a powerful two-dimensional structure for tabular data.

* Library setup

```ruby
pip install pandas
```

```ruby
import pandas as np
```

### 1.2 Modin

Modin is a library in Python designed to accelerate data manipulation tasks, particularly those involving Pandas DataFrames. Modin stands for "Pandas on Ray" and aims to provide a fast and scalable alternative to Pandas by utilizing parallel and distributed computing.

* Library setup

```ruby
pip install modin
```

```ruby
import modin.pandas as pd
```

### 1.3 Dask

Dask is a parallel computing library in Python designed to enable efficient parallel computing for analytics, machine learning, and other computational tasks. It provides advanced parallelism for larger-than-memory computations using parallel processing and, in some cases, distributed computing. Dask is particularly useful when working with datasets that are too large to fit into memory.

* Library setup

```ruby
pip install dask
```

## 2. Loading the dataset

For all the datasets, we use the same method to load them into Python. This approach is chosen for its simplicity and convenience. The loading time remains consistent across all the libraries, given that they all employ the same method.

```ruby
from  google.colab import files
files.upload()
```

* Upload dataset using Kaggle API
```ruby
!pip install kaggle # 1. Install the Kaggle Package
!mkdir -p ~/.kaggle # 2. Create a Kaggle Directory
!cp kaggle.json ~/.kaggle/ #3. Upload the Kaggle API Token
!chmod 600 ~/.kaggle/kaggle.json #4. Set File Permission
```

* Install time measurement extension
```ruby
!pip install ipython-autotime
%load_ext autotime
```

* Download the dataset
```ruby
!kaggle datasets download willianoliveiragibin/uk-property-price-data-1995-2023-04
```

* Unzip the downloaded dataset
```ruby
!unzip uk-property-price-data-1995-2023-04.zip
```

## 3. Perform data preparation & cleaning

Cleaning and preparing data serve critical purposes:

a. **Ensuring Data Precision:** The process addresses errors, omissions, and inconsistencies in data, fostering reliability and trustworthiness.

b. **Elevating Data Quality:** Well-prepared data leads to improved data quality by resolving issues like duplicates and outliers, resulting in a dataset that faithfully represents real-world situations.

c. **Streamlining Analysis:** Cleaned data facilitates the extraction of meaningful insights, patterns, and trends, fostering more accurate and dependable conclusions.

d. **Supporting Modeling and Machine Learning:** The effectiveness of machine learning models is highly influenced by input data quality. Effective data cleaning enhances model performance and accuracy.

e. **Managing Missing Data:** Handling incomplete datasets through strategies like imputation or removal ensures data integrity.

f. **Ensuring Consistency:** Data cleaning establishes uniformity, encompassing consistent formatting, standardized units, and a coherent structure for improved interpretability.

g. **Preparation for Specific Analyses:** Tailoring data to meet the requirements of specific analyses or modeling techniques is a key aspect of data preparation.

h. **Resource and Time Savings:** Early data cleaning and preparation mitigate the risk of issues during analysis or modeling, ultimately saving time and resources.

### 3.1 Pandas

* Sampling Data

```ruby
# Measure the start time
start_time = time.time()

filename = "202304.csv"

# Count the total number of rows in the CSV file
total_rows = sum(1 for line in open(filename)) - 1

# Sample size of 10%
sample_size = total_rows // 10

# Calculate the rows to skip for the sample
skip = sorted(random.sample(range(1, total_rows + 1), total_rows - sample_size))

# Read the CSV file with skipping non-sample rows
df = pd.read_csv(filename, skiprows=skip)
```

Using Pandas library it shows that the time to sample the data is 172.09 seconds

* Adding column names for headers for easy readability

```ruby
# Define your column names for header
column_names = ['Transaction Unique Identifier',
                'Price', 'Transfer Date', 'Postcode', 'Property Type', 'Old/New',
                'Duration', 'PAON', 'SAON', 'Street', 'Locality', 'Town/City', 'District',
                'County', 'PPDCategory Type', 'Record Status - Monthly File Only']

# Assign column names to the dataframe
df.columns = column_names
```


* Change the datatypes to a suitable format

```ruby
# Measure the start time
start_time = time.time()

# Define the data types for each column based on optimization
data_types = {
    'Transaction Unique Identifier': 'string',
    'Price': 'float32',
    'Transfer Date': 'datetime64',
    'Postcode': 'string',
    'Property Type': 'category',
    'Old/New': 'category',
    'Duration': 'category',
    'PAON': 'string',
    'SAON': 'string',
    'Street': 'string',
    'Locality': 'string',
    'Town/City': 'string',
    'District': 'string',
    'County': 'string',
    'PPDCategory Type': 'category',
    'Record Status - Monthly File Only': 'category'
}

# Convert columns to optimized data types
df = df.astype(data_types)

# Display information after sampling
final_file_size = os.path.getsize(filename) / (1024 ** 2)  # Final file size in MB
computation_time = time.time() - start_time  # Computation time in seconds

# Memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss / (1024 ** 2)  # Memory usage in MB

# Display DataFrame(df) object size
df_size = sys.getsizeof(df) / (1024 ** 2)  # Convert to megabytes
```
Computation Time: 1.87 seconds

```ruby
* Drop Missing Values

# Record the start time
start_time = time.time()

# Calculate memory usage before dropping missing values
memory_before = df.memory_usage().sum() / (1024 ** 2)  # Convert to megabytes

# Drop rows with missing values across all columns
df.dropna(inplace=True)

# Calculate memory usage after dropping missing values
memory_after = df.memory_usage().sum() / (1024 ** 2)  # Convert to megabytes

# Record the end time
end_time = time.time()

# Calculate computation time
computation_time = end_time - start_time

# Get the file size of the DataFrame after dropping missing values
file_size = os.path.getsize(filename) / (1024 ** 2)  # Convert to megabytes
```
Computation time: 1.53 seconds

```ruby
* Drop Duplicate Values

# Record the start time
start_time = time.time()

# Calculate memory usage before dropping duplicates
memory_before = df.memory_usage().sum() / (1024 ** 2)  # Convert to megabytes

# Drop duplicate rows based on all columns
df.drop_duplicates(inplace=True)

# Calculate memory usage after dropping duplicates
memory_after = df.memory_usage().sum() / (1024 ** 2)  # Convert to megabytes

# Record the end time
end_time = time.time()

# Calculate computation time
computation_time = end_time - start_time

# Get the file size of the DataFrame after dropping duplicates
file_size = os.path.getsize(filename) / (1024 ** 2)  # Convert to megabytes
```
Computation time: 0.66 seconds

* Drop Columns

```ruby
# Record the start time
start_time = time.time()

# Calculate memory usage before dropping specified columns
memory_before = df.memory_usage().sum() / (1024 ** 2)  # Convert to megabytes

# List of columns to drop
columns_drop = ['SAON', 'Duration', 'PPDCategory Type', 'Record Status - Monthly File Only']

# Drop the specified columns from the DataFrame
df.drop(columns=columns_drop, inplace=True)

# Calculate memory usage after dropping specified columns
memory_after = df.memory_usage().sum() / (1024 ** 2)  # Convert to megabytes

# Record the end time
end_time = time.time()

# Calculate computation time
computation_time = end_time - start_time

# Get the file size of the DataFrame after dropping specified columns
file_size = os.path.getsize(filename) / (1024 ** 2)  # Convert to megabytes
```
Computation time: 0.01 seconds

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
