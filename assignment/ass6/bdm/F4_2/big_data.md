<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Assignment 6: Mastering Big Data Handling

Team members name:\
LEE SEOW MING THERESA (MCS231013)\
SITI NORAFIZAH BINTI AB AZIZ (MCS231018)

## Task 1: Pick a Big Dataset

### Game Recommendations on Steam

A dataset of games, users and reviews for building recommendation systems.
The dataset contains over 38 million cleaned and preprocessed user recommendations (reviews) from a Steam Store - a leading online platform for purchasing and downloading video games, DLC, and other gaming-related content. Additionally, it contains detailed information about games and add-ons.

## Task 2: Loading Data
Step loading data and read data through Pandas:

## Task 3: Strategies for Big Datasets

Apply five smart strategies to handle large datasets effectively.


## Discussion for each of the big data handling techniques as below:

1. Load Less Data:

When dealing with massive datasets, loading the entire dataset into memory can be impractical due to resource constraints. In such cases, selectively loading a subset of the data becomes a viable strategy. This approach significantly reduces memory requirements and accelerates loading times. However, it comes with the trade-off of limiting the ability to perform analyses on the entire dataset. Load less data is particularly useful for exploratory data analysis tasks where only a portion of the data is needed for initial insights.

2. Chunking:

Chunking involves breaking down large datasets into smaller, more manageable chunks. Each chunk is processed independently, reducing the strain on memory and enabling parallel processing. This technique is well-suited for scenarios where the dataset is too large to fit into memory, and computations can be performed on individual chunks sequentially or in parallel. While chunking offers advantages in terms of resource efficiency, it requires additional logic to handle chunk-wise computations and may involve increased input/output operations.

3. Optimize Data Types:

Optimizing data types involves selecting the most space-efficient data types for each column in a dataset. By choosing data types that accurately represent the data while minimizing memory usage, substantial reductions in memory requirements can be achieved. This technique is effective for improving computational efficiency and is particularly relevant when dealing with datasets containing numerical values. However, careful consideration is necessary to avoid introducing precision issues or other unintended consequences.

4. Sampling:

Sampling is a technique that involves selecting a representative subset of the data for analysis instead of analyzing the entire dataset. This method provides a quick overview of the dataset and facilitates faster computations during exploration. While sampling is effective for gaining insights into the general characteristics of the data, it may not capture the full diversity of the dataset. Furthermore, results obtained from a sample may be subject to sampling bias, impacting the accuracy of certain analyses.

5. Parallelize with Dask:

Parallelization with Dask leverages distributed computing to scale computations across multiple cores or even distributed clusters. This technique allows for efficient parallel processing, making it well-suited for handling large datasets. Dask introduces a lazy evaluation approach, optimizing computation by postponing execution until necessary. While parallelization with Dask offers high scalability and computational speed, it requires additional setup and understanding of distributed computing concepts. It provides a global view of the data, enabling analyses on the entire dataset in a distributed manner.


## Task 4: Steps for Using These Strategies

a. Data Understanding

b. Data Preprocessing
- Check for missing value
- Check for duplicate value

c. Process data types

### Method 1: Load Less Data

Strategically load only the essential portions of the dataset to optimize memory usage.
The False value in 'Mac' and 'Linux' is more than True around 74.41% and 82.23%, so decided to load data without column 'Mac' and 'Linux' of game.csv.\
Processing Time has reduced from 0.40233731269836426 to 0.22 seconds.\
System RAM Usage has reduced from 63.9% to 61.57%.\
Memory usage has reduced from 3.7+ MB to 3.6+ MB.


### Method 2: Use Chunking

Process the data in smaller pieces to avoid memory issues.

In order to concat for all 3 csv files, the chunking technique has been used, the original file unable to merge all the 3 csv files as it will cause system RAM clash.

Processing Time is 224.17 seconds.\
System RAM Usage is 7.40% / 13.1 MB

### Method 3: Optimize Data Types
Fine-tune data types to maximize efficiency and minimize memory consumption.

Result after fine-tune data types as below:

Processing Time: 1923.23 seconds\
System RAM Usage After Conversion: 37.70%\
Memory usage for df_game, df_rec, and df_users is 13.1 MB, 4.1 GB, 315.6 MB.

### Method 4: Sampling
 Implement sampling methodologies to extract meaningful insights from a subset of the dataset.

Memory usage is 876.3+ MB\
Processing time is 0.00 seconds\
System memory usage for combining is 2313.05 MB\

### Method 5: Parallelize with Dask:
To extends pandas to enable parallel and distributed computing. It's particularly useful for handling larger-than-memory datasets.

Result of Parallelize with Dask:\
RAM Usage: 4960.21 MB\
Processing Time: 136.04 seconds\
Total Size: 20.82 GB

## Task 5: Comparative Analysis

The provided output shows the resources and processing time for the chunked approach and the entire dataset approach.

1. Resources for final_combined_chunks:
The final_combined_chunks DataFrame has 60,651 entries and 22 columns.
It displays the non-null count and data types for each column.
The memory usage is reported as 22.9 MB.

2. Processing time for entire dataset:
The processing time for reading the entire dataset is 32.92 seconds.

3. Games DataFrame (Full):
The games_df_full DataFrame includes columns such as app_id, title, date_release, and others.
It provides information on game titles, release dates, compatibility, ratings, and pricing.
The date_release column has been converted to a datetime format.

4. Recommendations DataFrame (Full):
The rec_df_full DataFrame contains columns like app_id, helpful, funny, date, and others.
It includes information about user recommendations, helpful/funny votes, and review details.

5. Users DataFrame (Full):
The users_df_full DataFrame includes columns such as user_id, products, and reviews.
It provides information about user IDs, the number of products owned, and the number of reviews submitted.

Overall, the chunked approach allows you to process the data in smaller portions, reducing memory usage. However, it may require additional processing steps to handle chunks individually. The entire dataset approach loads the complete dataset into memory, which can be faster but may consume more resources.

## Task 6: Conclusion

In conclusion, the comparative analysis between different data processing strategies provides valuable insights into the trade-offs and benefits associated with each approach. The original data processing method, while simple and intuitive, may exhibit limitations in terms of memory usage and processing time, particularly when dealing with large datasets.

The choice of which strategy performs better depends on the specific analytical goals, dataset characteristics, and available resources. For large datasets, strategies like chunking, optimizing data types, and parallelizing with Dask tend to offer better performance in terms of reduced memory usage and faster processing times. However, for smaller datasets or quick exploratory analysis, simpler approaches like loading less data or using the original processing method may suffice. A combination of strategies may often yield the best results in balancing performance and resource efficiency.
