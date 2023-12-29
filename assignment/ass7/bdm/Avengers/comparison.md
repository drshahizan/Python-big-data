# Big Data Management Assignment 7: Comparison between libraries
### Group Name: Avengers
### Dataset: Amazon Book Reviews
### Date: 24th December, 2023
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Ismail Maeen Fateh Allah Yaqot Alawami   |  MCS221028    |   
|LWANGA AKSAM              |  MCS231016    |
|BAKUNGA BRONSON             |   MCS232006   |  

# Comparison Report: Modin, Pandas, and Vaex
<p align="center">
<img src="https://github.com/drshahizan/Python-big-data/assets/51344005/94029d81-a904-48b1-a13c-6c5578e05990" alt="MODIN_ver2_hrz" width="220"/>
<img src="https://github.com/drshahizan/Python-big-data/assets/51344005/e266e658-957e-4aac-9e18-320e389d6032" alt="icons8-pandas" width="120"/>
<img src="https://github.com/drshahizan/Python-big-data/assets/51344005/c91e6854-d769-4a69-9be2-c0be322a9f92" alt="vaex" width="120"/>
</p>

## Introduction
This comprehensive report compares Modin with Ray backend, Pandas, and Vaex in data processing and exploratory data analysis (EDA). The focus is on their performance in memory usage, time efficiency, and compatibility with standard data analysis practices.

**Observation**: It should also be noted that Modin with the Dask backend failed to load the datasets because it was spending more than 95% of it's memory budget which is the reason it is not included in this report.

## Data Loading and Memory Usage

### Memory Usage Comparison
Memory usage is critical, especially when handling large datasets. The use of `psutil` offers a broader view of memory consumption, including the memory used by the Python interpreter and all loaded libraries, not just the DataFrame itself.

| Library | Operation           | Memory Used by psutil (MB) | Memory Used by .memory_usage() (GB) |
|---------|---------------------|----------------------------|-------------------------------------|
| Pandas  | Load Data (Ratings) | 4108.00                    | 3.7414                              |
|         | Load Data (Books)   | 213.16                     | 0.2872                              |
| Vaex    | Load Data (Ratings) | 4115.19                    | -                                   |
|         | Load Data (Books)   | 226.06                     | -                                   |
| Modin   | Load Data (Ratings) | -66.09                     | 3.7414                              |
|         | Load Data (Books)   | 22.83                      | 0.2872                              |


The negative memory value reported by psutil for Modin when loading the ratings dataset could be due to memory being freed up during the operation, possibly because of memory optimization techniques employed by Modin, such as lazy evaluation or because it might be offloading some of the data to disk.
Vaex also fails to run the ```.memory_usage()``` method as it is not present. This was a reoccurring event for Vaex in general as it lacks a lot of the Pandas APIs.

**Observation**: Vaex shows significant memory usage. Modin demonstrates efficient memory management.

## Compatibility with Pandas and Numpy
Conversion needs for specific operations highlight a library's integration with the broader Python data science ecosystem:

| Library | Operations Needing Conversion                     |
|---------|---------------------------------------------------|
| Vaex    | Visualizations, Word Clouds, Correlation Matrices |
| Modin   | Complex Visualizations, Statistical Computations  |

### Example showing different code adaptations for each library
- Pandas
<img width="808" alt="image" src="https://github.com/drshahizan/Python-big-data/assets/51344005/aa0245ad-e1fa-4d61-8534-63e91d3f95c7">

- Vaex
<img width="808" alt="image" src="https://github.com/drshahizan/Python-big-data/assets/51344005/7ffa370c-31f4-4fdb-9ba1-4bf98564fd29">

- Modin
<img width="808" alt="image" src="https://github.com/drshahizan/Python-big-data/assets/51344005/4d76296e-39f0-4fcd-8fef-dd5adff80a26">

### Operations that failed
Vaex in particular was very hard to work with with in terms of adapting the existing EDA done in Pandas to it. For example, a grouping operation failed and resulted in the inability to generate the temporal analysis of section.
<img width="777" alt="image" src="https://github.com/drshahizan/Python-big-data/assets/51344005/5a7b9a55-f2d5-4e0e-99b0-cbbe3826a902">


## Operational Efficiency and Performance

### Time Comparison for Key Operations
Timing metrics provide insight into the computational performance of data processing tasks. The analysis of timing data can reveal which operations may become bottlenecks as data volume scales up.

- User Time: The time CPU spends in user-mode executing the process code (excluding system calls).
- System Time: The time CPU spends in kernel-mode within system calls on behalf of the process.
- Total CPU Time: The sum of user time and system time.
- Wall Time: The real time from start to finish of the call, as it would have been measured by a wall clock, including time spent waiting for system resources.
In summary, user and system times help us understand CPU-bound efficiency, while wall time gives a real-world measure of elapsed time, often influenced by both CPU processing and waiting for I/O operations. This distinction is key when optimizing for performance, as user and system times can guide us on computational optimizations, while wall time may point towards I/O bottlenecks.

Insights into the real-world performance of these libraries:

| Library | Operation                       | Wall Time (s) |
|---------|---------------------------------|---------------|
| Modin   | Data Merge                      | 0.385         |
|         | Descriptive Stats               | 0.00877       |
| Pandas  | Data Merge                      | 0.516         |
|         | Descriptive Stats (Ratings)     | 0.152         |
| Vaex    | Data Merge                      | 1.11          |
|         | Descriptive Stats (Ratings)     | 1.33          |

### Time Analysis
Analyzing time reductions between these libraries for specific operations:

- **Data Merge**: Modin reduces time by approximately 25% compared to Pandas.
- **Descriptive Statistics**: Modin and Vaex show varying degrees of efficiency, with Modin being significantly faster.

**NOTE:** For detailed breakdown of times refer to the Timing Metrics Analysis table at the end of each library's notebook.
- Pandas: [View Notebook](Pandas.ipynb)
- Vaex: [View Notebook](Vaex.ipynb)
- Modin: [View Notebook](Modin(Ray).ipynb)

### Memory Analysis
Evaluating memory efficiency:

- **Vaex**: Its higher memory usage is suited for very large datasets.
- **Modin**: Shows signs of efficient memory usage, beneficial for large-scale data processing tasks.

## Conclusion
In the comparative evaluation of Modin (with Ray backend), Pandas, and Vaex, we have scrutinized the performance of these libraries across various dimensions such as memory usage, time efficiency, and compatibility with standard data analysis practices.

Memory usage, particularly for handling large datasets, is crucial for efficiency and avoiding system strain. The data indicates that Pandas is relatively memory-intensive. Modin showcases efficient memory management, which is evident from the negative memory usage reported by psutil, suggesting advanced memory handling through techniques like lazy evaluation or disk offloading. Vaex demonstrates a strong approach to memory usage suitable for large datasets but does not implement the .memory_usage() method, showing a limited compatibility with the Pandas API.

The compatibility with Pandas and NumPy is essential for ease of adoption and integration into existing workflows. Here, Vaex falls short, missing several Pandas APIs, necessitating conversions for common operations such as visualizations, and failing to perform group operations required for certain visualizations. Modin offers better compatibility but still requires conversion for complex operations and statistical computations.

Operational efficiency is assessed through the time performance of key operations, where Modin surpasses Pandas and Vaex in data merging and computation of descriptive statistics, suggesting superior scalability and suitability for tasks where time is of the essence. Despite its slower performance in these operations, Vaex's handling of extremely large datasets—those that exceed memory capacity—remains its strong suit due to its memory mapping techniques.

- Vaex, while powerful for its out-of-core data processing capabilities suitable for enormous datasets, falls behind when it comes to tasks requiring group operations, which are fundamental for many EDA visualizations.
- Modin excels in performance with its Ray backend, standing out for distributed data processing tasks that demand speed and efficient memory utilization.
- Pandas continues to be the standard for a broad range of data processing needs, offering a rich feature set and ease of use but at the cost of higher memory usage.

The appropriate selection of a data processing library is pivotal and should be tailored to the task requirements. Pandas is recommended for general data processing, Modin for performance-critical and large-scale data tasks, and Vaex for situations where its unique ability to handle very large datasets can be fully utilized, albeit with the noted limitations in API compatibility and group operation functionality.
