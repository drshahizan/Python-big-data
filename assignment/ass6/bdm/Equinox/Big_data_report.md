<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 6: Mastering Big Data Handling

### Group Name: Kicap
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Liu Kaiyuan            |MCS231020      |
| Wu Jiaming               |MCS221033      |

### 📂 Folder content:
* [💻 Assignment 6](https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/Equinox/Equinox_Assignment6_ipynb%E2%80%9D.ipynb)
* [💻 Report](https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/Equinox/Big_data_report.md)

1. **Pick a Big Dataset**: The chosen dataset(1GB) for our Assignment 6 which is from kaggle. This dataset contains a collection of user reviews of video games in the Steam Store with a plethora of information about each review such as steam id, app id, playtime, the review text, like/dislike, timestamp of review created, timestamp of review updated, etc, scraped from the STEAM API. 

2. **Loading the Dataset**: Use Python and Pandas to load our chosen dataset into our Colab notebook. We can either upload it from our computer or directly from an online source. By uploading the kaggle.json file, we connected the to Kaggle using the API to get the dataset. It gives us a zip file which is the 'reviews-1230-2345.csv' file and we need to unzip. 

3. **Strategies for Big Datasets**: Initial dataset information:

    - RangeIndex: 3067681 entries, 0 to 3067680
    - Columns: 13 entries, steamid to unix_timestamp_updated
    - Dtype: bool(1), float64(1), int64(10), object(1)
    - Memory usage: 1.2 GB

   Five smart strategies implemented:

   - *Load Less Data*: In the original data set, there are many 0 values in the weighted_vote_score column, and the corresponding calculation method is not given. We have no way of knowing how it works, so this column does not need to be loaded. In addition, knowing another player's ID and current play time is not very helpful in recommending games, so we will not load the steamid and playtime_forever columns. By applying the strategy of reducing data loading, the data loading time has been reduced from 34.46 seconds to 27.21 seconds.

   - *Use Chunking*: After knowing the number of entries in the data set, divide the original data set into several blocks, each block containing 100,000 pieces of data. It only takes 0.58 seconds to load one of the 31 sub-datasets! This significantly reduces load time compared to loading the entire original dataset

   - *Optimize Data Types*: Reduced memory usage from 1.23 GB to 1.11 GB by optimizing data types.

   - *Sampling*: Randomly sampled 3067 rows from the original DataFrame, creating a smaller subset for meaningful insights.

   - *Parallelize with Dask*: Utilized Dask for parallel and distributed computing on larger-than-memory datasets.

  
4. **Comparative Analysis**: 

[1]Load Less Data

1.Memory Efficiency: By loading only the critical portions of the data, significant reductions in memory usage can be achieved. This is crucial for large datasets where attempting to load the entire dataset at once might lead to memory issues, especially in resource-constrained environments.

2.Speed Improvement: Breaking the dataset into smaller chunks and loading only the necessary blocks can reduce the time spent on reading and processing. This often results in overall performance improvements as processing can start without waiting for the entire dataset to be loaded.

3.Storage Space Savings: Loading only a subset of the data can also lead to savings in storage space, particularly for datasets with redundant or unnecessary information.

4.Faster Responsiveness: When dealing with large datasets, loading data incrementally enhances system responsiveness. Users can start viewing and analyzing portions of the data more quickly without waiting for the entire dataset to load.

5.Iteration Processing: Loading data block by block allows for iterative processing, where memory from the previous block can be released while processing the current one, further reducing overall memory requirements.

6.Real-time Data Handling: For streaming or real-time data, a block-wise loading strategy is more suitable as data may arrive sequentially over time rather than being available all at once.

7.Increased Adaptability: The block-wise loading strategy enables handling datasets larger than the available memory, enhancing adaptability to large-scale datasets.

[2]Use Chunking

1.Memory Efficiency:

(1)Chunking: Divides the data into smaller chunks, processing one part at a time. This reduces memory usage, as only a portion of the data needs to be loaded and processed in memory.
(2)Traditional Loading: Loading an entire large dataset at once may lead to memory issues. Chunking efficiently avoids this problem.

2.Real-time Processing:

(1)Chunking: Enables processing to start while the data is still being loaded. This is useful for real-time or streaming data processing.
(2)Traditional Loading: Processing begins only after the entire dataset has been loaded, potentially causing longer wait times.

3.Parallel Processing:

(1)Chunking: Facilitates easier implementation of parallel processing, as each chunk is relatively independent. Different chunks can be processed in parallel on different computing units.
(2)Traditional Loading: Achieving parallel processing can be more complex when loading the entire dataset, requiring consideration of inter-data dependencies.

4.Adaptability with Iterators:

(1)Chunking: Suitable for iterator patterns, allowing progressive loading and processing of data instead of waiting for the entire dataset to load.
(2)Traditional Loading: Loading the entire dataset at once may demand substantial memory and may not be well-suited for iterator patterns.

5.Reduced Waiting Time:

(1)Chunking: Results can be generated while processing the first chunk, eliminating the need to wait for the entire process to complete.
(2)Traditional Loading: Waiting for the entire dataset to load and process is necessary before obtaining the final results.

[3]Optimize Data Types

1.Memory Efficiency:

(1)Data Type Optimization: By selecting appropriate data types, the memory footprint of variables can be significantly reduced, improving memory efficiency.
(2)Traditional Without Optimization: Without data type optimization, default data types may be used, leading to higher memory consumption.

2.Performance Improvement:

(1)Data Type Optimization: Employing suitable data types can enhance runtime performance by reducing memory access and improving computational efficiency.
(2)Traditional Without Optimization: Inappropriate data types may lead to performance degradation due to increased memory access or computational costs.

3.Storage Space Savings:

(1)Data Type Optimization: Choosing compact and appropriately sized data types helps save storage space, especially when dealing with large datasets.
(2)Traditional Without Optimization: Default data types may occupy more storage space than necessary, resulting in resource wastage.

4.Avoiding Unnecessary Precision:

(1)Data Type Optimization: Selecting the right precision for a specific task helps avoid the use of excessively high-precision data types, reducing memory overhead.
(2)Traditional Without Optimization: Default behavior might involve higher precision data types than required for the task.

5.Algorithmic Optimization:

(1)Data Type Optimization: The choice of data types can influence algorithm selection, allowing exploitation of the advantages of specific data types to improve algorithm efficiency.
(2)Traditional Without Optimization: Without considering data types, less efficient algorithms might be chosen.

6.Adapting to Hardware Characteristics:

(1)Data Type Optimization: Considering hardware characteristics, selecting data types that match the underlying hardware architecture can enhance overall performance.
(2)Traditional Without Optimization: Ignoring hardware characteristics may lead to performance bottlenecks.

[4]Sampling

1.Computational Efficiency:

(1)Sampling: Working with a subset reduces computational requirements, allowing for quicker analysis and model training.
(2)Traditional Without Sampling: Analyzing the entire dataset can be computationally expensive and time-consuming.

2.Memory Usage:

(1)Sampling: A smaller subset requires less memory, making it feasible to analyze and process datasets that might be too large to fit into memory. (2)Traditional Without Sampling: Analyzing the entire dataset may lead to memory issues, especially with large datasets.

3.Exploratory Data Analysis (EDA):

(1)Sampling: Facilitates faster exploratory data analysis by providing a representative view of the data without analyzing the entire dataset.
(2)Traditional Without Sampling: EDA on the entire dataset may delay the discovery of patterns and trends.

4.Model Training and Validation:

(1)Sampling: Useful for training and validating models on a representative subset, especially when the dataset is large.
(2)Traditional Without Sampling: Training models on the entire dataset may be time-consuming and computationally intensive.

5.Cost Efficiency:

(1)Sampling: Reduces the cost associated with processing and analyzing the entire dataset.
(2)Traditional Without Sampling: Analyzing the entire dataset may involve higher costs, particularly in terms of computational resources.

6.Real-time and Streaming Data:

(1)Sampling: Well-suited for real-time and streaming data scenarios where it's impractical to process the entire dataset at once.
(2)Traditional Without Sampling: Processing entire datasets in real-time might be challenging due to resource constraints.

7.Initial Data Exploration:

(1)Sampling: Provides an initial insight into the dataset, helping to decide whether a more in-depth analysis of the entire dataset is warranted.
(2)Traditional Without Sampling: Without initial sampling, the full dataset must be processed even if only a subset might be relevant.

[5]Parallelize with Dask

Advantages of Dask over Pandas in Python:

1.Distributed Computing:

Dask is designed for parallel and distributed computing, allowing it to handle large-scale datasets that exceed the memory capacity of a single machine. It can operate on clusters, leveraging multiple machines for computation.

2.Lazy Evaluation:

Dask employs lazy evaluation, meaning it builds a task graph rather than immediately executing operations. This flexibility enables Dask to optimize computations more effectively and provides better control over when and how computations are performed.

3.Scalability:

Dask is highly scalable and can handle datasets larger than memory by automatically partitioning and processing data in chunks. This scalability is particularly beneficial when dealing with datasets that don't fit into the memory of a single machine.

4.Integration with Existing Tools:

Dask integrates well with popular data science tools such as Pandas, NumPy, and Scikit-Learn. Users can seamlessly transition and extend their workflows, combining the ease of use of Pandas with the scalability of Dask.

5.Task Scheduling:

Dask provides a flexible task scheduler, allowing dynamic task scheduling on various computing resources. This feature is advantageous for optimizing resource utilization in distributed computing environments.

5. **Conclusion**: 

1.Strategically loading essential portions of the dataset in Python offers advantages such as improved memory efficiency, faster startup times, and real-time processing capabilities. However, it may require more thoughtful code design and management to handle the loading and processing of data in chunks.

2.Chunking provides advantages in scenarios involving large datasets, real-time processing, memory efficiency, and parallel processing. However, it may introduce complexity as you need to manage the state between data chunks and potential dependencies. The choice between chunking and loading the entire dataset depends on the specific task and dataset size.

3.Using data type optimization in Python allows for more efficient use of memory, improved performance, and reduced storage space usage. This is particularly important for handling large datasets and applications that require high performance. Traditional approaches might overlook these details, resulting in resource wastage and performance degradation.

4.Adopting sampling methodologies in Python provides computational and memory efficiency, facilitates quicker exploratory analysis, and is particularly beneficial for large datasets. Traditional approaches without sampling may face challenges related to computational resources, memory, and real-time processing. Sampling is a valuable technique for extracting meaningful insights when dealing with vast amounts of data.

5.Dask is advantageous for large-scale, distributed computing tasks and scenarios where datasets exceed memory limits. Pandas, on the other hand, excels in ease of use, performance with smaller datasets, and benefits from a well-established ecosystem. Depending on the specific requirements and dataset sizes, users may choose to use Pandas, Dask, or a combination of both in their workflows.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/BDM/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
