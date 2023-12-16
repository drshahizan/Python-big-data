<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 6: Mastering Big Data Handling

### Group Name: Ayam Rendang 1
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| RANJEET A/L THIAGARAJAN           |MCS231015      |
| THANEATHARRAN A/L SANTHARASEKARAN               |MSC232006      |

1. **Pick a Big Dataset:**
    We have chosen a dataset from Kaggle which is Iowa Liquor Sales Dataset for Assignment 6. This dataset contains information on the name, kind, price, quantity, and location of sale of sales of individual containers or packages of containers of alcoholic beverages. 

3. **Loading the Dataset:**
   - The dataset that was selected was downloaded directly from Kaggle into Google Colab using the API key (.json file). The information about the dataset is as follows:
     - RangeIndex: 12591077 entries, 0 to 12591076
     - Data columns (total 24 columns):
     - Data Types: float64(5), int64(5), object(14)
     - Memory usage: 2.25 GB

4. **Strategies for Big Datasets - General Information:**

  - Load less data: Optimising memory consumption and speeding processes can be achieved by loading only the certain columns or rows needed for the analysis. But because it doesn't represent the whole dataset, it can have an impact on the choice.

  - Chunking: To prevent memory problems, chunks enable data to be processed in smaller portions. This is especially helpful for procedures that don't need the whole dataset to be open in memory at once. Still, working with chunks may make some processes more complicated.

  - Optimized data types: Selecting the most memory-efficient data types for every column will significantly decrease memory consumption and simplify computations by reducing the amount of data needed. As a result, it may increase overall effectiveness.

  - Sampling: Sampling can provide insight into and aid in comprehending the dataset's general properties. However, sampling may not fully represent the entire population, meaning that some rare occurrences or changes may go unnoticed.

  - Parallelize with Dask: Dask is a parallel computing platform that allows computing scaling and parallelization.  Dask's ability to parallelize calculations is one of its primary characteristics; it makes it possible to work with datasets that are larger than memory by dividing them into smaller jobs that can be completed in parallel.

4. **Comparative Analysis**
   | No. | Usual Pandas Method | Advanced Strategies | Result |
   | --- | ------------------ | -------------------- | ------ |
   | 1.  | Memory usage 2.25GB | **Load Less Data**: Memory usage 0.28GB | Memory usage reduced by 87.56% |
   | 2.  | Memory usage 2.25GB | **Use Chunking**: Memory usage 0.18GB | Memory usage reduced by 92.0% |
   | 3.  | Data Frame Size 2.25GB | **Optimize Data Types**: Data Frame Size 1.9 GB | Data frame size reduced by 15.56% |
   | 4.  | Memory usage 2.25GB | **Sampling**: 10% sampling; Memory usage 0.23 GB <br> 10000 rows sampling; Memory usage 0.19 GB | Memory usage reduced by 89.78% <br> Memory usage reduced by 91.56% |
   | 5.  | Reading Data frame: 1min 34s  | **Parallelize with Dask**: Reading Data frame: 15.9 ms  | Processing time reduced by 99.9%  |

The comparative analysis clearly shows that the usual pandas method has its limitations when handling big datasets. It has limitations in RAM, memory usage, and processing time. The advanced strategies help to reduce memory usage, shorten the processing time, reduce the RAM percentage, and other ways to analyze big datasets.

5. **Conclusion**

  In conclusion, we can consider optimizing the data types or continuing over the data to process all of our data. Dask can parallelize Pandas if our dataset is still too big and requires too much processing time, as its processing time has been reduced by 99.9%. Together, these techniques seek to improve processing speed, use less memory, and offer effective methods for managing big information without taxing the system's capacity.




