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

There are a plethora of Python libraries that focus on certain aspects of data analysis and manipulation, two of the most fundamental operations in data science. The purpose of this paper is to offer a concise yet thorough review of three well-known libraries, namely Vaex, Pandas, and Dask, that are commonly used for data analysis and manipulation. The study will provide an overview of various libraries as well as a comparison analysis.


### Pandas

Pandas is most commonly used with memory-capable datasets that are modest to medium in size. Dataset analysis, modification, and cleaning are some of its most common uses.

#### The advantages and drawbacks of using Pandas

**Advantages**:

**1. Data Representation:**
Pandas provides the DataFrame object, a two-dimensional structured data format for simple data processing and analysis. The application's indexing and column manipulation features are user-friendly, and it supports a large variety of data formats.


**2. Increased Efficiency:**
By providing a clear and comprehensive syntax, Pandas allows users to achieve more with less code. By providing a variety of pre-established methods and methodologies for data processing and analysis, the programme streamlines processes and eliminates the need for human coding.


**3. Efficiently Handles Large Datasets:**
Even though Pandas has been fine-tuned to handle massive datasets efficiently, it could still have some performance issues. Pandas allows for the efficient processing and analysis of large data sets while preserving all of its capability.


**Drawbacks**:

**1. Memory Usage:**
Particularly when dealing with massive datasets, Pandas may use a lot of RAM. In situations with limited memory capacity, the act of importing and handling large amounts of data might require a lot of memory resources.


**2. Performance Constraints:**
While Pandas is great at processing data, it might not be as efficient as libraries that operate at a lower level, like NumPy, for some tasks. data-intensive jobs that might be better handled by dedicated libraries or bespoke implementations than by Pandas.


**3. Limited Support for Real-Time Data:**
Pandas is designed primarily for the manipulation of organized, tidy datasets. When analyzing streaming data or managing real-time data, alternative specialized tools or libraries might be more suitable.


### Dask

Dask has been purposefully designed to perform computations in parallel and effectively manage the processing of large-scale data. Users are granted the capability to execute concurrent operations on sizable datasets, making it highly suitable for managing datasets that exceed the capacity of the RAM.


#### The advantages and drawbacks of using Pandas

**Advantages**:

**1. Easy to use:**
Dask integrates seamlessly with widely recognized tools, including NumPy and Pandas, providing Python users with a smooth transition. By substituting the Dask equivalents for libraries like Pandas in the API, it is possible to execute concurrent processing with minimal alterations to the code.


**2. Scalability:** 
Dask guarantees smooth scalability by supporting both single-machine deployments and large clusters with thousands of processing cores. In a distributed computing system or on a single computer, it makes use of the resources that are available.


**3. Flexibility:**
Dask provides a wide variety of collections, such as DataFrames, Arrays, Bags, and Datasets, so you may pick the one that works best for your data and your tasks. Also supported are a number of processes, such as filtering, aggregation, and machine learning.


**Drawbacks**:

**1. Overhead:**
When dealing with tiny datasets, Dask's computational costs are higher than those of single-threaded execution. The potential savings from parallelization may not be worth the extra cost in many scenarios.


**2. Limited functionalities:** 
Dask, in contrast to Spark, does not have the features of dedicated frameworks made for processing data at scale. As an example, we are now developing the SQL engine and the interaction with the system's external surroundings.


**3. Constrained stateful operations:** 
Dask collections are primarily unchangeable, indicating that altering existing data is impossible. This might provide a challenge for some workflow patterns.


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


