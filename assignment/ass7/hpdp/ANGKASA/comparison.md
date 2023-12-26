<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# **Assignment 7: Comparison Between Libraries (Pandas, Vaex & Dask)**

<div align="center">
  
### Group Members:
|No.|NAME|MATRICS NO.|
|---|---|---|
|1.|FAUZAN AQIL BIN AZMAN|A20EC0078|
|2.|NIK AMIRUL ARIFF BIN AMRAN|A21EC0214|
|3.|MUHAMMAD ASHRAAF BIN SALEH|A21EC0068|
|4.|MUHAMMAD NAQUIB BIN ZAKARIA|A20BE0161|

</div>

## **Dataset: Chess Game** ♟️

This dataset contains 6.25 Million chess games played on lichess.org during July of 2016. This dataset is around 4 GB. Some of the games have Stockfish analysis evaluations like* [%eval 2.35] (235 centipawn advantage)* always from White's point of view. These are evaluations of the movement made by a player.

| Column | Description |
| :----: | :---------: |
| Event | Game type |
| White | White's ID |
| Black | Black's ID |
| Result | Game Result (1-0 White wins) (0-1 Black wins) |
| UTCDate | UTC Date |
| UTCTime | UTC Time |
| WhiteElo | White's ELO |
| BlackElo | Black's ELO |
| WhiteRatingDiff | White's rating points difference after the game |
| BlackRatingDiff | Blacks's rating points difference after the game |
| ECO | Opening in ECO encoding |
| Opening | Opening name |
| TimeControl | Time of the game for each player in seconds. The number after the increment is the number of seconds before the player's clock starts ticking in each turn |
| Termination | Reason of the game's end |
| AN | Movements in Movetext format |

## Library 1: **Pandas**

<div align="center">
  
![illu_pandas-82-1024x562](https://github.com/drshahizan/Python-big-data/assets/146650043/e0835bec-1827-4984-ab3e-4abe216b34cc)

</div>

Pandas is a powerful data manipulation and analysis library for Python. It provides easy-to-use data structures and functions for efficiently handling structured data, making it an essential tool for data scientists, analysts, and researchers.

### Advantages of Pandas
- **Data Structures:**
  - Pandas introduces two primary data structures: Series and DataFrame, which are designed to handle one-dimensional and two-dimensional data, respectively.
- **Data Cleaning and Transformation:**
  - Pandas simplifies data cleaning tasks, offering functions for handling missing values, filtering, and transforming data.
- **Indexing and Selection:**
  - Efficiently select, filter, and manipulate data using label-based indexing, slicing, and Boolean indexing.
- **Statistical and Mathematical Operations:**
  - Perform statistical and mathematical operations on data with ease, including mean, median, sum, and more.
- **Integration with NumPy:**
  - Seamlessly integrates with NumPy, enabling interoperability between Pandas DataFrames and NumPy arrays.
- **Time Series Data:**
  - Robust support for time series data, including date/time indexing and resampling functionalities.
- **IO Tools:**
  - Read and write data from various file formats, such as CSV, Excel, SQL databases, and more.
- **Visualization:**
  - Integrated plotting capabilities for quick data visualization, built on top of Matplotlib.
<be>

## Library 2: **Veax**

<div align="center">

![1639567859424](https://github.com/drshahizan/Python-big-data/assets/146650043/7d66bef8-fbc2-49ce-b89e-ee5a5cce278b)

</div>

Vaex is a Python library for lazy, out-of-core DataFrames. It is designed to efficiently handle and analyze extremely large datasets that may not fit into memory.

- **Key Features:**
  - Lazy and out-of-core computation: Vaex computes on the fly, minimizing memory usage.
  - Fast and memory-efficient: Optimized for speed and minimal memory footprint, making it suitable for large-scale datasets.
  - DataFrame API: Vaex provides a familiar pandas-like API for easy integration into existing workflows.

### Advantages of Vaex

- **Efficient Memory Usage:**
  - Vaex's lazy computation allows it to efficiently handle datasets larger than available RAM.
- **High Performance:**
  - Vaex is designed for speed, leveraging parallel and vectorized operations for quick data manipulations.
- **Ease of Use:**
  - With a DataFrame API similar to pandas, Vaex is easy to pick up for users familiar with pandas syntax.
- **Out-of-Core Computation:**
  - Vaex operates seamlessly with data that is too large to fit into memory, processing it in chunks.
<be>

## Library 3: **Dask**

<div align="center">

![512px-Dask_Logo](https://github.com/drshahizan/Python-big-data/assets/146650043/93bcd891-4769-426b-959e-837cd7d78342)

</div>

Dask is a parallel computing library in Python that seamlessly integrates with pandas, NumPy, and other Python libraries. It allows users to scale their computations from a single machine to large clusters, making it ideal for handling large datasets.

### Advantages of Dask
- **Scalability:**
  - Dask enables parallel and distributed computing, providing scalability for computations beyond the limits of a single machine.
- **Integration:**
  - It integrates well with existing Python libraries, allowing users to leverage Dask's capabilities without a steep learning curve.
- **Lazy Evaluation:**
  - Dask uses lazy evaluation, which builds up a task graph to represent computations before executing them. This allows for efficient execution plans.
- **Out-of-Core Computing:**
  - Dask can handle datasets that do not fit into memory by utilizing out-of-core computing and processing data in chunks.

## Comparative Analysis
- Time to load data :clock1:
  - The time to load data refers to the duration it takes to read and load a dataset into memory for further processing or analysis. The loading time can be a critical factor, especially when dealing with large datasets, and it depends on various factors including the size of the dataset, the format of the data, and the capabilities of the software or libraries used for loading. Below is the comparison between the time taken to load the data before the optimization for each library:

<div align="center">
  
| No. | Libraries | Time taken (seconds) |
|---|---|---|
|1.| Pandas | 47.67546 |
|2.| Vaex |  |
|3.| Dask | 0.03214 |
  
</div>

- Computation time 📊
  - Computation time, also known as execution time or runtime, refers to the time it takes for a computer program or algorithm to complete its execution. It is a critical metric in evaluating the efficiency and performance of software, and it is often measured in seconds, milliseconds, or microseconds. Below is the comparison between the computation time for each library for the calculation and visualization:

<div align="center">
  
| No. | Operation | Pandas Time (seconds) | Vaex Time (seconds) | Dask Time (seconds) |
| --- | --- | --- | --- | --- |
| 1. | Compute statistic summaries | 1.16429 |  | 146.04489 |
| 2. | Facet Grid | 0.88007 |  | 147.20021 |
| 3. | Histogram | 1.64682 |  | 147.05568 |
 
</div>

- Memory Usage 📤
  - Memory usage refers to the amount of computer memory (RAM - Random Access Memory) that a program or process utilizes at a specific time. Memory is a critical resource in computing, and how efficiently it is managed can significantly impact the performance and responsiveness of a system. Below is the comparison between the memory usage for each library after the data is loaded into dataframe and has done some computation and visualization for which we will use a histogram as our sample: 

<div align="center">
  
| No. | Libraries | Memory use (GB) |
|---|---|---|
|1.| Pandas | 0.27385 |
|2.| Vaex |  |
|3.| Dask | 0.74580 |
 
</div>

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
