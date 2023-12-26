# Performance Comparison: Pandas vs Dask vs Koalas

## Data Cleaning Performance Benchmark
<div align="center">
  
| Cleaning Operation                        | Pandas (µs) | Dask (ms) | Koalas (µs) |
|-------------------------------------------|------------|----------|------------|
| Data Type Optimization                    | 8.11       | 0        | 8.58       |
| Dropping Rows with Significant NaN        | 8.34       | 8.34     | 7.87       |
| Missing Value Replacement                 | 9.06       | 61110     | 7.63       |
| Identifying Duplicate Rows                | 8.34       | 0        | 8.34       |
| Drop Duplicate Column                     | 6.68       | 8.11     | 0.973      |


</div>
Data Type Optimization:<br><br>

Pandas and Koalas have similar execution times for data type optimization (8.11 µs and 8.58 µs, respectively).
Dask has an extremely low execution time (0 ms), suggesting that it might handle this operation very efficiently.<br><br>
Dropping Rows with Significant NaN:

Pandas and Koalas have comparable execution times for dropping rows with significant NaN (8.34 µs and 7.87 µs, respectively).
Dask has a non-zero execution time (8.34 ms), indicating that it takes some time for this operation.<br><br>
Missing Value Replacement:

Pandas has the lowest execution time (9.06 µs) for missing value replacement.
Koalas has a reasonable execution time (7.63 µs).
Dask, on the other hand, has a significantly higher execution time (61110 ms or 61.11 seconds), suggesting that it might not be efficient for this specific operation.<br><br>
Identifying Duplicate Rows:

Pandas and Koalas have similar execution times for identifying duplicate rows (8.34 µs).
Dask has an extremely low execution time (0 ms), indicating efficient handling of this operation.<br><br>
Drop Duplicate Column:

Pandas has the lowest execution time (6.68 µs) for dropping a duplicate column.
Koalas also has a low execution time (0.973 µs).
Dask has a higher execution time (8.11 ms), suggesting that it might not be as efficient for this specific task.

<br><br>

## Exploratory Data Analysis and Visualization
<div align="center">
  
| chart | Pandas (µs) | Dask (s) | Koalas (µs) |
|--------------------|------------|----------|------------|
| Chart1             | 9.06       | 5.96     | 5.96       |
| Chart2             | 9.06       | 7.15     | 7.15       |
| Chart3             | 8.34       | 8.11     | 8.11       |

</div>
Chart1:

Pandas and Koalas have nearly identical performance for Chart1 (9.06 µs and 5.96 µs, respectively).
Dask also performs well but has a slightly higher execution time (5.96 s), indicating that, for this specific chart, Dask might have a longer runtime compared to Pandas and Koalas.<br><br>
Chart2:

Similar to Chart1, Pandas and Koalas show similar performance for Chart2.
Dask has a higher execution time (7.15 s), suggesting that it might be less efficient for this specific chart.<br><br>
Chart3:

Pandas, Dask, and Koalas all have comparable performance for Chart3.
The execution times are relatively close, with Dask having a slightly higher time, suggesting that the choice of library may not significantly impact performance for this chart.

<br><br>
## Answering Question
<div align="center">
  
|      Question      | Pandas (µs) | Dask (s) | Koalas (µs) |
|--------------------|------------|----------|------------|
| Question1          | 9.06       | 33.6     | 5.96       |
| Question2          | 9.06       | 29.2     | 7.15       |
| Question3          | 8.34       | 0.086    | 8.11       |
| Question4          | 7.22       | 0.467    | 5.22       |


</div>
Question1:

Pandas and Koalas have relatively similar performance (9.06 µs and 5.96 µs, respectively).
Dask shows a higher execution time (33.6 s) compared to Pandas and Koalas, indicating that for this specific operation, Dask might not be the optimal choice.
<br><br>
Question2:

Similar to Question1, Pandas and Koalas have comparable performance.
Dask, however, has a higher execution time (29.2 s), suggesting that it may not be as efficient for this operation.
<br><br>
Question3:

Pandas has the highest execution time (8.34 µs), indicating that it performs better for this specific cleaning operation compared to Koalas and Dask.
Dask shows an extremely low execution time (0.086 s), which might be an outlier or a result of Dask's parallel processing capabilities.
<br><br>
Question4:

Koalas has the lowest execution time (5.22 µs) for this operation, outperforming both Pandas and Dask.
Dask has a relatively low execution time (0.467 s) compared to Question1 and Question2, indicating that it might be better suited for this particular cleaning task.

<br><br>
     1. Unable to execute since Dask does not have function to check for duplicates value <br>
     2. We can see from the table Dask library is the most computational time use



<br><hr>


| **Library** | **Strengths** | **Considerations** |
|-------------|---------------|--------------------|
| **Pandas**  | - Well-established and widely used in the data science community. <br> - Excellent for smaller to moderately sized datasets in memory. <br> - Comprehensive functionality for data manipulation. | - Operates in-memory, limiting large dataset handling. <br> - Performance degradation with extensive computations on big data. |
| **Dask**    | - Designed for parallel and distributed computing. <br> - Scales from a single machine to a cluster. <br> - Supports lazy evaluation for complex workflows. | - Overhead in performance for smaller datasets. <br> - Learning curve, especially for Pandas users transitioning to Dask. |
| **Koalas**  | - Bridges Pandas and Apache Spark, providing a Pandas-like API. <br> - Scales code easily to larger datasets using Spark. <br> - Integrates well with PySpark and SparkSQL workflows. | - Performance may not be as efficient as native Spark for some operations. <br> - Not all Spark functionalities may be directly accessible through Koalas. |

## Conclusion

- **For Small to Medium-sized Data:**
  - If your dataset comfortably fits into memory, Pandas is likely the most straightforward and efficient choice.

- **For Large-scale Data:**
  - Dask and Koalas are designed for scenarios where data is too large to fit into memory. Dask is more general-purpose, while Koalas leverages the power of Apache Spark.

- **Consider Your Use Case:**
  - The best choice depends on your specific use case, infrastructure, and the size of your data. Evaluate each tool based on performance requirements, scalability needs, and ease of integration.

In summary, the choice between Pandas, Dask, and Koalas depends on the scale of your data and the specific requirements of your analysis or processing tasks. Each tool has its own niche, and understanding your use case will help you make an informed decision. Always consider the latest updates and community feedback when making choices, as these libraries evolve over time.

