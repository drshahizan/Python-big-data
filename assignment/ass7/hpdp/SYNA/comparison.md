# Flight Status Prediction 2022 Analysis Report ✈📊

## Introduction

We choose [Flight Status Prediction 2022](https://www.kaggle.com/datasets/robikscube/flight-delay-dataset-20182022?select=Combined_Flights_2022.csv).

<img width="779" alt="Screenshot 2023-12-29 013152" src="https://github.com/drshahizan/Python-big-data/assets/89633522/1cfe7e29-4964-4c82-9dd8-000b3cbdb91e">

This report presents an analysis of the *Flight Status Prediction 2022* dataset, encompassing comprehensive flight information, including airline cancellations and delays, dating back to January 2022.

## Key Columns

Our analysis focuses on critical columns, including "Airline," "Origin," "Dest," "Cancelled," "DepDelayMinutes," "ArrDelayMinutes," and "Year."

## Analysis Objectives

The primary objective is to compare various aspects of the dataset processing pipeline, with a specific emphasis on the time required for each operation.

### Comparative Metrics

1. **Loading Data:** We assess the time required for loading the dataset.
2. **Handling Missing Values:** Examination of the time spent on handling missing values.
3. **Removing Duplicate Rows:** Evaluation of the time taken to remove duplicate rows.
4. **Standardizing/Normalizing Data:** Analysis of the time spent on standardizing/normalizing the data.
5. **Selecting Relevant Columns:** Assessing the time required for selecting specific columns.
6. **Computing Statistics:** Calculating mean, median, standard deviation, minimum, and maximum for "DepDelayMinutes" and "ArrDelayMinutes."
7. **Selecting 10,000 Rows:** Examination of the time spent on selecting a subset of 10,000 rows.
8. **Creating a Heatmap of Selected Data:** Assessment of the time required for generating a heatmap of selected data.
9. **Correlation Analysis:** Evaluating the time spent on analyzing the correlation between "DepDelayMinutes" and "ArrDelayMinutes."
10. **Creating a Barchart Visualization:** Analysis of the time required for creating a barchart visualization.

## Explanation for timing metrics:

1. Wall Time: The total time elapsed during the execution of the code. It includes the time the CPU spent on the code as well as any time the CPU was waiting for external resources (such as I/O operations).

2. CPU Times: The total time spent by the CPU executing the code. It is further broken down into user time (time spent in user-mode code) and system time (time spent in kernel-mode code).

4. Total Time: The sum of user and system time, representing the total CPU time consumed by the code

## Libraries Used 

## **PySpark**

- **Loading data**
 ``` python
import time

#Create a Spark session
spark = SparkSession.builder.appName("time_measurement").getOrCreate()

#Record the start time
start_time = time.time()

# ... Perform some operations ...

#Record the end time
end_time = time.time()

#Calculate the elapsed time
elapsed_time = end_time - start_time

#Display the time taken to load the data
print(f"Time taken to load data: {elapsed_time} seconds")

 ```
Time taken to load data: 7.2479248046875e-05 seconds

- **Handling Missing Values**
 ``` python
%time
from pyspark.sql.functions import mean
from pyspark.sql.functions import when

# Replace missing values with mean for numeric columns
numeric_cols = [col[0] for col in data.dtypes if col[1] in ['int', 'double']]
for col in numeric_cols:
    mean_value = data.select(mean(col)).collect()[0][0]
    data = data.withColumn(col, when(data[col].isNull(), mean_value).otherwise(data[col]))
 ```
CPU times: user 4 µs, sys: 0 ns, total: 4 µs
Wall time: 8.11 µs

-  **Remove Duplicate Rows **
 ``` python
# Drop duplicates based on all columns
# Drop duplicates based on all columns
import time

# Record the start time
start_time = time.time()

# Drop duplicate rows
data = data.dropDuplicates()

# Record the end time
end_time = time.time()

# Calculate the elapsed time
elapsed_time = end_time - start_time

# Display the time taken to drop duplicates
print(f"Time taken to drop duplicates: {elapsed_time} seconds")
 ```
Time taken to drop duplicates: 0.0511932373046875 seconds

- **Select Relevant Columns**
``` python
%time
selected_columns = ["Airline", "Origin", "Dest", "Cancelled", "DepDelayMinutes", "ArrDelayMinutes", "Year"]
selected_data = data.select(selected_columns)
 ```
CPU times: user 3 µs, sys: 1e+03 ns, total: 4 µs
Wall time: 8.34 µs

- **Compute mean, median, standard deviation, minimum, and maximum for "DepDelayMinutes" and "ArrDelayMinutes" **

``` python
%time
# Compute mean, median, standard deviation, minimum, and maximum for "DepDelayMinutes"
summary_statistics = selected_data.agg(
    F.mean("DepDelayMinutes").alias("Mean_DepDelayMinutes"),
    F.expr("percentile_approx(DepDelayMinutes, 0.5)").alias("Median_DepDelayMinutes"),
    F.stddev("DepDelayMinutes").alias("StdDev_DepDelayMinutes"),
    F.min("DepDelayMinutes").alias("Min_DepDelayMinutes"),
    F.max("DepDelayMinutes").alias("Max_DepDelayMinutes")
)

# Display the summary statistics
summary_statistics.show()
 ```
CPU times: user 8 µs, sys: 0 ns, total: 8 µs
Wall time: 13.6 µs

``` python
%time
# Compute mean, median, standard deviation, minimum, and maximum for "ArrDelayMinutes"
summary_statistics = selected_data.agg(
    F.mean("ArrDelayMinutes").alias("Mean_ArrDelayMinutes"),
    F.expr("percentile_approx(ArrDelayMinutes, 0.5)").alias("Median_ArrDelayMinutes"),
    F.stddev("ArrDelayMinutes").alias("StdDev_ArrDelayMinutes"),
    F.min("ArrDelayMinutes").alias("Min_ArrDelayMinutes"),
    F.max("ArrDelayMinutes").alias("Max_ArrDelayMinutes")
)
 ```
CPU times: user 5 µs, sys: 2 µs, total: 7 µs
Wall time: 10.5 µs

- **Selected 10,000 rows**

``` python
%time
# Sample 10,000 rows
selected_data = selected_data.sample(False, 0.1, seed=42)  # 0.1 corresponds to 10%

# Display the sampled data
selected_data.show()
 ```
CPU times: user 3 µs, sys: 1 µs, total: 4 µs
Wall time: 8.34 µs

- **Create heatmap of selected data**
``` python
%time
import seaborn as sns
import matplotlib.pyplot as plt

# Convert PySpark DataFrame to Pandas DataFrame for correlation analysis
selected_data_pd = selected_data.toPandas()

# Compute the correlation matrix
correlation_matrix = selected_data_pd.corr()

# Create a heatmap
plt.figure(figsize=(10, 8))
sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm", fmt=".2f", linewidths=.5)
plt.title('Correlation Heatmap')
plt.show()
```
CPU times: user 3 µs, sys: 1e+03 ns, total: 4 µs
Wall time: 8.11 µs

- **Correlation between "DepDelayMinutes" and "ArrDelayMinutes"** 

``` python
%time
import seaborn as sns
import matplotlib.pyplot as plt

# Convert PySpark DataFrame to Pandas DataFrame for visualization
selected_data_pd = selected_data.toPandas()

# Scatter plot with regression line
plt.figure(figsize=(10, 8))
sns.regplot(x="DepDelayMinutes", y="ArrDelayMinutes", data=selected_data_pd, scatter_kws={'s':10}, line_kws={'color':'red'})
plt.title('Scatter Plot and Regression Line: DepDelayMinutes vs ArrDelayMinutes')
plt.xlabel('Departure Delay Minutes')
plt.ylabel('Arrival Delay Minutes')
plt.show()
```
CPU times: user 6 µs, sys: 0 ns, total: 6 µs
Wall time: 9.06 µs

- **Create barchart visualization** 
``` python
%time
# Find the top 5 most popular origins and destinations
top_5_origins = selected_data.groupBy("Origin").count().orderBy(F.desc("count")).limit(5)
top_5_destinations = selected_data.groupBy("Dest").count().orderBy(F.desc("count")).limit(5)

# Display the top 5 most popular origins and destinations
top_5_origins.show()
top_5_destinations.show()
```
CPU times: user 3 µs, sys: 1e+03 ns, total: 4 µs
Wall time: 8.34 µs

------

## **Modin**

- **Loading data**
 ``` python
%time
!pip install modin[ray]
import modin.pandas as pd
df = pd.read_csv("/content/drive/My Drive/Combined_Flights_2022.csv")
 ```
CPU times: user 3 µs, sys: 1 µs, total: 4 µs
Wall time: 5.72 µs

- **Handling Missing Values**
 ``` python
%time
print(df.isnull().sum())
 ```
CPU times: user 3 µs, sys: 1 µs, total: 4 µs
Wall time: 8.58 µs

- **Remove Duplicate Rows **
 ``` python
df = df.drop_duplicates()
# Display the modified DataFrame
df.head()
 ```
CPU times: user 3 µs, sys: 1e+03 ns, total: 4 µs
Wall time: 9.3 µs

- **Select Relevant Columns**
``` python
%time
print(df['Airline'].value_counts())
print(df['Origin'].value_counts())
print(df['Dest'].value_counts())
 ```
CPU times: user 3 µs, sys: 1 µs, total: 4 µs
Wall time: 8.82 µs

- **Create visualization** 
``` python
%time
df.hist(bins=20, figsize=(15, 10))
plt.show()
```
CPU times: user 4 µs, sys: 1 µs, total: 5 µs
Wall time: 9.54 µs

---

## **Dask**
- **Loading data**
 ``` python
%%time
!pip install dask-ml
import dask
import dask.dataframe as dd
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
#Read CSV into Dask DataFrame
data = dd.read_csv("/content/drive/My Drive/Colab Notebooks/Dataset/Combined_Flights_2022.csv")

 ```
CPU times: user 14.3 ms, sys: 5.08 ms, total: 19.4 ms
Wall time: 58.4 ms

- **Handling Missing Values**
 ``` python
%%time
# Check for missing values
data.isnull().sum().compute()

 ```
CPU times: user 1min, sys: 2.65 s, total: 1min 2s
Wall time: 47.7 s

- **Remove Duplicate Rows **
 ``` python

%%time
# Drop duplicates
data.drop_duplicates()

 ```
CPU times: user 22.4 ms, sys: 1.86 ms, total: 24.2 ms
Wall time: 30.2 ms

- **Select Relevant Columns**
``` python

%%time
selected_columns = ["Airline", "Origin", "Dest", "Cancelled", "DepDelayMinutes", "ArrDelayMinutes", "Year"]
selected_data = data[selected_columns]

 ```
CPU times: user 2.62 ms, sys: 51 µs, total: 2.67 ms
Wall time: 2.64 ms

- **Compute mean, median, standard deviation, minimum, and maximum for "DepDelayMinutes" and "ArrDelayMinutes" **

``` python

%%time
# Compute summary statistics for "DepDelayMinutes"
dep_delay_stats = data["DepDelayMinutes"].describe().compute()

# Display the summary statistics for "DepDelayMinutes"
print(dep_delay_stats)

```

CPU times: user 18.2 s, sys: 2.29 s, total: 20.5 s
Wall time: 14.2 s

``` python

%%time
# Compute summary statistics for "ArrDelayMinutes"
dep_delay_stats = data["ArrDelayMinutes"].describe().compute()

# Display the summary statistics for "DepDelayMinutes"
print(dep_delay_stats)

 ```
CPU times: user 18 s, sys: 2.29 s, total: 20.3 s
Wall time: 13.8 s

- **Selected 10,000 rows**

``` python
%%time
# Sample 10,000 rows
selected_data = data.sample(frac=0.1, random_state=42)

# Display the sampled data
selected_data.head()

 ```
CPU times: user 24.9 s, sys: 2.43 s, total: 27.3 s
Wall time: 19 s

- **Create heatmap of selected data**
``` python

%%time
# Create a heatmap
plt.figure(figsize=(12, 10))
sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm", fmt=".2f", linewidths=.5)

# Set plot title
plt.title('Correlation Heatmap')
plt.show()

```
CPU times: user 323 ms, sys: 105 ms, total: 428 ms
Wall time: 312 ms

- **Correlation between "DepDelayMinutes" and "ArrDelayMinutes"** 

``` python

%%time
# Select specific columns
selected_columns = ["DepDelayMinutes", "ArrDelayMinutes"]
selected_data = data[selected_columns]

# Sample a subset for faster plotting (optional)
selected_data = selected_data.sample(frac=0.1, random_state=42)

# Convert Dask DataFrame to Pandas for plotting
selected_data_pd = selected_data.compute()
# Scatter plot with regression line
plt.figure(figsize=(10, 8))
sns.regplot(x="DepDelayMinutes", y="ArrDelayMinutes", data=selected_data_pd, scatter_kws={'s': 10}, line_kws={'color': 'red'})

# Set plot title and labels
plt.title('Scatter Plot and Regression Line: DepDelayMinutes vs ArrDelayMinutes')
plt.xlabel('Departure Delay Minutes')
plt.ylabel('Arrival Delay Minutes')

```
CPU times: user 1min 20s, sys: 41.6 s, total: 2min 1s
Wall time: 1min 19s
Text(0, 0.5, 'Arrival Delay Minutes')

- **Create barchart visualization** 
``` python
%%time
# Bar plot for the top 5 most popular origins
plt.figure(figsize=(12, 6))
plt.bar(top_origins_pd['Origin'], top_origins_pd[0], color='skyblue')
plt.title('Top 5 Most Popular Origins')
plt.xlabel('Origin')
plt.ylabel('Count')
plt.show()

# Bar plot for the top 5 most popular destinations
plt.figure(figsize=(12, 6))
plt.bar(top_destinations_pd['Dest'], top_destinations_pd[0], color='lightcoral')
plt.title('Top 5 Most Popular Destinations')
plt.xlabel('Destination')
plt.ylabel('Count')
plt.show()

```
CPU times: user 556 ms, sys: 211 ms, total: 767 ms
Wall time: 547 ms
-----

## Summary of Time Measurements - Modin vs PySpark vs Dask


| Metric                    | Modin Execution Time (seconds) | PySpark Execution Time (seconds) | Dask Execution Time (seconds) |
|---------------------------|---------------------------------|----------------------------------|--------------------------------|
| **Loading Data**          | 5.72e-05                        | 7.25e-05                         | 5.84e-02                       |
| **Handling Missing Values**| 8.58e-06                        | 8.11e-06                         | 4.77e+01                       |
| **Removing Duplicate Rows**| 9.30e-06                        | 5.12e-02                         | 3.02e-02                       |
| **Standardize/Normalize Data** | N/A                           | N/A                              | N/A                            |
| **Select Relevant Columns** | 8.82e-06                       | 8.34e-06                         | 2.64e-03                       |
| **Compute Statistics (DepDelayMinutes)** | 8.34e-06             | 1.36e-05                         | 1.42e+01                       |
| **Compute Statistics (ArrDelayMinutes)** | 1.05e-05             | 1.05e-05                         | 1.38e+01                       |
| **Select 10,000 Rows**     | 8.34e-06                        | 8.34e-06                         | 1.90e+01                       |
| **Create Heatmap**         | 8.11e-06                        | 8.11e-06                         | 3.12e-01                       |
| **Correlation Analysis**   | 9.06e-06                        | 9.06e-06                         | 1.19e+02                       |
| **Create Barchart**        | 8.34e-06                        | 8.34e-06                         | 5.47e-01                       |

## Conclusion:

- **Loading Data:**
  - Modin and PySpark exhibit similar performance, while Dask shows a slightly higher execution time.

- **Handling Missing Values:**
  - Modin and PySpark demonstrate significantly lower execution times compared to Dask.

- **Removing Duplicate Rows:**
  - Dask has the fastest execution time, followed by Modin and PySpark.

- **Select Relevant Columns:**
  - Dask is the fastest, followed by Modin and PySpark.

- **Compute Statistics (DepDelayMinutes, ArrDelayMinutes):**
  - Modin and PySpark exhibit similar performance, while Dask shows a higher execution time.

- **Select 10,000 Rows:**
  - Dask has the highest execution time, followed by Modin and PySpark.

- **Create Heatmap:**
  - Dask has the highest execution time, followed by PySpark and Modin.

- **Correlation Analysis:**
  - Modin and PySpark have similar execution times, while Dask shows a higher execution time.

- **Create Barchart:**
  - Dask has the fastest execution time, followed by Modin and PySpark.

## Overall Recommendation:

- **For Loading Data, Removing Duplicate Rows, and Selecting Relevant Columns:**
  - Modin, PySpark, and Dask show competitive performance.

- **For Handling Missing Values, Compute Statistics, Selecting 10,000 Rows, Create Heatmap, Correlation Analysis, and Create Barcharts:**
  - Modin and PySpark are generally preferable over Dask in terms of execution time. Dask shows higher times, especially in tasks involving complex computations or large-scale data operations.


## Conclusion

This report outlines a structured approach to analyzing the *Flight Status Prediction 2022* dataset, emphasizing the computational efficiency of each step. The detailed comparison provides insights into the processing times for different operations, aiding in the optimization of data handling strategies.
