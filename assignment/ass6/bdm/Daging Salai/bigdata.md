<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 6: Mastering Big Data Handling

### Group Name: Daging Salai
### Group Members

| Name                            | Matrix Number |
| :------------------------------ | :-----------: |
| Nur Shahirah Jailani            |MEC233005      |
| Mustafa Ghazi Talab             |MCS212012      |

### 📂 Folder content:
* [💻 Assignment 6](https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/Daging%20Salai/BigDataHandling.ipynb)
* [💻 Report](https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/DagingSalai/bigdata.md)

1. **Pick a Big Dataset**: We chose our dataset from Kaggle which is TripAdvisor Hotel Reviews (1.3GB). The dataset consists of 2 csv files which are the offerings and reviews. We chose reviews csv files that will be use in this assignment.

2. **Loading the Dataset**: We linked to Kaggle using the API by uploading the kaggle.json file. It offers us a zip file called 'hotel-reviews.zip,' which we must unzip in order to access the two csv files contained within. Then we mount them on Google Drive. 

3. **Strategies for Big Datasets**: 

   - *Load Less Data*: Load less data which is load only required columns has reduce memory usage from 1.3 GB to 253.7 MB.

   - *Use Chunking*: Chunk has reduced the memory usage from 2.64 GB to 1.99 GB by subdividing dataset into smaller part.

   - *Optimize Data Types*: After optimized the Data Types into uint8,category and datetime64, the data frame size has reduce 10% which is from 1.29 GB to 1.16 GB.

   - *Sampling*: After sampling, memory usage has tremendously reduced which is from 1.3 GB to 132.5 MB if used 10% of sample.

   - *Parallelize with Dask*: Reading dataframe and merging dataframe using dask reduced the wall time from 30.1s to 20.1s.

4. **Comparative Analysis**: 

    **1. Memory usage**
    - Traditional Methods: Batch Processing. Typically involves processing large datasets in batches. Memory usage can be high as the entire batch needs to be loaded into memory for processing.
    - Advanced Strategies: In-Memory Processing. Utilizes in-memory processing techniques where data is kept in RAM, significantly reducing the need to read and write to disk. This can lead to lower memory usage and faster processing.

    **2. Computation Time**
    - Traditional Methods: Slower computation time, especially for large datasets.
    - Advanced Strategies: Generally faster due to parallelism, in-memory processing, and real-time capabilities.

    **Advantages of Advances Strategies**
    **1. Load Less Data:** 
    - Lower Memory Requirements: Minimizes memory usage, particularly beneficial for systems with limited resources.
    - Faster Query Response: Improves query response times by focusing on loading only essential data.

    **2. Chunking:**
    - Efficient Storage: Enhances storage efficiency by breaking data into manageable chunks, enabling efficient retrieval.
    - Parallel Processing: Facilitates parallel processing and distributed computing, improving scalability and performance.

    **3. Optimize Data Types:**
    - Faster Computations: Optimizes data storage and retrieval, speeding up computations.
    - Memory Efficiency: Reduces memory footprint, allowing for the efficient use of available memory resources.

    **4. Sampling:**
    - Reduced Processing Time: Speeds up analytics by working with a representative subset of the data.
    - Resource Efficiency: Reduces the amount of data to be processed, saving computational resources and improving efficiency.

    **5. Parallelized with Dask :**
    - Scalability: Enables scalable parallel computing across clusters, accommodating growing data volumes.
    - Resource Optimization: Efficiently utilizes computational resources, leading to improved performance.

5. **Conclusion**: <br> 
In conclusion, the advanced strategies for handling big data, including sampling, chunking, loading less data, parallelized processing with Dask, and optimizing data types, collectively contribute to overcoming the challenges associated with large and complex datasets. 

- Enhanced performance. Optimizing data types contribute to improved performance. These strategies reduce memory requirements, speed up data retrieval, and enhance query performance. 
- Minimized data transfer and storage costs. Loading less data and optimized data types contribute to reduced data transfer and storage costs. By only working with necessary data subsets and optimizing storage formats, organizations can achieve significant cost savings.
- Scalability and parallel processing. The strategies support scalability by enabling parallel processing. Chunking and parallelized processing with tools like Dask facilitate the distribution of computations across multiple nodes or cores, enhancing speed and efficiency.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/BDM/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)




