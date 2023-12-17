<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# Assignment 6: Mastering Big Data Handling

### Group Name: MEOW
### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | :-------------: |
| NADIA SYAFIQAH BINTI ZULKIPLI  | A21EC0098      | Assignment 6 |
| ALIYA ZARENA BINTI ZAINULANUAR   |  A21EC0013    | Assignment 6  |

##  📚 Objective
The objective of this assignment is to explore the management of big data processing in data science. Big data processing involves the systematic handling and analysis of vast and complex datasets that exceed the capabilities of traditional data processing methods. It encompasses the storage, retrieval, and manipulation of massive volumes of information to extract valuable insights.

## 1. Dataset Selection

We able to find and retrieve a dataset from Kaggle, [Amazon Books Reviews](https://www.kaggle.com/datasets/mohamedbakhet/amazon-books-reviews) where we used both files with 1GB. This dataset is about feedback about 3 million users on 212404 unique books the data set is part of the Amazon review Dataset from May 1996 - July 2014.

## 2. Data Preparation & Cleaning

### 2.1 Import necessary libraries
```python
import pandas as pd
import numpy as np
import gc
```

### 2.2 Load dataset

Firstly, we will upload dataset by using Kaggle API

*   Import Kaggle API file

```python
from  google.colab import files
files.upload()
```

*   **files.upload()** is used to intiated a file upload dialog box which enable users to upload files. User have to navigate the intended file for upload, select the file and click **'Open'**
*   Install Kaggle Package

Setting up Kaggle credentials on Google Colab allows interaction with the Kaggle API for dataset downloads.  This procedure allows users to access datasets without having to manually download them, which is very useful when dealing with large datasets.

```python
!pip install -q kaggle

!mkdir -p ~/.kaggle #Create a Kaggle Directory
!cp kaggle.json ~/.kaggle/ #Upload the Kaggle API Token
!chmod 600 ~/.kaggle/kaggle.json #Set File Permission
```

*   Download the dataset
```python
!kaggle datasets download -d mohamedbakhet/amazon-books-reviews
```

*   Unzip the downloaded dataset
```python
!unzip amazon-books-reviews.zip
```

- Read the dataframe
```python
path = 'Books_rating.csv'
df = pd.read_csv(path)
```

### 2.3 Explore dataset information

To explore the dataset columns name and the first five rows of the dataframe, we use **df.head()**
```python
df.head()
```
<br>

We can get dataframe information via df.info(), such as column names, data types, entries, memory usage, and so on.
```python
df.info()
```

To determine the number of items (cells) in a dataframe, run this command:
```python
df.size
```

To analyze the dataframe's rows and columns, run this command:
```python
df.shape
```

To observe the descriptive statistics of the dataframe, run this command:
```python
df.describe()
```

The table above summarizes all of the statistics for the relevant numerical variables, such as mean, median, standard deviation, and quantiles.

### 2.4 Handle missing values

This procedure entails locating and addressing missing or null values in the dataset to maintain data integrity and eliminate potential biases or inconsistencies in the analysis caused by the absence of information in specific entries.

*   Check for the missing data for each column

To check missing data, run this command:
```python
df.isna().sum()
```

*   Handle the missing values by dropping it from the dataframe

To handle missing values, run this command:
```python
df = df.dropna()
```

*   Double check the missing data after drop it

```python
df.isna().sum()
```

### 2.5 Remove duplicates

This function used to remove the duplicates rows that were found in the dataframe.
```python
def drop_duplicates(df):
    old = df.shape[0]
    df.drop_duplicates(inplace=True)
    new = df.shape[0]
    count = old - new
    if (count == 0):
        print("No duplicate rows were found.")
    else:
        print(f"{count} duplicate rows were found and removed.")
````

- Use the above function to remove the duplicates rows
```python
drop_duplicates(df)
```

## 3. Strategies for Big Datasets

### 3.1 Load Less Data

By loading only the essential portions of the dataset to optimize memory usage.

- Display the columns name of the dataframe to ensure accurate selected columns used
```python
df.columns
```

- Select the specific columns that we want to use
```python
used_columns = ['Title', 'review/helpfulness', 'review/score', 'review/time', 'review/text']

df_less_data = pd.read_csv(path, usecols = used_columns)
```

- To display the memory usage of the dataframe after loading less data
```python
df_less_data.info()
```
From the above info, we can observed that the memory usage is being reduced from 228.9+ MB to 114.4+ MB.

### 3.2 Use Chunking

When datasets are too massive to be loaded and processed at once due to memory constraints, chunking allows breaking down the dataset into smaller, more manageable portions or chunks. Each chunk can be processed independently, enabling analysis, manipulation, or modeling on parts of the dataset without requiring the entire dataset to be held in memory simultaneously.
```python
chunk_size = 500000
num = 1
for chunk in pd.read_csv(path, chunksize = chunk_size):
  chunk.to_csv('chunk'+str(num)+'.csv', index = False)
  gc.collect()
  num+=1
```

After chuncking, see whether we can read the chunk and check the info.
```python
df = pd.read_csv('chunk1.csv')
df.head()
```

### 3.3 Optimize Data Types

We need to review the dataset information for the columns and their data types.
```python
df.info()
```

We can see from the information that there are 2 columns with float64. One of the most common problems with pandas is that it constantly loads float data as float64. We may have lowered the size of our dataset by optimizing this memory. To save memory, we must convert it to **'float16'** or **'float32'**. Here, we will convert it to **'float16'**.

Not only that, column that have data type of 'int64' will also be converted to **'int16'**.

```python
for column in df.columns:
  if df[column].dtype == 'float64':
    df[column] = df[column].astype('float16')
  if df[column].dtype == 'int64':
    df[column] = df[column].astype('int16')
```

- Observe the memory usage after optimizing the data type
```python
df.info()
```

As you can see, the memory usage has been reduced to 29.6+ MB from 38.1+ MB.

### 3.4 Sampling

Sampling data known as choosing a selection of samples from a larger dataset in order to draw conclusions about the wider population from which the data is derived. Because it enables analysts to make inferences about a population without having to examine the complete dataset, which may be difficult or time-consuming, sampling is an essential tool in statistics and data analysis. In this case study, we choose two types of sampling which is **simple random sampling** and **stratified sampling**.

#### 3.0.4.1 Simple Random Sampling

Using simple random sampling, every segment of the population has an equal chance of being selected for the sample. It can be used on our dataset's numeric and categorical columns.

```python
df.info()
```

- This is the default method in sampling which it will select one row from the dataset randomly
```python
df.sample()
```

**Example 1:** We can try to choose two random rows by using the **"n" parameter** too and compare the results.

This is the first row of sampling:

- To generate one row, run this command:
```python
first_row = df.sample(n = 1)
```

- To display the first random row, run this command:
```python
first_row
```

This is the second row of sampling:

- To generate another row, run this command:
```python
sec_row = df.sample(n = 1)
```

- To display the second random row, run this command:
```python
sec_row
```

Based on both results, we can see that:
- Both have a review score of 5.0, suggesting that users rated both books highly.
- The first entry's "Review Helpfulness" score is 0/2, meaning that two people voted it helpful and none against. With a score of 0/0, the second entry is unvoted.

**Example 2:** We use **"frac" parameter** to specify the fractions of rows and columns. In this case, we will be using 25% sample of data frame. You may adjust the frac based on your preference.

Generating new dataset with the fraction of 25%
- 25% = 0.25

```python
frac_row = df.sample(frac = 0.25)
frac_row
```

A method to check whether the result is 0.25 times of dataset or not:
```python
if (0.25*(len(df)) == len(frac_row)):
    print( "This is the sample with 25% fraction")
    print(f"The size of original dataset: {len(df)} while " + f"the size of fraction dataset: {len(frac_row)}")
else:
    print("This is not the sample with 25% fraction")
    print(f"The size of original dataset: {len(df)} while " + f"the size of fraction dataset: {len(frac_row)}")
```

#### 3.4.2 Stratified Sampling
Using stratified sampling, the population is divided into several subgroups (*strata*) according to specific criteria. Next, from each stratum which called as *singular form of strata*, a random sample is being taken then.

**Example:** We select 10 rows from the records where we want to sample out 8 rows based on the "review/score" column

- Select 10 random rows
```python
rows = df.sample(n = 10)
rows
```

**First Method:** Disproportionate Sampling

The sample size of each stratum is equal irrespective of the population size of the stratum. Here, we separate the records into groups based on "review/score" where sampling 3 random from each score

- Group the DataFrame by 'review/score'
```python
grouped = rows.groupby('review/score', group_keys=False)
```

- To sample 3 rows from each group, run this command:
```python
grouped_rows = grouped.apply(lambda x: x.sample(min(3, len(x))))

grouped_rows
```

**Second Method:** Proportionate Sampling

The sample size of each stratum is proportional to the population size of the stratum.

Sample 80% of records proportionately
- 80% = 0.8

```python
grouped_rows_frac = rows.groupby('review/score', group_keys=False).apply(lambda x: x.sample(frac=0.8))
grouped_rows_frac
```

Based on the both methods, we can analyze that the **"review/score"** for 5.0 and 4.0 is holding 37.5% each, while as for 2.0 and 1.0 is holding 12.5% each. Moreover, we can see there is no score of 3.0 because refer to the selected 10 random samples does not contain score of 3.0

### 3.5 Parallelize with Dask

```python
!pip install dask
```

We can check the detail information about Dask package using the command below:
```python
!pip show dask
```

- Import dask and other necessary libraries
```python
import dask
import dask.dataframe as dd
from dask.diagnostics import ProgressBar
```

- Load data with dask by specify the dtype for the 'Id' column
```python
dtype = {'Id': 'object'}
```

- Read the CSV file with specified dtype
```python
file_path = 'Books_rating.csv'
dask_df = dd.read_csv(file_path,dtype=dtype)
dask_df
```

In loading dataset, dask have same functionality "read.csv' with the pandas, but in dask, it allows to operate on large memory datasets compared to pandas. We can see that pandas take 46 seconds to load the data while the dask only takes 0 seconds to complete run it.

```python
dask_df.columns
```

- To check for any missing values, run this command:
```python
missing_values_count = dask_df.isna().sum().compute()
missing_values_count
```

- To handle missing values, run this command:
```python
dask_df = dask_df.dropna()
check_missing_value_count = dask_df.isna().sum().compute()
check_missing_value_count
```

**Example:** Calculates the mean of the 'review/score' based on the 'User_id' column in parallel across Dask partitions.

```python
import time
```

- To record the start time, run this command:
```python
start_time = time.time()
mean_score = dask_df.groupby('User_id')['review/score'].mean()
```

- To trigger computation and display the result, run this command:
```python
result = mean_score.compute()
print(f"Mean Review Score: {result}")
```

Based on the results, the 'User_id' column displays the mean review scores for every unique user, which represent the overall mood of their reviews. The values fall between 1.0 and 5.0, with higher numbers correspond to more favourable ratings.

**Example:** How the parallelization with Dask works.

**Note:** Initial functions for calculating the mean review score would remain the SAME
```python
import dask
from dask import delayed
```

```python
complex_result = dask_df.groupby('User_id')['review/score'].mean()
```

```python
parallelize_score = delayed(complex_result)
parallelize_score
```

As we can see above, it wont show the value of parallelize score, therefore we need to apply *compute()* function in order to get the result. We can also use *visualize()* function to see the parallel execution will look like.

```python
parallelize_score.visualize()
```
```python
new_result = parallelize_score.compute()
print(f"Mean Review Score: {new_result}")
```
We can see that the results from pandas and Dask are similar; however, the difference is that Dask can manage several pandas dataframes and store them if memory is limited. Furthermore, dask provides a delayed approach for parallelizing execution, allowing data storage to be used more efficiently.

- To record the end time, run this command:
```python
end_time = time.time()
```

- To calculate the elapsed time, run this command:
```python
elapsed_time = end_time - start_time
```

- To calculate the memory usage of the Dask DataFrame, run this command:
```python
memory_usage = dask_df.memory_usage(deep=True).compute()
```
```python
print(f"Memory Usage: {memory_usage}")
print(f"The Elapsed Time to calculate the mean review score by Dask: {elapsed_time} seconds")
```
## 4. Comparative Analysis

Table 1 below shows the comparison between traditional methods and advanced strategies in several aspects for handling big datasets.

| Aspect | Traditional Methods | Advanced Strategies(Dask) |
| -------- | -------- | -------- |
| **Memory Usage** | High | Optimized at each step |
| **Computation Time** | Longer processing time | Varies depending on the steps as some steps may be faster |
| **File Size** | Large | Smaller chunked / optimized files |
| **Handling NaNs** | Drop NaN values | Handle missing values as needed |
| **Load Dataset** | Loads entire dataset into memory | Loads essential columns only |
| **Data Types** | Unoptimized data types | Optimized data types for efficiency|
| **Sampling**         | Longer time processing              | Implemented for subset analysis   |
| **Parallelization**  | Not utilized(limited)                   | Faster and efficient completion of tasks |


<div align="center">

**Table 1**
</div>

<br>

Here are meaningful insights into the advantages gained through the adoption of those strategies:



a) Memory Efficiency
*  Loading less data and optimizing data types result in a significantly smaller memory footprint than the traditional approach.
*   Chunking and optimized data types significantly decrease memory usage which enable efficient storage and manipulation of large datasets without exhausting system resources.

<br>

b) Computation Time
*   Techniques such as chunking and parallelization (with Dask) result in faster processing speeds by allowing operations to be executed concurrently on smaller subsets or across several processors.

<br>

c) File Size Reduction
*   Chunked files and optimized datasets occupy considerably smaller storage space compared to the original dataset. This reduction in file size simplifies data management and storage.

<br>

d) Parallel Computing
*   Utilizing Dask for parallel computing enables distributed and parallel execution, leveraging multicore processors or distributed computing clusters for faster computations and analysis of large-scale datasets.

<br>

e) Scalability & Flexibility
*   Advanced strategies facilitate scalability by enabling the processing of larger datasets without overwhelming system resources.
*   The ability to perform analysis on smaller subsets (sampling) or chunks of data allows for more flexible and iterative analysis without the need to load the entire dataset.

## 5.0 Conclusion

The adoption of advanced strategies in handling big data offers substantial improvements in memory efficiency, computation speed, file size reduction, data quality, scalability, and parallel processing capabilities. These advantages empower data scientists and analysts to efficiently manage, process, and derive insights from massive and complex datasets, overcoming the limitations of traditional methods and enhancing the overall productivity and effectiveness of data-driven decision-making processes. Several key strategies include:

1. **Load Less Data:**
   - By utilising the `usecols` parameter to define a subset of columns ({['Title','review/helpfulness','review/score',
   'review/time','review/text']}), the code snippet loads less data from a CSV file. The result of DataFrame ({df_less_data}) minimises it's memory footprint and speeds up data loading and processing by selectively loading only the relevant columns. Enhancing overall efficiency is a benefit of this strategy, particularly when dealing with huge datasets when analysis may not require all columns. A more effective data handling strategy is facilitated by the reduced data amount, which enables faster exploratory data analysis as well as more streamlined and resource-efficient operations.

2. **Chunking:**
   - In the provided code, chunking is implemented using the pandas `Books_rating.csv` function with a specified chunk size of `500,000 rows.` To enable more managed and parallelized processing, each chunk read from the big dataset is saved as a distinct CSV file `(e.g., "chunk1.csv," "chunk2.csv").` This method reduces memory needs, permits parallelized actions on each chunk, and facilitates more efficient processing by dividing the dataset into smaller, more manageable pieces. Additionally, memory management during the iterative reading and storing of chunks is aided by the explicit memory release performed by the `gc.collect()` method after each chunk is completed.

3. **Optimize Data Types:**
   - To reduce the DataFrame's memory footprint, the code downcasts data types to more memory-efficient formats like `float16` and `int16.` This benefits in terms of having lesser storage needs, quicker calculations, and better overall performance—particularly with big datasets. Although reducing the size of data types may lead to a decrease in accuracy, this is frequently a trade-off that should be taken into account when aiming for memory economy, especially when the precision loss has little effect on the analysis or outcomes. When working with datasets whose numeric columns take up a lot of RAM in their native formats, this optimisation is quite helpful.

4. **Sampling:**
   - Sampling is a crucial data analysis strategy, with two main techniques being simple random sampling and stratified sampling based on the `"review/score" column.` In contrast, simple random sampling is straightforward, stratified sampling provides a more targeted approach, especially in heterogeneous populations, ensuring accurate representation of diverse groups. Both methods contribute to more efficient data analysis by allowing manageable subsets for processing.

5. **Parallelize with Dask:**
   - Dask makes it possible to parallelize processes effectively, which boosts overall performance and processing speed. Furthermore, Dask gives users fine-grained control over parallel execution with tools like `delayed()`, which let them directly specify and manage calculations. Through the creation of a graph visualisation of the task dependencies, Dask's `visualise()` function facilitates comprehension and optimisation of the parallelized computation. When combined, these characteristics give Dask great power to scale computations and data analysis across distributed computing environments.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

