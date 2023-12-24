# Homelander - Assignment 6 

<a target="_blank" href="https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/AM/AM_Assignment_6.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Ayaz Rahman Bhuiyan           |MCS231023      |
| Musab Ibne Ahmad              |MCS231017      |

**Five strategies to handle the big dataset**

1. Load Less Data
2. Use Chunking
3. Optimize Data Types
4. Sampling
5. Parallelize with Dask

**## Comparative Analysis**
| No. | Traditional Method | Advanced Strategies | Result |
   | --- | ------------------ | -------------------- | ------ |
   | 1.  | Memory usage 2.00 GB | **Load Less Data**: Memory usage 1015.60 MB | Memory usage reduced by 49.20% |
   | 2.  | Time taken to read dataframe 42.99 s| **Use Chunking**: Time taken to read in chunks 0.67 s | Reading time reduced by 98.4% |
   | 3.  | Data Frame Size 2.00 GB | **Optimize Data Types**: After optimization 0.89 GB | Data frame size reduced by 55.50% |
   | 4.  | Memory usage 2051.85 MB | **Sampling**: 10% sampling; Memory usage 209.73 MB | Memory usage reduced by 89.8% |
   | 5.  | Reading Data frame: 43.48 s | **Parallelize with Dask**: Reading Data frame: 0.024 s | Processing time reading dataframe reduced by 99.94% |
   
**Pros & Cons:**

1. Pandas
Pros:
*   Powerful data structures and functions for analysis and manipulation
*   Efficient for smaller datasets
  
Cons:
*   Can consume significant memory for large datasets
*   Operations on large DataFrames can be slow

2. Load Less Data:
Pros:
*   Reduces memory footprint and initial loading time
*   Can improve performance for specific tasks
  
Cons:
*   Requires careful selection of relevant data
*   Could limit analysis if essential data is excluded

3. Use Chunking
Pros:
*   Processes large datasets in manageable chunks
*   Reduces memory overhead and can improve performance for certain operations.
  
Cons:
*   Requires careful handling of data continuity
*   Can introduce code complexity

4. Optimize Data Types
Pros:
*   Reduces memory usage by choosing appropriate data types
*   Can improve performance for computations
  
Cons:
*   Requires understanding of data types and their memory implications
*   Might necessitate data type conversions

5. Sampling
Pros:
*   Analyzes a representative subset to reduce memory and processing time
*   Can provide insights without processing the entire dataset
  
Cons:
*   Potential loss of information if sample is not representative
*   Sampling bias might lead to inaccurate conclusions

6. Parallelize with Dask
Pros:
*   Distributes computations across multiple cores or machines
*   Can handle datasets too large for single-machine processing
  
Cons:
*   Adds complexity to code and setup
*   Requires understanding of parallel computing principles

**Conclusion**

In conclusion, the comparative analysis between traditional methods and advanced strategies demonstrates substantial improvements in memory usage, processing time, and data frame size.Firstly, memory usage has significantly decreased by 49.20% through the implementation of strategies such as loading less data and optimizing data types. Secondly, substantial improvements in reading time have been achieved, with a remarkable 98.4% reduction in the time taken to read data frames. Moreover, the optimization of data types has led to a noteworthy reduction of 55.50% in data frame size. This not only aids in better storage utilization but also facilitates faster data retrieval and manipulation. Lastly, the combination of sampling and parallelization with Dask has resulted in an impressive 89.8% decrease in memory usage during data frame reading. These advanced strategies collectively showcase the potential for substantial efficiency gains, making them essential considerations for anyone seeking to enhance the performance of data processing workflows.

