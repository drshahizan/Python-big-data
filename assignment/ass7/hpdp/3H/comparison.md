
# Assignment 7: Comparison between libraries

### Date: 24/12/2023
### Group Name: 3H

<center>

### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
| ALIEYA ZAWANIE BINTI A ZAINI | A21EC0156 | MODIN
| MOHAMAD AZRI HADIF BIN MOHAMMAD RIZAL | A21EC0054 | DASK
| IZZAT HAQEEMI BIN HAIRUDIN | A21EC0033 | PANDAS
| ALIYA ZARENA BINTI ZAINULANUAR | A21EC0013 | COMPARISON LIBRARIES  |

</center>

<br>

Let's explore the functionalities of the three selected libraries: Pandas, Modin, and Dask. These libraries are widely employed for managing large datasets and executing data manipulations. Before we conduct a comparative analysis, let's delve into the individual features and capabilities of each library.

## 1.0 Pandas

Pandas is a powerful and widely used Python library for data manipulation and analysis. It provides a flexible and easy-to-use data structure called a DataFrame, which is essentially a two-dimensional table with labeled axes (rows and columns). Additionally, it offers a range of functionalities for data analysis. Some of the analyses that can be performed using this library include:

*   Data cleaning: delete rows that are not relevant, or contains wrong values (*empty or NULL values*). For instance, we used `dropna()` in the case study to drop any duplications in rows/columns from the chunks dataset.

*   Analyzing data : Make statistical analysis such as finding the correlation, `corr()` based on two important columns that contribute towards the case study. We also used  `describe()` in order to get summary statistics for the Fermentation Time in preparing the beer.

*   Make conclusion: Able to come out with relevant results by doing the data visualisation that will help in making informed decisions and enhancing the case study


<br> 

## 2.0 Dask

Dask is a parallel computing library in Python designed to enable parallel and distributed computing for larger-than-memory computations. It makes handling big datasets quickly is possible even when they can't fit in one machine's memory. Moreover, it also operates by breaking down computations into smaller tasks that can be executed in parallel across multiple cores or even distributed across a cluster of machines. These are the key aspects of Dask:

*  Parallel Computing: Breaking down computations into smaller tasks that can be executed independently.

* Integration with Existing Libraries: Integrate seamlessly with other existing Python libraries, including `NumPy, Pandas, and Seaborn.` This makes it easy to parallelize and scale computations on arrays, dataframes, and machine learning tasks.

*   Lazy Evaluation: It builds up a task graph representing the computation but doesn't execute it immediately. For example, the actual function is not performed until `compute()` is called. This allows for optimization and parallelization of the computation before it is actually performed.

In our assignment 7, we apply the Dask Dataframes because it able to compute for terabyte-sized datasets. For instance, we read our input by running `'import dask.dataframe as dd'` code.

<br>

## 3.0 Modin

As we know, Modin, a Python library that makes it simple to scale and parallelize pandas routines. By smoothly dividing the computation across several cores, it seeks to improve the performance of Pandas operations. Because Modin is meant to be a drop-in replacement for Pandas, users can still utilise the well-known Pandas API while enjoying enhanced performance for specific tasks.
Here are essential features of the Modin Library:


*   Pandas Compatibility: Allows users to transition seamlessly from Pandas to Modin without requiring significant changes to their existing code.

*   Lazy Evaluation: It use similar approach like Dask do but the difference is the user need to explicitly requests the result in order to built a task graph; otherwise, the computation will be postponed.

* Integration with Existing Code: Able to integrate into the existing code  directly where most of the Pandas operations will automatically parallelized.

In this assignment 7,  we used `groupby` function to grouping based on the *Beer_Style* column. Additionally, `mean()` function after grouping to calculate average alcohol content for each beer style which leverages parallelism.

<br>

## 4.0 Comparative Analysis
### 4.1 Memory Usage

Memory usage is an essential consideration when working with large datasets, and different libraries may have varying memory requirements. Furthermore, the memory usage is directly influenced by the size of complexity of the dataset. This is because some operations may become meory-intensive, where with large datasets, it will lead to performance issues. Let's discuss the memory usage aspects of Pandas, Modin, and Dask:
  
  <br>
   <center>

   | Operation/Analysis | Pandas | Modin | Dask |
   | --------------- | --------------- | --------------- |--------------- |
   | Read selected columns | 2.4GB   | 2.4GB    |1.5GB |
   | Reducing Memory Usage (After Optimization)   | 0.17GB   | 0.17GB    | <center> - |

   </center>
<br>

(**1) Pandas vs. Modin:**

Here, we can observe that even after minimising the usage according to each operation, Modin and Pandas both have the same amount of memory utilisation. This is a result of the dataset fitting into memory with ease. However, because of the parallelization method, Modin will typically use greater memory overhead than Pandas. Modin may result in large memory reductions for some operations but just moderate benefits for others.

<br>

(**2) Pandas vs. Dask:**

As for Pandas and Dask, we can clearly see that Dask consumes less memory compared to the Pandas. This can proof that Dask has the ability to handle larger-than-memory datasets which makes it more suitable for handling big datasets compared to Pandas. In this case study, we also use Dask to handle computations on chunks of data, making it more memory-efficient for large-scale data processing.

<br>

(**3) Modin vs. Dask:**

Here, Dask also consumes less memory compared to Modin. This show that dask's scalability is more beneficial in terms of memory usage because in handling big datasets and several operations take a lot of memory usage to be done.

<br>

### 4.2 Overall Execution Time

The execution time of data processing tasks is a crucial factor when dealing with large datasets. Let's explore how Pandas, Modin, and Dask contribute to execution time and their implications for handling big dataset case studies:

<br>
 <center>

| Operation/Analysis | Pandas | Modin | Dask |
| --------------- | --------------- | --------------- |--------------- |
| Statistical Measures   | 16.77 sec   | 20.47 sec    | 18.65 sec|
| Distribution of Numerical Features   | 7.28 sec    | 11.53 sec    | 7.66 sec|
| Chunking   | 150.21 sec   | 79.86 sec    | 1.63 sec|

 </center>

<br>

(**1) Pandas vs. Modin:**

Based on case study, in chunking only, Modin has a significant faster value compared to Pandas, while other two operations, Pandas is faster. While Modin aims to parallelize Pandas operations, there might be some overhead in certain cases, leading to slightly longer execution times compared to Pandas.

<br>

(**2) Pandas vs. Dask:**

As for this comparison, Pandas has a small value difference faster compared to Dask, but has slower operation when it comes to chunking. This is to show that Pandas is not designed for distributed computing, resulting in significantly longer execution times for chunking operations on large datasets.

<br>

(**3) Modin vs. Dask:**

Between these two libraries, Dask is the winner because it has faster execution time compared to Modin in all operations. Eventhough Modin can do the parallelization in order to improve the performance compared to Pandas, but it still outperforming than Dask, due to some overhead occured.

<br>

## 5.0 Conclusion

Based on task given, handling large datasets has become a fundamental difficulty in modern data science and analytics, necessitating the usage of a number of libraries capable of managing the intricacies associated with large and diverse data. As the size and diversity of datasets grow, typical data processing methods frequently find restrictions, encouraging the investigation of specialised libraries that provide solutions for efficient computation, storage, and analysis. Pandas, Dask, and Modin libraries play critical roles in solving the issues provided by huge datasets. This case study sets the context for delving into how different libraries adapt to the complexities of vast and diverse datasets, each providing distinct strengths to the toolkit of data scientists and analysts.

<br>

In the context of memory considerations, Modin emerges as a suitable choice for a case study involving a moderately sized dataset that comfortably fits into the memory of a single machine. Modin's primary focus on parallelism on a single computer, as well as its smooth connection with Pandas, make it an effective tool for optimising performance in instances where the dataset can fit inside available memory. This option is especially helpful for Pandas users looking for speed boosts without the need for distributed computing capabilities.

<br>

Next, the investigation offers diverse findings when it comes to execution time. Pandas is the most efficient library for basic statistical measurements and the distribution of numerical features based on the execution times provided. When tasks entail parallel computing workloads, chunking, or working with extremely huge datasets, the landscape shifts. Dask outperforms the competition in terms of execution time in such cases. Dask's ability to parallelize computations and handle huge datasets efficiently makes it an appealing alternative for workloads requiring distributed computing capabilities.

<br>

In conclusion, Dask had been chosen as the preferred tool library for this case study because to its impressive efficiency in both memory usage and execution time. This tool can generate an optimal solution for dealing with huge datasets. Dask's ability to manage memory efficiently, as indicated by its lower memory utilisation when compared to Pandas, is a significant advantage, particularly when working with datasets that surpass the capacity of a single system. Furthermore, the little difference in execution time between Dask and Pandas suggests that Dask provides competitive performance while also providing the scalability and parallel computing capabilities required for large-scale data processing. Not to forget, Dask is the ideal tool library for cases where the focus is on both effective memory utilisation and streamlined calculation speeds in the face of large datasets due to its dual strength in memory optimisation and execution efficiency.
