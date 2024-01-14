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

Data manipulation and analysis are essential in data science, and various Python libraries specialize in various aspects of these tasks. This report aims to present a concise and detailed analysis of three widely recognized libraries, Pandas, Dask, and Vaex, which are commonly used for data manipulation and analysis. The report will offer an overview of these libraries and conduct a comparison analysis between them.


### Pandas

Pandas is mainly used for datasets of small to medium size that can be stored in computer memory. It is frequently used to modify, cleanse, and analyze data.


#### The advantages and drawbacks of using Pandas

**Advantages**:

**1. Data Representation:**
Data Representation: Pandas offers a DataFrame object, a structured data format with two dimensions that allow straightforward manipulation and data analysis. The tool provides user-friendly indexing and column manipulation features and is compatible with various data types.


**2. Increased Efficiency:**
Pandas provides a brief and comprehensive syntax, helping users to execute more with minimal code. The tool offers extensive pre-built algorithms and methods for manipulating and analyzing data, minimizing human coding requirements, and enhancing efficiency.


**3. Efficiently Handles Large Datasets:**
Pandas has been optimized to manage large datasets effectively but may have some performance constraints. Pandas offers efficient processing and analysis of large data sets while maintaining full functionality.


**Drawbacks**:

**1. Memory Usage:**
Pandas can consume significant memory, particularly when handling massive datasets. Performing the task of loading and handling extensive quantities of data can require significant memory resources, which might be a limitation in settings with restricted memory capacity.


**2. Performance Constraints:**
Although Pandas has efficient data processing capabilities, some operations may show slower performance when compared to lower-level libraries such as NumPy. Pandas might not offer the same level of performance as specialized libraries or custom implementations for activities that require a lot of processing power.


**3. Limited Support for Real-Time Data:**
Pandas is mainly intended for manipulating clean, organized datasets. It may not be optimal for handling real-time data or analyzing streaming data when other specialized tools or libraries may be more appropriate.


### Dask

Dask is engineered explicitly to execute computations in parallel and handle large-scale data processing. It is well-suited for handling more significant datasets than the available RAM and allows users to perform concurrent operations on large datasets.


#### The advantages and drawbacks of using Pandas

**Advantages**:

**1. Easy to use:** Dask effortlessly interfaces with well-known libraries such as Pandas and NumPy, offering a seamless transition for Python users. By using the Dask equivalents of libraries such as Pandas, one can easily replace them in the API to perform simultaneous processing with few code modifications.


**2. Scalability:** Dask provides seamless scalability, supporting single-machine deployments and extensive clusters with thousands of processing cores. It optimally utilizes the available resources, whether on the computer or in a system with distributed computing.


**3. Flexibility:** Dask provides a variety of collections such as DataFrames, Arrays, Bags, and Datasets, enabling you to select the most suitable option for your data and task. Additionally, it supports a range of functions, such as filtering, aggregating, and employing machine learning methods.


**Drawbacks**:

**1. Overhead:** Dask incurs additional computational costs compared to single-threaded execution, mainly when working with tiny datasets. The advantages of parallelization may not exceed the additional costs for specific jobs.


**2. Limited functionalities:** Dask does not have the same capabilities as specialized large data processing frameworks like Spark. For example, the SQL engine of the system is currently being developed, as is its interface with other environments.


**3. Constrained stateful operations:** Dask collections are primarily unchangeable, indicating that altering existing data is impossible. This might provide a challenge for some workflow patterns.


### Vaex

Vaex is precisely engineered to efficiently process data frames too large to fit into the computer's memory, allowing users to handle datasets that exceed the memory capacity (RAM).

**Advantages**:

**1. Performance:**
Vaex is well-known for its exceptional efficiency while handling large datasets. The system utilizes memory mappings and performs lazy evaluations, leading to prompt and effective operations.


**2. Memory Optimization:**
Vaex efficiently loads the required data segments into memory, ensuring memory optimization while working with extensive datasets.


**3. Easy to use:**
Vaex offers an API that closely resembles Pandas, allowing an effortless transition for users who are already experienced with Pandas.


**Drawbacks**:

**1. Limited Functionality:**
Vaex does not support the full range of Pandas operations. Some features available in Pandas may not be present in Vaex.

**2. Less Resources:**
Vaex, while gaining popularity, may have a smaller community than Pandas. This can result in fewer online resources and community support.

**3. Complex Queries:**

Writing complex queries in Vaex might be less intuitive compared to Pandas, as Vaex relies heavily on expressions.


## Comparative Analysis

### Execution Time

In the execution time analysis, Pandas outperformed Vaex and Dask, completing the task in a notably shorter time frame (4 s). Pandas, optimized for in-memory processing, excel with smaller to medium-sized datasets that fit into memory. Dask, designed for parallel and distributed computing, showed a moderately longer execution time (21 s), reflecting its ability to handle larger-than-memory datasets efficiently. Vaex, which had the most extended duration (46.30 s), is designed for processing big datasets that cannot fit in memory, and the increased execution time can be attributed to the intrinsic additional time required for reading and processing data in this manner. The most suitable library to use relies on the individual attributes and scale of the dataset. Pandas provide fast performance for jobs that can be handled in memory. Still, Dask and Vaex give more significant advantages for enormous datasets requiring distributed or out-of-core processing.


### Memory Usage

Because of its out-of-core architecture for effectively processing massive datasets, Vaex had the most significant utilization in the memory consumption analysis, requiring 2.1 GB. Through its in-memory processing optimization, Pandas showcased the most minimal memory footprint of 380 MB. Using 1.2 GB, Dask demonstrated its scalability for datasets with larger-than-memory requirements, falling somewhere in the middle. Vaex is great in out-of-core situations, Pandas is great in in-memory jobs, and Dask is a good compromise for scalable calculations; nevertheless, the choice should be based on the available memory resources and the particular features of the dataset.


## Conclusion

The dataset's specifics and the job's needs should dictate whether Vaex, Pandas, or Dask is best. Pandas shine when working with tiny datasets that can be stored in memory because of its fast execution and extensive features. When scalability is paramount, Dask's ability to effectively handle datasets bigger than memory makes it a valuable tool. When dealing with enormous datasets that exceed available RAM, Vaex comes into its own, especially when memory efficiency is paramount. Memory use, runtime, and the size of the dataset are all trade-offs that should inform the selection. At various points in the data analysis pipeline, it may need the strategic utilization of several libraries.


