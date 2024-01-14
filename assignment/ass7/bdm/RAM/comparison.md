# Assignment 7: Comparison Between Libraries 

### Group Name: RAM

### Group Members
| Name                             | Matric Number |
| :------------------------------- | :-------------:|
|MOHAMMED RAZA ASFAK CHIDIMAR | MCS231004|
|AYAZ RAHMAN BHUIYAN |MCS231023 |
|MUSAB IBNE AHMAD  |MCS231017 |
|HUSSEIN YUSUF SHEIKH MOHAMED |MCS231024 |

## Introduction

Data manipulation and analysis are fundamental tasks in the field of data science, and several Python libraries cater to different aspects of these tasks. This report aims to provide an overview and a comparative analysis of three prominent libraries used for data manipulation and analysis: Pandas, Dask, and Vaex.

### Pandas

Pandas is primarily intended for use with small to medium-sized datasets that can be stored in memory. It is commonly used to manipulate, clean, and analyze data.

#### The advantages and drawbacks of using Pandas

**Advantages**:

**1. Data Representation:**
Pandas provides a DataFrame object, a two-dimensional tabular data structure that allows for easy manipulation and analysis of data. It offers intuitive indexing, column operations, and supports various data types.


**2. Less Write and More Work Done:**
Pandas offers concise and expressive syntax, allowing you to achieve more with less code. It provides a wide range of built-in functions and methods for data manipulation and analysis, reducing the need for manual coding and increasing productivity.

**3. Efficiently Handles Large Data:**
Despite some performance limitations, Pandas is designed to handle large datasets efficiently. With Pandas, you can process and analyze large datasets without compromising on functionality.


**Drawbacks**:

**1. Memory Consumption:**
Pandas can be memory-intensive, especially when working with large datasets. Loading and manipulating large amounts of data may require substantial memory resources, which can be a constraint in environments with limited memory availability.


**2. Performance Limitations:**
While Pandas provides efficient data processing capabilities, certain operations can be slower compared to lower-level libraries like NumPy. For computationally intensive tasks, Pandas may not offer the same level of performance as specialized libraries or custom implementations.

**3. Lack of Support for Real-Time Data:**
Pandas is primarily designed for working with static, structured datasets. It may not be the ideal choice for real-time data processing or streaming data analysis, where other specialized tools or libraries may be more suitable.

### Dask

Dask is designed for parallel computing and scalable data processing. It is suitable for working with larger-than-memory datasets, and it allows users to parallelize operations on these datasets.

#### The advantages and drawbacks of using Pandas

**Advantages**:

**1. Ease of use:** Dask integrates seamlessly with familiar libraries like Pandas and NumPy, making it easy for Python users to get started. The API is similar, so you can simply replace libraries like Pandas with their Dask counterparts and experience parallel processing with minimal code changes.


**2. Scalability:** Dask scales gracefully from single-machine use to large clusters with thousands of cores. It efficiently utilizes available resources, whether on your laptop or a distributed computing environment.


**3. Flexibility:** Dask offers various collections like DataFrames, Arrays, Bags, and Datasets, giving you the flexibility to choose the best fit for your data and workload. It also supports a wide range of operations, including filtering, aggregating, and machine learning algorithms.


**Drawbacks**:

**1. Overhead:** Dask introduces some overhead compared to single-threaded execution, especially for small datasets. The benefits of parallelization might not outweigh the overhead for certain tasks.


**2. Limited functionality:** Dask lacks some features available in dedicated big data processing frameworks like Spark. For instance, its SQL engine is still under development, and its integration with other ecosystems like Hadoop is not as extensive.


**3. Limited stateful operations:** Dask collections are mostly immutable, meaning you can't modify existing data in-place. This can be inconvenient for certain workflow patterns.


### Vaex

Vaex is designed for high-performance, out-of-core dataframes that allow users to work with datasets that are larger than the available RAM.

**Advantages**:

**1. Performance:**
Vaex is known for its excellent performance on large datasets. It employs memory mapping and lazy evaluation, resulting in fast and efficient operations.


**2. Memory Efficiency:**
Vaex loads only the necessary portions of the data into memory, making it memory-efficient when dealing with large datasets.

**3. Ease of Use:**
Vaex provides a similar API to Pandas, making it easy for users familiar with Pandas to transition to Vaex.


**Drawbacks**:

**1. Limited Functionality:**
Vaex does not support the full range of Pandas operations. Some features available in Pandas may not be present in Vaex.

**2. Less Resources:**
Vaex, while gaining popularity, may have a smaller community compared to Pandas. This can result in fewer online resources and community support.

**3. Complex Queries:**

Writing complex queries in Vaex might be less intuitive compared to Pandas, as Vaex relies heavily on expressions.


## Comparative Analysis

### Execution Time


In the execution time analysis, Pandas outperformed both Vaex and Dask, completing the task in a notably shorter time frame (4 s). Pandas, optimized for in-memory processing, excels with smaller to medium-sized datasets that fit into memory. Dask, designed for parallel and distributed computing, showed a moderately longer execution time (21 s), reflecting its ability to handle larger-than-memory datasets efficiently. Vaex, which took the longest time (46.30 s), specializes in out-of-core processing for large datasets, and the extended execution time may be attributed to the inherent overhead of reading and processing data in this manner. The optimal choice among these libraries depends on the specific characteristics and size of the dataset, with Pandas offering swift performance for in-memory tasks, while Dask and Vaex become more advantageous for larger datasets that demand distributed or out-of-core processing.


### Memory Usage

In the memory consumption analysis, Vaex exhibited the highest usage, consuming 2.1 GB, reflective of its out-of-core design for efficient handling of large datasets. Pandas demonstrated the lowest memory footprint at 380 MB, leveraging its in-memory processing optimization. Dask fell in between, consuming 1.2 GB, showcasing its scalability for larger-than-memory datasets. The choice among these libraries should consider both the available memory resources and the specific characteristics of the dataset, with Vaex excelling in out-of-core scenarios, Pandas in in-memory tasks, and Dask providing a balance for scalable computations.



## Conclusion

In conclusion, the choice between Vaex, Pandas, and Dask should be driven by the specific characteristics of the dataset and the requirements of the task. If dealing with relatively small datasets that fit into memory, Pandas stands out for its swift execution and rich functionality. Dask proves valuable when scalability is essential, handling larger-than-memory datasets efficiently. On the other hand, Vaex shines in scenarios where extreme memory efficiency is paramount, particularly when working with massive datasets that surpass available RAM. The decision should align with the trade-offs between memory consumption, execution time, and the scale of the dataset, and it might involve a strategic use of multiple libraries within different stages of the data analysis pipeline.


