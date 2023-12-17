# Assignment 6 by Thruth Seeker

<a target="_blank" href="https://colab.research.google.com/github/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/Thruth%20Seeker/Assignment_6_by_Thruth_Seeker.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Hazem Fenneer            |MCS231019      |
| Shivanesh A/L Sivakumar               |MCS231014      |

**Dealing with large datasets poses challenges in terms of memory efficiency and processing speed. In this exploration, we'll employ five smart strategies to effectively manage substantial datasets**

1. Load Less Data
2. Use Chunking
3. Optimize Data Types
4. Sampling
5. Parallelize with Dask

## Comprehansive analysis
#### In Terms of Approach:
| Strategy | Time (in seconds) | Memory Usage (in Miga Byte) | Analysis|      
|----------|------|--------------|---------|
|Traditional(pandas)|35.2|1087|Uses pandas for data manipulation, takes longer time and higher memory usage.|
|Load Less Data|27.3|973.3|Optimizes by loading only necessary data, reducing both time and memory usage.|
|Optimize Data Types|19|1000.5|Optimizing data types contributes to a significant time reduction, but memory usage remains high.|
|sample (random)|23.1|3.1|Uses random sampling, significantly reduces memory usage, moderately improves time.|
|sample (percentage_sample)|22.3|549.8|Uses a percentage-based sample, which reduces memory usage and slightly improves time.|
|Parallelize with Dask|2.9|190.7|Utilizes Dask for parallel processing, resulting in a substantial reduction in both time and memory usage.|
|Chunking|33.3|674.91|Chunking the data shows a trade-off with higher time and lower memory usage compared to the traditional approach.|

#### Pros and Cons
| Technique                        | Pros                                           | Cons                                                         |
| ---------------------------------|-----------------------------------------------|--------------------------------------------------------------|
| Traditional (pandas)             | - Familiar and widely used.                   | - High time consumption.                                      |
|                                  | - Comprehensive functionality.                 | - High memory usage for large datasets.                       |
| Load Less Data                   | - Reduced time by loading only necessary data. | - Limited scope for analysis on the entire dataset.           |
|                                  | - Moderate impact on memory.                   | - Potential information loss.                                  |
| Optimize Data Types              | - Significant reduction in processing time.   | - Limited impact on memory usage.                              |
|                                  | - Improved efficiency in memory usage.        | - May require careful handling of data type conversions.     |
| Sample (Random)                  | - Balanced approach to time and memory usage.  | - Potential for non-representative samples.                   |
|                                  | - Preserves random data distribution.         | - Limited control over sample characteristics.               |
| Sample (Percentage-based Sampling)| - Maintains a good balance between time and memory. | - Possible bias depending on the sampling technique.         |
|                                  | - Allows for controlled sampling.              | - May not capture rare events well.                           |
| Parallelize with Dask            | - Substantial reduction in both time and memory usage. | - Learning curve for Dask usage.                            |
|                                  | - Scalable for large datasets.                 | - Overhead associated with parallelization.                   |
| Chunking                         | - Reduced memory usage compared to traditional approach. | - Increased processing time due to chunking overhead.      |
|                                  | - Allows processing of large datasets in smaller, manageable chunks. | - Requires careful consideration of chunk size for optimal results. |

## Conclustion

In handling big data, various strategies present trade-offs between processing time and memory usage. Traditional approaches like pandas may struggle with large datasets, resulting in prolonged processing times and high memory consumption. Optimization techniques, sampling methods, and chunking offer intermediate solutions, balancing time and memory, but they come with their own limitations and considerations.

For substantial gains in efficiency, parallelization with tools like Dask emerges as a powerful solution, delivering significant reductions in both processing time and memory requirements. Despite the learning curve and associated overhead, the scalability of parallelization makes it a compelling choice for large-scale data processing. The most effective strategy depends on the specific analysis requirements, available computing resources, and acceptable trade-offs between time and memory in the context of handling extensive and intricate datasets.
