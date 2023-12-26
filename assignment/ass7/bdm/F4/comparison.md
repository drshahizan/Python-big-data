## Introduction

### Pandas

Pandas is a Python library that simplifies data analysis. It offers two main structures: Series for single-column data and DataFrame for multi-column data.

With Pandas, data can be clean by fixing errors or filling in missing values. It allows you to analyze data by calculating statistics, grouping data, and finding patterns. Pandas can be used alongside other libraries like NumPy, SciPy, Matplotlib, and Scikit-learn for additional functionalities such as mathematical computations, scientific analysis, plotting, and machine learning.

It also enables to read data from and write data to various file formats or databases. Furthermore, it can be used with Matplotlib to create visualizations. Overall, Pandas is a vital tool for data scientists and data analysts as it makes data analysis in Python more efficient.

### Modin

Modin is a Python library designed to enhance the performance of data manipulation and analysis tasks by providing a parallelized and distributed backend for Pandas. It introduces parallel computing capabilities, enabling the execution of Pandas operations on multiple CPU cores for faster processing times. Additionally, Modin supports distributed computing through backends like Ray or Dask, making it suitable for handling large datasets that may exceed the memory capacity of a single machine. Despite its advanced features, Modin maintains compatibility with the Pandas API, allowing users to seamlessly switch between Pandas and Modin with minimal code changes.

As a drop-in replacement for Pandas, Modin is easy to integrate into existing codebases and offers performance improvements for common operations such as filtering, grouping, and aggregating. Users can choose from multiple backends based on their specific use case and computing environment, making Modin a versatile tool for data analysis tasks. It's worth noting that the effectiveness of Modin depends on the nature of the data and the operations performed, and users are encouraged to benchmark it against Pandas to evaluate performance gains in their specific applications.

By using Modin, you can potentially speed up operations like data loading, filtering, and aggregation, especially when working with large datasets.

### Vaex

Vaex is a high performance data wrangling Python library for lazy Out-of-Core DataFrames (similar to Pandas), to visualize and explore big tabular datasets. It calculates statistics such as mean, sum, count, standard deviation etc, on an N-dimensional grid for more than a billion (10^9) samples/rows per second. Visualization is done using histograms, density plots and 3d volume rendering, allowing interactive exploration of big data. Vaex uses memory mapping, zero memory copy policy and lazy computations for best performance (no memory wasted)

It helps developers work with “uncomfortably large” datasets on a single machine using lazy evaluation, memory mapping, and integrations with C++ code. It’s specifically designed to work “out of core” – to process data that’s too big to be loaded into memory (RAM) all at once.

Vaex solves this problem by rebuilding a Pandas-like library “from the ground up,” taking advantage of lower-level C++ integrations for parallelization and lazy evaluation. Opening a 100GB dataset on a normal laptop is difficult with Pandas, but Vaex can do this efficiently, allowing developers to analyze larger datasets without compute clusters.

## Comparative Analysis

Various Tasks/Functions are run using the three chosen libraries. 

Summary Table as below. 

| Number | Task/Function | Pandas | Modin | Vaex |
|--------|---------------|--------|-------|------|
| 1 | Read file | `df=pd.read_csv('/content/brewery_data_complete_extended.csv')` | `df=pd.read_csv('/content/brewery_data_complete_extended.csv')` | `df=vaex.open('/content/brewery_data_complete_extended.csv')` |
| 2 | Data Understanding |  |  |  |
|   | a) Display first 5 rows | `df.head(5)` | `df.head(5)` | `df.head(5)` |
|   | b) Display information | `df.info()` | `df.info()` | `df.info()` |
|   | c) Display descriptive statistics | `df.describe()` | `df.describe()` | `df.describe()` |
| 3 | Count |  |  |  |
|   | a) Count number of rows | `len(df)` | `len(df)` | `len(df)` |
|   | b) Count the non-null values in a variable | `df['Fermentation_Time'].count()` | `df['Fermentation_Time'].count()` | `df['Fermentation_Time'].count()` |
| 4 | Mean |  |  |  |
|   | a) Calculate mean of an int64 variable | `df.Fermentation_Time.mean()` | `df.Fermentation_Time.mean()` | `df.Fermentation_Time.mean()` |
|   | b) Calculate mean of a float64 variable | `df.Temperature.mean()` | `df.Temperature.mean()` | `df.Temperature.mean()` |
| 4 | Standard Deviation |  |  |  |
|   | a) Calculate standard deviation of an int64 variable | `df.Fermentation_Time.std()` | `df.Fermentation_Time.std()` | `df.Fermentation_Time.std()` |
|   | b) Calculate standard deviation of a float64 variable | `df.Temperature.std()` | `df.Temperature.std()` | `df.Temperature.std()` |
| 5 | Sum columns | `df['Fermentation_Time'] + df['Temperature']` | `df['Fermentation_Time'] + df['Temperature']` | `df['Fermentation_Time'] + df['Temperature']` |
| 6 | Sum columns mean | `(df['Fermentation_Time'] + df['Temperature']).mean()` | `(df['Fermentation_Time'] + df['Temperature']).mean()` | `(df['Fermentation_Time'] + df['Temperature']).mean()` |
| 7 | Value Counts | `df.Fermentation_Time.value_counts()` | `df.Fermentation_Time.value_counts()` | `df.Fermentation_Time.value_counts()` |
| 8 | Group-by |  |  |  |
|   | a) Multiple aggregation | `df_group=df.groupby(by='Beer_Style').agg({'Fermentation_Time':['mean','std'],'Temperature':['mean','std']})` | `df_group=df.groupby(by='Beer_Style').agg({'Fermentation_Time':['mean','std'],'Temperature':['mean','std']})` | `df_group=df.groupby(by='Beer_Style').agg({'Fermentation_Time':['mean','std'],'Temperature':['mean','std']})` |
|   | b) Mean aggregation | `df.groupby('Beer_Style')['Temperature'].mean()` | `df.groupby('Beer_Style')['Temperature'].mean()` | `df.groupby(df.Beer_Style,agg=vaex.agg.mean(df.Temperature))` |
|   | c) Count aggregation | `df.groupby('Beer_Style').count()` | `df.groupby('Beer_Style').count()` | `df.groupby(df.Beer_Style,agg='count')` |
| 9 | Join | `pd.merge(df, df_group, on='Beer_Style')` | `df.join(df_group, on='Beer_Style')` | `df.join(df_group,on='Beer_Style')` |
| 10 | EDA Visualization |  Refer to Notebooks Uploaded|

For the analysis, we will focus on Wall Time and CPU Time. CPU time is the time actually spent by CPU executing method code whereas the Wall time is the real-world time elapsed between method entry and method exit.

### Wall Time 

| Number | Task/Function | Pandas | UoM  | Modin | UoM  | Vaex | UoM  | Winner |
|--------|---------------|--------|------|-------|------|------|------|--------|
| 1      | Read file     | 95     | s    | 76    | s    | 4.8  | s    | Vaex   |
| 2      | Data Understanding | | | | | | | |
|        | a) Display first 5 rows | 193 | µs | 2.76 | ms | 977 | µs | Pandas |
|        | b) Display information | 21.2 | ms | 3.26 | s | 1.81 | s | Pandas |
|        | c) Display descriptive statistics | 10.5 | s | 51.3 | ms | 179 | s | Modin |
| 3      | Count          | | | | | | | |
|        | a) Count number of rows | 26.7 | µs | 65.6 | µs | 30 | µs | Pandas |
|        | b) Count the non-null values in a variable | 15.8 | ms | 4.53 | s | 6.87 | s | Pandas |
| 4      | Mean           | | | | | | | |
|        | a) Calculate mean of an int64 variable | 56.7 | ms | 3.76 | s | 8.4 | s | Pandas |
|        | b) Calculate mean of a float64 variable | 85.2 | ms | 2.12 | s | 8.14 | s | Pandas |
| 5      | Standard Deviation | | | | | | | |
|        | a) Calculate standard deviation of an int64 variable | 127 | ms | 2.27 | s | 7.93 | s | Pandas |
|        | b) Calculate standard deviation of a float64 variable | 153 | ms | 2.34 | s | 7.67 | s | Pandas |
| 6      | Sum columns    | 42 | ms | 26.3 | ms | 197 | µs | Vaex   |
| 7      | Sum columns mean | 86.4 | ms | 5.35 | s | 13.3 | s | Pandas |
| 8      | Value Counts   | 211 | ms | 2.67 | s | 7.99 | s | Pandas |
| 9      | Group-by       | | | | | | | |
|        | a) Multiple aggregation | 2.13 | s | 50.5 | s | 20.9 | s | Pandas |
|        | b) Mean aggregation | 1.26 | s | 6.53 | s | 18.2 | s | Pandas |
|        | c) Count aggregation | 17.2 | s | 33.5 | ms | 19.6 | s | Modin |
| 10     | Join           | 5.74 | s | 27.8 | ms | 8.88 | s | Modin |
| 11     | EDA Visualization | | | | | | | |
|        | a) Barplot      | 323 | ms | 281 | ms | 487 | ms | Modin |
|        | b) Boxplot      | 26.3 | s | 3.4 | s | 10.4 | s | Modin |
|        | c) Scatterplot  | 15.5 | s | 42.2 | s | 10.1 | s | Vaex |
|        | d) Lineplot     | 793 | ms | 475 | ms | 22.7 | s | Modin |
|        | e) Histogram    | 1.61 | s | 11.8 | s | 28.3 | s | Pandas |
|        | f) Heatmap      | 26 | s | 29.1 | s | 20.8 | s | Vaex |

For Wall Time, Vaex shows the best performance for reading and loading dataset.Vaex uses lazy evaluation, allowing it to efficiently handle large datasets without loading them entirely into memory. Pandas shows the shortest execution time when dealing with operations. Whereas Modin demonstrate the shortest time in EDA Visualization. 

### CPU Time

| Number | Task/Function | Pandas | UoM | Modin | UoM | Vaex | UoM | Winner   |
| ------ | ------------- | ------ | --- | ----- | --- | ---- | --- | -------- |
| 1      | Read file      | 67     | s   | 7.76  | s   | 2.17 | s   | Vaex     |
| 2      | Data Understanding | | | | | | |          |
|        | a) Display first 5 rows | 186 | µs | 1.34  | ms  | 970  | µs | Pandas   |
|        | b) Display information  | 12.5 | ms | 83.5  | ms  | 1.71 | s  | Pandas   |
|        | c) Display descriptive statistics | 7.55 | s | 38  | ms  | 266 | s  | Modin    |
| 3      | Count           | | | | | | |             |
|        | a) Count number of rows | 23 | µs | 61   | µs  | 25  | µs | Pandas   |
|        | b) Count the non-null values in a variable | 15.2 | ms | 63.4 | ms | 11.6 | s | Pandas   |
| 4      | Mean            | | | | | | |               |
|        | a) Calculate mean of an int64 variable | 25.2 | ms | 62.7 | ms | 12  | s | Pandas   |
|        | b) Calculate mean of a float64 variable | 33.2 | ms | 45.3 | ms | 12.4 | s | Pandas   |
| 4      | Standard Deviation | | | | | | |           |
|        | a) Calculate std deviation of an int64 variable | 67 | ms | 48.9 | ms | 12.9 | s | Modin    |
|        | b) Calculate std deviation of a float64 variable | 108 | ms | 42.9 | ms | 12.8 | s | Modin    |
| 5      | Sum columns     | 40.3 | ms | 21   | ms  | 191 | µs | Vaex     |
| 6      | Sum columns mean | 70   | ms | 99.1 | ms  | 19.2 | s | Pandas   |
| 7      | Value Counts    | 129  | ms | 70   | ms  | 12.4 | s | Modin    |
| 8      | Group-by        | | | | | | |                |
|        | a) Multiple aggregation | 1.49 | s | 803 | ms | 32.1 | s | Modin    |
|        | b) Mean aggregation | 1.08 | ms | 101 | ms | 28.7 | s | Pandas   |
|        | c) Count aggregation | 11 | s | 13.9 | ms | 27.9 | s | Modin    |
| 9      | Join            | 5.7 | s | 12.3 | ms | 13.9 | s | Modin    |
| 10     | EDA Visualization | | | | | | |               |
|        | a) Barplot       | 408 | ms | 333 | ms | 508 | ms | Modin    |
|        | b) Boxplot       | 26.3 | s | 1   | s  | 15  | s  | Modin    |
|        | c) Scatterplot   | 15.6 | s | 15  | s  | 10.2 | s | Vaex     |
|        | d) Lineplot      | 798 | ms | 527 | ms | 36.4 | s | Modin    |
|        | e) Histogram     | 1.69 | s | 1.72 | s | 42.9 | s | Pandas   |
|        | f) Heatmap       | 25.7 | s | 23.3 | s | 31.2 | s | Modin    |

For CPU Time, similarly Vaex shows the best performance for reading and loading dataset. Howevers, Modin shows the shortest execution time both when dealing with operations and EDA Visualization. 

## Conclusion
In conclusion,  Pandas may be more suitable for smaller datasets that fit comfortably in memory, while Modin and Vaex are designed for larger datasets that may not fit in memory. Since our chosen data only around 2 to 3 GB, Pandas might be faster in view of the Wall Time. The choice depends on specific use cases and requirements. For exploratory data analysis on smaller datasets, Pandas may be sufficient. For larger datasets, Modin and Vaex offer performance improvements.
