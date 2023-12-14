<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 6: Mastering Big Data Handling

### Group Name: Sambal
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Mohd Nor bin Mohidin            |MCS231008      |
| Zuhayr Arif bin Zakaria               |MCS231002      |

### 📂 Folder content:
* [💻 Assignment 6](BigDataProcessing.ipynb)
* [💻 Report](big_data.md)

1. **Pick a Big Dataset:**

   We have chosen a dataset from Kaggle which is 2019 Airline Delays w/Weather and Airport Detail for this assignment. This dataset comprises comprehensive information on airlines, weather conditions, airports, and employment details, primarily designed for classification purposes.
   
3. **Loading the Dataset:**
   - This dataset we downloaded directly from Kaggle into Google Colab using API key (.json file). The information about the dataset is as follows:
     - RangeIndex: 6489062 entries, 0 to 6489061
     - Columns: 26 entries, MONTH to AWND
     - Dtypes: float64(9), int64(13), object(4)
     - Memory usage: 2.9 GB

4. **Strategies for Big Datasets:**
   
   a) **Load Less Data:**
   
      In this strategy, we load only the required columns instead of all columns because sometimes, we don’t need all the columns or features for our analysis. 
      Therefore, we have to identify first the columns that we need before loading the data frame. From 26 columns in the dataset, we have chosen only 10 columns 
      that we need for the data frame.

      As a result, after loading only 10 columns instead of all columns, the memory usage has reduced by 55.17% which is from 2.9GB to 1.3GB. This method proved 
      that loading less data can reduce the data frame significantly.

   b) **Use Chunking:**
   
      To use chunking, we will declare the size of the chunk in the beginning. Then using read_csv() with the chunk size parameter, returns an object we can 
      iterate over.

      In this strategy, instead of 6,489,061 rows, we choose a chunk size of 50,000 which means at a time, only 50,000 rows of data will be imported. So we can 
      have multiple chunks, and each chunk can easily be loaded as a pandas data frame.

      As a result, chunks has reduced the memory usage by 65.86% which is from 2.9 GB to 0.99 GB by subdividing the dataset into smaller parts.

   c) **Optimize Data Types:**
   
      In this strategy, we convert the columns' numerical data types into smaller data types. Before we convert the data types of columns, we have to ensure that 
      there are zero null values, check the data types for each column, and get the size of the data frame for comparison. We also have to identify the unique 
      values, minimum and maximum values of each column so that we can specifically assign the new data types.
   
      After we check the values of the columns, there are 5 columns that we have converted into uint8, 2 columns into uint16 and 1 column into Boolean data type. 
      There is one object column that we can’t convert into category data types because of too many different values and also one object column that we can’t 
      convert from string to datetime64 due to a different format which will cause null values.
   
      As a result, after optimizing the Data Types into uint8, uint16 and boolean, the data frame size has reduced 26% which is from 1.25 GB to 0.93 GB.

   d) **Sampling:**
   
      For this strategy, we used 2 methods of sampling which are sampling by percentage and sampling by random rows. We have chosen 10% randomly of the sample and 
      10000 rows for sampling purpose.

      As a result, after sampling, memory usage has tremendously reduced which is from 2.9 GB to 300.5 MB (89.6%) if choose 10% of the sample and reduced to 4.6 
      MB (99.8%) if choose only 10,000 out of 6,489,062 rows as sampling.

   e) **Parallelize with Dask:**
   
      For this strategy, we use 3 methods to compare run time between Pandas and Dask as follows:
   
          i) Reading Data frame:
             Pandas = 33.8s;
             Dask = 32.3s
   
         ii) Merging dataframe:
             Pandas = 63.7ms;
             Dask = 27.3ms

        iii) Create Figure:
             Pandas = 537ms; 
             Dask = 250ms

     Based on the comparison above, reading dataframe, merging dataframe and create figures shows that Dask take less time compared to Pandas due to parallel 
     computing in Dask. This indicates that when involve data manipulation, Dask will take less time than Pandas. This is because, parallel computing in Dask is 
     like a single task done by four workers while being done by a single worker in Pandas

6. **Comparative Analysis:**
   - Compared traditional methods with advanced strategies in terms of memory usage and processing time.

   | No. | Traditional Method | Advanced Strategies | Result |
   | --- | ------------------ | -------------------- | ------ |
   | 1.  | Memory usage 2.9GB | **Load Less Data**: Memory usage 1.3GB | Memory usage reduced by 55.17% |
   | 2.  | Memory usage 2.9GB | **Use Chunking**: Memory usage 0.99GB | Memory usage reduced by 65.86% |
   | 3.  | Data Frame Size 1.25GB | **Optimize Data Types**: Data Frame Size 0.93 GB | Data frame size reduced by 26% |
   | 4.  | Memory usage 2.9GB | **Sampling**: 10% sampling; Memory usage 300.5MB <br> 10000 rows sampling; Memory usage 4.6MB | Memory usage reduced by 89.60% <br> Memory usage reduced by 99.80% |
   | 5.  | Reading Data frame: 33.8s <br> Merging data frame: 63.7ms; <br> Create Figure: 537ms; | **Parallelize with Dask**: Reading Data frame: 32.3s <br> Merging dataframe: 27.3ms <br> Create Figure: 250ms | Processing time reduced by 4.4% <br> Processing time reduced by 57.14% <br> Processing time reduced by 53.44% |

   Based on the above comparative analysis, it indicates that the traditional method which is Pandas may have some limitations when dealing with large datasets in 
   terms of memory usage and processing time. The advanced strategies give us the opportunity if Pandas still is an option for analysis where these strategies can 
   reduce memory usage, enhance processing speed, and provide efficient ways to handle large datasets. 

**Conclusion:**

In conclusion, the advanced strategies allow us to handle big data in Pandas as follows:-

   - **Load Less Data:**
      Instead of loading the entire dataset into memory, only loading the specific columns or rows that are required for the analysis will reduce the memory 
      footprint and speed up operations. However, it may affect the decision due to not representing the entire dataset.
     
   - **Use Chunking:**
      When dealing with large datasets, chunks allow to processing of the data in smaller pieces to avoid memory issues. This is particularly useful when 
      performing operations that don't require the entire dataset to be in memory simultaneously. However, certain operations might be more complex when working 
      with chunks

   - **Optimize Data Types:**
      Choosing the most memory-efficient data types for each column can significantly reduce memory usage and speed up computations due to reduced data size. 
      Thus, it can improve overall performance
     
   - **Sampling:**
      Analyzing a sample of the data also can reduce memory usage and take less time for processing. Moreover, sampling can provide insights and help in 
      understanding the overall characteristics of the dataset. However, certain rare events or patterns might be missed due to sampling might not represent the 
      entire population accurately.

   - **Parallelize with Dask:**
      Dask enables parallel and distributed computing, allowing computations to be split across multiple cores or even distributed across a cluster. This will 
      help in handling larger-than-memory datasets by efficiently utilizing available computational resources.
     
   In summary, depending on our goal, the best strategies for exploration purposes can be sampling strategies. In case we need to process all of our data, we can 
   try iterating over data or optimizing the data types. If our dataset is still too large and takes more time to process, then we can go for Dask to parallelize 
   Pandas. All of these strategies collectively aim to reduce memory usage, enhance processing speed, and provide efficient ways to handle large datasets without 
   overwhelming system resources. 


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/BDM/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)



