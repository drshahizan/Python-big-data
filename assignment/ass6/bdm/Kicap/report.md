# Assignment 6: Mastering Big Data Handling

### Group Name: Kicap
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Nabila Husna binti Rosli            |MCS231009      |
| Nur Azimah binti Mohd Salles               |MCS231011      |


1. **Pick a Big Dataset**: The chosen dataset for our Assignment 6 is the Restaurant Reviews that we got from Kaggle. The dataset consists of 2 csv files which are the pre-covid review and post-covid reviews. 

2. **Loading the Dataset**: Use Python and Pandas to load your chosen dataset into your Colab notebook. You can either upload it from your computer or directly from an online source. By uploading the kaggle.json file, we connected the to Kaggle using the API to get the dataset. It gives us a zip file which is the 'restaurant-reviews.zip' file and we need to unzip it to access the 2 csv files inside. Then, we decided to concat both files and mount int the google drive. 

3. **Strategies for Big Datasets**: Initial dataset information:

    - RangeIndex: 5572493 entries, 0 to 5572492
    - Columns: 21 entries, business_id to date_
    - Dtype: float64(3), int64(6), object(12)
    - Memory usage: 8.8 GB.

   Five smart strategies implemented:

   - *Load Less Data*: Loaded the first 1000 rows to create a smaller subset for quick exploration with a memory usage of 0.0001565814 GB.

   - *Use Chunking*: Measured time to read the entire CSV file (1min 4s) and setup chunked reader (5.06 ms), showcasing the efficiency of processing smaller portions.

   - *Optimize Data Types*: Reduced memory usage from 8.8 GB to 4.9 GB by optimizing data types to float16, int16, and category.

   - *Sampling*: Randomly sampled 1000 rows from the original DataFrame, creating a smaller subset for meaningful insights.

   - *Parallelize with Dask*: Utilized Dask for parallel and distributed computing on larger-than-memory datasets.
       - This is the comparison of the computational time of several operations we have tried:


        | Operation                 | Pandas Time (seconds) | Dask Time (seconds) |
        |---------------------------|-----------------------|----------------------|
        | Mean Stars                | 0.1015                | 0.5184               |
        | Filtering Data            | 4.3887                | 1.4118               |
        | Mean Stars by City        | 0.5483                | 1.0637               |
        | Review Counts by Stars    | 0.1234                | 0.0925               |


  
4. **Comparative Analysis**: 

    | Aspect             | Pandas                                      | Dask                                             |
    |--------------------|---------------------------------------------|--------------------------------------------------|
    | **Memory Usage**   | Limited by available memory; loads entire dataset into memory | More scalable, operates on larger-than-memory datasets by dividing into partitions; adaptive memory usage |
    | **Computation Time**| Increases linearly with dataset size          | Significantly reduces computation time, especially for parallelizable operations; parallelizes operations by dividing into partitions |
    | **File Size**      | File size determined by dataset and data types | Efficiently handles larger datasets without proportional increase in file size |
    | **Lazy Evaluation** | No lazy evaluation; loads data eagerly      | Lazy evaluation minimizes unnecessary loading of data; efficient handling of operations without loading entire dataset |
    | **Parallelization**| Limited parallelization                     | Parallelizes operations by dividing the dataset into partitions; efficient parallel processing |
    | **Partitioning**   | N/A                                         | Requires careful consideration of partitioning strategy |
    | **Overheads**      | N/A                                         | Overheads associated with task scheduling and communication |


5. **Conclusion**: 

- **Loading less data** is a common strategy when working with large datasets, allowing you to save memory and speed up initial data exploration tasks. However, keep in mind that working with a subset may not represent the full dataset, and decisions based on this subset should be made with caution.

- The primary benefit of **optimizing data types** is to reduce memory usage, making it more efficient for handling and processing large datasets. It's important to choose the appropriate data types for columns to balance memory efficiency with the precision needed for analysis.

- Using **chunks** is beneficial when dealing with large datasets that may not fit into memory. Instead of loading the entire dataset at once, it is read in smaller chunks. This allows for more efficient memory usage and processing. In the example, the time to read the entire dataset using chunks might be longer than reading it without chunks. However, the benefit becomes apparent when the dataset is too large to fit into memory, as chunks allow you to process and analyze portions of the data at a time.

- **Sampling** is a useful technique for working with large datasets when you want to get a representative subset for exploratory data analysis or model building. The random_state parameter is set for reproducibility, ensuring that the same random rows are selected if the code is run again with the same random state.

### **After using Dask:**
* Traditional methods (pandas) are suitable for smaller datasets but may face limitations in terms of memory and computation time for larger datasets.
* Advanced strategies (Dask), offer scalability, efficient memory usage, and parallelization, making them highly advantageous for big data scenarios.
* The choice between traditional methods (pandas) and advanced strategies (Dask) depends on the size and complexity of the data, available computing resources, and the specific requirements of the analysis.


## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/BDM/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
