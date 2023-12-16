## Big Data Management Assignment 6: Mastering Big Data Handling
### Group Name: Avengers
### Dataset: Amazon Book Reviews
### Date: 9th December, 2023
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| ISMAIL MAEEN FATEH ALLAH YAQOT ALAWAMI   |  MCS221028    |   
|LWANGA AKSAM              |  MCS231016    |
|BAKUNGA BRONSON             |   MCS232006   |  



---

### Abstract

This report explores various strategies for managing big data processing, focusing on the "Amazon Book Reviews" dataset. It assesses each strategy's effectiveness in terms of memory usage, computation time, and file size, providing step-by-step instructions for their implementation.

---

### Table of Contents

1. Introduction
2. Dataset Overview
3. Methodology
4. Results and Discussion
   1. Basic Data Processing with Pandas
   2. Chunk-Based Processing
   3. Data Type Optimization
   4. Sampling
   5. Parallel Processing with Dask
5. Comparative Analysis
6. Conclusion
7. References

---

### 1. Introduction

Efficiently managing large datasets is a critical challenge in data science. This report examines different strategies for processing the "Amazon Book Reviews" dataset to determine the most efficient methods.

---

### 2. Dataset Overview

The primary dataset under study is "Amazon Book Reviews," approximately 2.7GB in size. This dataset includes a wealth of information, encompassing diverse data points such as ratings, reviews, and user information, which presents a typical large dataset challenge in big data scenarios. 

In addition to the "Books_rating.csv" file from the "Amazon Book Reviews" dataset, a second dataset named "books_data.csv" was also utilized. This complementary dataset provided additional information that was essential for a more comprehensive analysis. Together, these two datasets represent a typical scenario in big data processing where multiple data sources are combined to extract more nuanced and valuable insights.

The integration of these datasets underscores the challenges and complexities often encountered in big data management, particularly when dealing with various data types and large volumes of information. The analysis of these datasets provides a robust framework for exploring and evaluating different data handling strategies, making it an exemplary case study in the field of big data analytics.

---

### 3. Methodology

The study employs various strategies, from basic Pandas operations to advanced Dask processing, evaluating their effectiveness based on computation time, memory usage, and file size.

---

### 4. Results and Discussion

#### 4.1 Basic Data Processing with Pandas

- **Steps**:
  1. Import Pandas library.
  2. Load datasets using `pd.read_csv`.
  3. Merge datasets using `pd.merge`.
- **Computation Time**:
  - Loading "Books_rating.csv": 30.3 seconds
  - Loading "books_data.csv": 2.39 seconds
  - Merging DataFrames: 846 milliseconds
  - Sentiment Analysis: 3 minutes 53 seconds
-  **Memory Usage**: Approximately 8.13 GB
-  **Memory Reduction**: Not applicable, as this represents the initial dataset size.
- **Discussion**: Basic data processing with Pandas is straightforward but can be memory-intensive. This approach is ideal for datasets that comfortably fit into memory. However, for larger datasets, as seen with "Books_rating.csv," it can lead to longer loading times. Merging large datasets can also be computationally expensive, but Pandas provides an easy-to-use interface for such operations.

#### 4.2 Chunk-Based Processing

- **Steps**:
  1. Import Pandas library.
  2. Load data in chunks using `pd.read_csv` with the `chunksize` parameter.
  3. Process each chunk individually.
- **Computation Time**: Not explicitly measured but generally more efficient than loading entire dataset.
- **Memory Usage**: Varies depending on the chunk size. Significantly less than loading the entire dataset into memory at once.
- **Discussion**: Chunk-based processing is a practical approach to handle datasets that are too large to fit into memory. By breaking the dataset into smaller, manageable parts, it becomes possible to perform computations that would otherwise be infeasible. This method is particularly effective for large datasets but requires careful management of each chunk to ensure consistency and completeness of the analysis.

#### 4.3 Data Type Optimization

- **Steps**:
1.  Inspect data types of the DataFrame columns.
2.  Identify columns that can be converted to more memory-efficient types.
3.  Perform specific data type conversions:
    -   Convert `Price`, `review/score`, and `ratingsCount` columns from `float64` to `float32` to reduce memory usage.
    -   Convert string columns like `Id`, `Title`, `User_id`, `profileName`, `review/helpfulness`, `review/summary`, `review/text`, `description`, `authors`, `image`, `previewLink`, `publisher`, `publishedDate`, `infoLink`, and `categories` to `category` type if they have a limited number of unique values compared to the size of the dataset.
4.  Apply these changes to the DataFrame to optimize overall memory usage.
-   **Memory Usage**: Reduced to approximately 3.34 GB after optimization.
-   **Memory Reduction**: Approximately 58.87% reduction from the original memory usage.
- **Discussion**: Optimizing data types is a crucial strategy in managing memory usage for large datasets. By converting data to more efficient types, the overall size of the dataset in memory is reduced, facilitating faster processing. This method is particularly effective when working with datasets that have columns with repetitive or limited unique values, making them ideal candidates for conversion to the `category` type. The reduction in memory footprint can significantly impact the performance of data processing tasks, particularly in environments with limited memory resources.

#### 4.4 Sampling

- **Steps**:
  1. Use `DataFrame.sample` to randomly select a subset of the data.
- **Computation Time**: Significantly faster due to reduced dataset size.
-  **Memory Usage**: Reduced to around 0.76 GB for a 10% sample of the data.
-  **Memory Reduction**: Approximately 90.67% reduction from the original memory usage.
- **Discussion**: Sampling is a powerful technique to reduce the size of the dataset for analysis. By working with a representative subset, we can achieve significant reductions in both memory usage and computation time. However, it's important to ensure that the sample is representative of the entire dataset to maintain the accuracy and reliability of the analysis.

#### 4.5 Parallel Processing with Dask

- **Steps**:
  1. Import Dask library.
  2. Use `dd.read_csv` to load dataframes.
  3. Perform operations like merge using Dask's parallel processing capabilities.
- **Computation Time**:
  - Loading "Books_rating.csv" with Dask: 16.9 milliseconds
  - Loading "books_data.csv" with Dask: 9.7 milliseconds
  - Merging DataFrames: 38 seconds
  - Sentiment Analysis: 43 minutes 8 seconds
-   **Memory Usage**:
    -   "Books_rating.csv" loaded with Dask: 2.7 GB.
    -   "books_data.csv" loaded with Dask: 179.3 MB.
-   **Memory Reduction**: Not directly comparable to Pandas processing, as Dask handles data differently, but demonstrates efficient memory management for larger-than-memory datasets.
- **Discussion**: Parallel processing with Dask is particularly effective for very large datasets, as it enables distributed computing and parallelizes operations across multiple cores. Dask can handle datasets larger than the available memory by breaking them into chunks and processing these chunks in parallel. However, its advantages are most pronounced with very large datasets. For moderately large datasets, such as the one analyzed, Dask's performance gains in complex operations like sentiment analysis may not be as significant as expected.

---

### 5. Comparative Analysis
#### 5.1. Computation times summary
| Strategy                     | Operation                 | Computation Time            |
|------------------------------|---------------------------|-----------------------------|
| Basic Pandas Processing      | Loading, Merging, Analysis| 30.3 s, 2.39 s, 846 ms, 3min 53s |
| Dask Processing              | Loading, Merging, Analysis| 16.9 ms, 9.7 ms, 38 s, 43min 8s  |

#### 5.2. Memory usage summary

| Strategy                     | Memory Usage Before | Memory Usage After | Reduction in Memory Usage |
|------------------------------|---------------------|--------------------|---------------------------|
| Basic Pandas Processing      | 8.13 GB             | N/A                | N/A                       |
| Chunk-Based Processing       | 8.13 GB             | Varies             | Depends on chunk size     |
| Data Type Optimization       | 8.13 GB             | 3.34 GB            | 58.87%                    |
| Sampling                     | 8.13 GB             | 0.76 GB            | 90.67%                    |
| Parallel Processing with Dask| 8.13 GB             | 2.8793 GB          | 64.61%                    |

*Note*: The memory usage before optimization is based on the initial size of the merged datasets. Dask's memory usage represents the combined size of "Books_rating.csv" and "books_data.csv".

- **Observations**: While Dask demonstrated faster initial loading times, it was less efficient for complex operations such as sentiment analysis. Basic Pandas processing, though slower in initial data loading, remained reliable for simpler tasks.

---

### 6. Conclusion

The comparative analysis of different data handling strategies in the context of the "Amazon Book Reviews" dataset reveals significant differences in terms of file size, memory usage, and computation time:

-   **File Size Reduction**: 
	- **Data Type Optimization**: Led to a 58.91% reduction in file size due to more efficient data representation.
-   **Overall Memory Usage Reduction**: The most substantial memory reduction was achieved through Sampling (approximately 90.67%), followed by Data Type Optimization (approximately 58.87%). Chunk-Based Processing doesn't have exact figures as these depend on the chunks use. Dask, with its unique approach to data handling, showed efficient memory usage of 2.7 GB for "Books_rating.csv" and 179.3 MB for "books_data.csv" (64.61% compared to the initial Pandas memory usage.).
-   **Computation Time Reduction**: Dask showed the fastest initial data loading times, but for complex operations like sentiment analysis, it did not necessarily translate to the fastest overall processing times. Basic Pandas Processing, while slower for initial data loading, was more efficient for certain operations but this is only the case for smaller datasets.

These findings underscore the importance of selecting the appropriate data handling strategy based on the specific needs of the dataset and the analysis objectives. Strategies like Sampling and Data Type Optimization are highly effective for reducing memory usage, while Dask is better suited for very large datasets where its parallel processing capabilities can be fully leveraged. Combining several of these techniques can also yield better performance and reduce memory usage when handling big data.

---

### 7. References

- Kaggle Dataset: [Amazon Book Reviews](https://www.kaggle.com/datasets/mohamedbakhet/amazon-books-reviews?select=books_data.csv)
- Pandas Documentation: [pandas documentation — pandas 2.1.4 documentation (pydata.org)](https://pandas.pydata.org/docs/)
- Dask Documentation: [Dask — Dask documentation](https://docs.dask.org/en/stable/)

---