# Flight Status Prediction 2022 Analysis Report ✈📊

## Introduction

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

## Libraries Used 

1. **PySpark**

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

- **Remove Duplicate Rows **
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

3. **Modin**

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

5. **Dask**
- **Loading data**
 ``` python


 ```
Time taken to load data: 7.2479248046875e-05 seconds

- **Handling Missing Values**
 ``` python

 ```

- **Remove Duplicate Rows **
 ``` python

 ```
- **Select Relevant Columns**
``` python

 ```
- **Compute mean, median, standard deviation, minimum, and maximum for "DepDelayMinutes" and "ArrDelayMinutes" **

``` python

 ```


``` python

 ```
- **Selected 10,000 rows**

``` python

 ```
- **Create heatmap of selected data**
``` python

```

- **Correlation between "DepDelayMinutes" and "ArrDelayMinutes"** 

``` python

```

- **Create barchart visualization** 
``` python

```

## Summary of comparison

## Conclusion

This report outlines a structured approach to analyzing the *Flight Status Prediction 2022* dataset, emphasizing the computational efficiency of each step. The detailed comparison provides insights into the processing times for different operations, aiding in the optimization of data handling strategies.
