# Assignment 7: Comparison between libraries

### Group Name: Theboys

### Group Members
| Name                             | Matrix Number |
| :------------------------------- | :-------------:|
|Pang Chern Hong  | MCS231006|
|Nian Cong | MCS231007 |
|Wu Jiaming | MCS221033 |
|Liu Kaiyuan | MCS231020|

### Pandas

Pandas is a fast powerful, flexible and easy to use tool specially for data manipulating and analysis, it is built on top of the python language.

#### Pros and cons of using Pandas
**Pros**:

1.**Data manipulating**: Pandas has 2 structure which are series and dataframe that are enable users to easily manipulate the data. It also has a variety of function that can be used for data cleaning and preprocessing.

2. **Flexibility**: Pandas can alter the index with columns and also able to integrate with the NumPy functions. It also help us to aligh data based on labels we selected, and it can process time-series data such as stock market prices.

3. **Community and Documentation**: There is a big and active community of Pandas users, that means we can find resources, documentations, examples or case studies and solutions easily in the internet.

**Cons**

1. **Memory usage**: Although Pandas is a convenient tool, it is also memory intensive, particularly when it came to large dataset, some big data management techniques such as fine tuning or sampling should be applied to overcome it but also will make the dataset lack of representability.

2. **Performance**: Pandas is using single core of the computer to process the data, which means it do not perform efficiently like Dask with the multi-cores computers that can process the data parallely and do distributed computing.


### Dask

Dask is a parallel computing library that integrate seamlessly with Pandas and it can scale the python libraries like NumPy and scikit-learn. It is useful especially when dealing with large dataset since it can buld a task graph before execution to let users modify before wasting the execution time.

#### Pros and cons of using Dask
**Pros**:

1. **Scalability**: User used a clusters of machine instead of just a single machine to do the computation. So it is suitable to handle large datasets and performing distributed computing.

2. **Integration with Pandas and NumPy**: Users can use the similar APIs of Pandas and NumPy, so that most of the problems can be found in the internet and gain the similar solutions.

3. **Parallel Processing**: Unlike Pandas, Dask possess parallel processing capabilities, which allowed users to perform parallel computation on multi-core machines. This can significantly speed up data processing tasks.

4. **Lazy Evaluation**: Dask can build up a task graph like what we showed above before execution, this function allows users to check whether that can be modified to increase efficiency.

**Cons**:

1. **Learning Curve**: Although Dask is designed to be user-friendly, there is still some difficulties for the users who are new to this concept and to perform dask operations.

2. **Debugging Complexity**: Although Dask can have integration with Pandas and NumPy, but sometimes there also got some incompatible functions within Dask and that let the debugging being more complicated compared to Pandas.

3. **Performance Overhead**: When the data size is small, the charateristics of Dask for distributed computing will be a disadvantage since there can be overhead brought by managing this distributed computing tasks.


#### Vaex

Vaex is a python library that apply lazy out-of-core dataframes, which is able to process and load big dataset compared to python, particularly useful for statistical calculation and basic visualization. It applied memory mapping and lazy computation for best performance.

###Pros and Cons of using Vaex

**Pros**:

1. **Memory Efficiency**: Vaex loads subset of entire dataset multiple times and that enable it to handle the dataset which larger than the RAM, in the same way it also process and read the data in chunks.

2. **Concurrency**: Like Dask, Vaex also use parallel processing to better utilize the multi-core system.

3. **Integration with Dask**: Vaex can integrate with Dask, another parallel computing library of Python.

4. **Support of expression**: Vaex enable the use of expression for the calculation which simplify the process of creating new columns without a complicated loop.

**Cons**

1. **Community**: The community of Vaex is smaller compared to Pandas, that means it is harder to find a good resources or documentation and the solutions when we encounter some problems.

2. **Limited Functionality**: Vaex is excellent to do the basic data manipulation and analysis, but it do not possess some more advanced features and functions of Pandas.

3. **Learning Curve**: Users need to master the syntax and approaches of Vaex, which might cause a learning curve for users who are new to the Vaex like a traditional Pandas user.


### Memory Usage
To load the 1.2 GB data, pandas used 283.8 MB, while Vaex do not store memory but only read file from disk when needed, which is called memory mapping. when it cames to execution time for loading the data, Pandas used 13.73 seconds, Vaex used 21.22 seconds, while Dask used 39.74 seconds to read the dataset. In brief, we can evaluate that for small dataset, Pandas can load the data fastest, while for memory usage, Vaex can do the best job among them, while dask perform the worst on smaller dataset.



## Conclusion
This comparative analysis showed the pros and cons of each columns, and when it comes to small dataset nearly to 1 GB of data, Pandas is still the best choice due to its flexibility and compatibility with many functions and tools. While Vaex also be considered one of the best choice when we process the numerical or categorical data with the need of statistical analysis and visualization especially when the data is larger. Dask can be considered as a powerful tool particularly for large data since it can sketch the flow of the tasks graph before execution so that we can save a lot of time by modifying the flow. Vaex and Dask are both user-friendly but some efforts needed to mastery these libraries for someone who is new to them or already used to implement Pandas. User need to make the right choice of applying these libraries depends on their task given.
