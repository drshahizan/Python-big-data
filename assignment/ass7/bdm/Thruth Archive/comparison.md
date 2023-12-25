

# Assignment 7: Comparison between libraries By Truth Archive

### Group Name: Truth Archive

### Group Members
| Name                             | Matrix Number |
| :------------------------------- | :-------------:|
|Hazem | MCS231019|
|Shivanesh |MCS231014 |
|Nur Shahirah  |MEC233005 |
| Mustafa |MCS212012 |

## Introduction

In the rapidly evolving international of facts science, the potential to efficaciously technique and analyze big information is of maximum importance. The advent of big facts has created a need for tools and libraries that could process huge amounts of records speedy and successfully. In this record we delve right into a comparative analysis of 3 major Python libraries - Pandas, Dask and Modin - each acknowledged for its particular talents in information manipulation and analysis Our intention is to evaluate these libraries in reminiscence utilization and time control together with facts internal set handling, data introduction And cleaning, exploratory-analysis and visualization, asking and answering questions

### Pandas


Written with the aid of Panda
Pandas is a cornerstone in the information technological know-how toolkit, providing versatile information systems and functions to efficaciously manage and analyze data systems Excelling within the use of small to medium-sized facts structures, Pandas gives intuitive connectivity and rich capability for information mining, resizing, aggregating , reducing-and-dicing Known for its ease of use and ease of use, making it more on hand whilst it takes for standardized statistics analysis obligations


### Dask

Dask is a dynamic parallel computing library that interfaces seamlessly with Pandas and extends its competencies to huge datasets. Dask breaks down the big facts approaches into achievable chunks and permits you to system these in parallel. This technique appreciably reduces computation time, making Dask a higher alternative for running with massive facts sets. In addition, Dask gives a familiar Panda-like API, which guarantees a clean mastering curve for those already used to Panda.
### Modin

Modin is an bold library aiming to supercharge Pandas' overall performance. By utilizing disbursed computing frameworks like Ray or Dask inside the background, Modin scales Pandas' operations across all to be had CPU cores. This parallel execution model allows for faster statistics processing, especially useful while managing huge datasets. Modin aspires to be a drop-in substitute for Pandas, requiring minimal code changes to acquire the benefits of extended records evaluation.

## Comparative Analysis

### Memory Usage

Memory management is a critical aspect of data processing, particularly when dealing with large datasets. In Python, different libraries offer varying approaches to handle data efficiently. 

Our analysis encompassed a range of operations, with a keen focus on how each library manages memory usage. The table below illustrates the memory footprint for each library across different operations:

   | Operation | Pandas | Modin | Dask |
   | --------- | ------ | ----- |----- |
   | DATASET                                | 358 MB | 227 MB | 1326 MB |
   | Data Preparation and Cleaning          | 7454 MB | 297 MB | 5360 MB |
   | Exploratory Analysis and Visualization | 7300 MB | 294 MB | 6718 MB |
   | Asking and Answering Questions         | 7601 MB | 559 MB | 6958 MB |

First, the row DATASET represents the memory usage when loading and working with a dataset. Pandas shows a moderate memory footprint, while Modin demonstrates a lower memory requirement. In contrast, Dask exhibits higher memory usage, indicating a potentially more resource-intensive approach.

Second, data preparation and cleaning reflects the memory consumption during data preparation and cleaning tasks. Pandas exhibits a substantial memory requirement, whereas Modin showcases a significantly lower footprint. Dask falls in between, with a moderate but more efficient memory usage compared to Pandas.

 Third, in memory usage during exploratory analysis and visualization, Pandas shows a high memory demand, whereas Modin displays a much lower requirement. Dask, again, positions itself between the two, emphasizing a balance between memory efficiency and performance.
 
 lastly, The memory usage for querying and answering questions on the dataset is presented in this row. Pandas exhibits the highest memory consumption, Modin shows a moderate requirement, and Dask, once again, positions itself as a middle ground.

In summary, the comparison reveals distinct memory usage patterns among the three libraries across various data processing tasks. Pandas tends to consume more memory, Modin demonstrates lower memory requirements, and Dask strikes a balance, providing a trade-off between memory efficiency and distributed computing capabilities. The choice of library would depend on specific project requirements, considering factors such as dataset size, task complexity, and available computational resources. 

Modin emerged as the clear winner in terms of memory efficiency, consistently using less memory across all tasks.


### Execution Time
The speed of execution is crucial in data analysis, especially when dealing with large and complex datasets. The following table summarizes the time taken for each operation by the different libraries:

  | Operation | Pandas | Modin | Dask |
  | --------- | ------ | ----- |----- |
  | DATASET                                | 13s    | 8s    | 20s  |
  | Data Preparation and Cleaning          | 41s    | 36s   | 50s  |
  | Exploratory Analysis and Visualization | 56s    | 30s   | 1m   |
  | Asking and Answering Questions         | 42s    | 9s    | 17s  |

First, DATASET row represents the execution time when loading and working with a dataset. Modin shows the shortest execution time, followed by Pandas, and Dask requiring a bit more time, potentially due to its distributed computing nature.

Second, execution time during data preparation and cleaning tasks is highlighted here. Modin demonstrates the shortest execution time, Pandas falls in the middle, and Dask exhibits a slightly longer duration, indicating the trade-off between parallel processing and overhead.

Third, the execution time for exploratory analysis and visualization tasks is present that Modin significantly outperforms the others in terms of speed, Pandas is in the middle, and Dask exhibits a longer execution time.

Finally, the execution time for querying and answering questions on the dataset showcas that Modin, again, shows the shortest execution time, Pandas falls in the middle, and Dask exhibits a slightly longer duration.


Here, Modin consistently outperformed the others, demonstrating significant time savings, particularly in exploratory analysis and visualization

## Pros and Cons 

| Library | Pros                                      | Cons                                      |
|---------|-------------------------------------------|-------------------------------------------|
| Pandas  | - Rich functionality for data manipulation| - Inefficient with large datasets         |
|         | - Extensive documentation and community   | - Single-threaded, limiting parallelism   |
|         | - Mature and widely adopted in the industry| - Limited support for distributed computing|
|         | - Seamless integration with other libraries|                                           |
|         | - Intuitive and user-friendly API         |                                           |
|         | - Suitable for small to medium-sized datasets|                                       |
| Modin   | - Improved performance with parallel processing| - Limited support for some Pandas features|
|         | - Transparently scales across multiple cores| - Relatively smaller community compared to Pandas|
|         | - Easy integration with existing Pandas code| - Dependency on Ray, which may add complexity|
|         | - Minimal code changes needed for parallelism| - Limited support for distributed computing|
|         | - Suitable for medium to large-sized datasets|                                       |
|         | - Actively developed and evolving          |                                       |
| Dask    | - Seamless parallel and distributed computing| - Learning curve for distributed computing|
|         | - Scales from a laptop to a cluster        | - Overhead in setting up a Dask cluster   |
|         | - Supports larger-than-memory computations| - Limited support for some Pandas features|
|         | - Lazy evaluation for optimized task execution| - More complex debugging and error handling|
|         | - Integrates well with existing NumPy and Pandas code| - Limited support for real-time data processing|
|         | - Suitable for very large and distributed datasets|                                   |


## 5.0 Conclusion
Our comparative analysis underscores the importance of choosing the right device for facts evaluation duties. Modin sticks out as a strong alternative to Pandas, specifically when coping with massive datasets, imparting both reminiscence performance and pace. While Pandas stays a reliable and easy-to-use device for smaller datasets, Modin and Dask offer effective options for scaling facts analysis to large datasets. Ultimately, the choice of library have to align with the unique wishes and scale of the statistics analysis obligations handy.


