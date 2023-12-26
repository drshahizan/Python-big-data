# Performance Comparison: Pandas vs Dask vs Koalas

## Data Cleaning Performance Benchmark
<div align="center">
  
| **Cleaning Operation**                 | **Pandas (s)** | **Dask (s)** | **Koalas (s)** |
|----------------------------------------|----------------|--------------|----------------|
| Data Type Optimization                | 8.11           | 0            | 8.58           |
| Dropping Rows with Significant NaN    | 8.34           | 0            | 7.87           |
| Missing Value Replacement             | 9.06           | 0            | 7.63           |
| Identifying Duplicate Rows            | 8.34           | 0            | 8.34           |
| Drop Duplicate Column                 | 6.68           | 0            | 0.973          |


<img src="https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass7/hpdp/BROKE/images/download.png" alt="Alt text" width="700"/>
</div>
<br><br>

## Exploratory Data Analysis and Visualization
<div align="center">
  
| chart | Pandas (s) | Dask (s) | Koalas (s) |
|--------------------|------------|----------|------------|
| Chart1             | 9.06       | 5.96     | 5.96       |
| Chart2             | 9.06       | 7.15     | 7.15       |
| Chart3             | 8.34       | 8.11     | 8.11       |

<img src="https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass7/hpdp/BROKE/images/download.png" alt="Alt text" width="700"/>
</div>

<br><br>





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

