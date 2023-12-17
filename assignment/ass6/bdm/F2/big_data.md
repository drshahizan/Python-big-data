<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 6: Big Data Handling

### Group Name: F2
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Thong Yee Moon            |MCS231001      |
| Lye Kah Hooi             |MCS231010      |

### Dataset - Brewery Operations and Market Analysis Dataset
- Pick a Big Dataset: Start by choosing a suitable dataset.
- It's big—over 700 MB.
- This dataset presents an extensive collection of data from a craft beer brewery, spanning from January 2020 to January 2024. It encapsulates a rich blend of brewing parameters, sales data, and quality assessments, providing a holistic view of the brewing process and its market implications
[Kaggle Link](https://www.kaggle.com/datasets/ankurnapa/brewery-operations-and-market-analysis-dataset)

### Big Data Handling 
#### Step 1 
- Connect with google drive
- Upload API token to allow connect with Kaggle in upcoming step.

#### Step 2 Loading the Dataset: 
- Use Python and upload the dataset directly from an online source which is Kaggle
- The size of the dataset is 1.06 GB in a compressed condition whereas after unzip, 4.25 GB.

Zip condition = 1.06 GB

Unzip condition = 4.25 GB

- The dataset contains 10 millions row and 20 columns/attributes. The attributes of data contained

| Dtype    | Number of attributes    |
| :--------| :--------    |
| float64    | 10    |
| int64    | 5    |
| object    | 5    |

#### Step 3 Strategies for Big Datasets: 
Apply five smart strategies to handle large datasets effectively
The steps for using these strategies can be referred to Google Collab uploaded.
<br/>
a. Parallelize with Dask:
- Dask is a powerful library that extends pandas to enable parallel and distributed computing. It's particularly useful for handling larger-than-memory datasets..

b.Sampling:
- Implement sampling methodologies to extract meaningful insights from a subset of the dataset.

c. Use Chunking:
- Process the data in smaller pieces to avoid memory issues.

d. Load Less Data:
- Strategically load only the essential portions of the dataset to optimize memory usage.

e. Optimize Data Types:
- Fine-tune data types to maximize efficiency and minimize memory consumption.

#### Step 4: Comparative Analysis: 

Below is the summary table for 5 strategies mentioned and the comparison table when compared to traditional Pandas dataframe. 

Summary Table: 
| No. | Action: Read File                           | Pandas (Control) | Parallelize with Dask | Chunking | Sampling using 70% of dataset | Load Less Data (Less 4 columns) | Optimize Data Type |
| --- | ------------------------------- | ----------------- | ---------------------- | -------- | ----------------------------- | ------------------------------- | ------------------- |
| 1   | Computation Time (second)       | 65.5799           | 0.021                  | 76.779   | 12.8338                       | 54.6219                         | NA                |
| 2   | Memory Usage (GB)               | 4.25              | 4.25                   | 4.25     | 3.03                          | 3.39                            | 1.33              |
| 3   | Dataframe Size (GB)             | 4.25              | 0 (due to lazy evaluation nature of Dask)  | 4.25     | 3.03                          | 3.39                            | 1.33              |

Comparison Table (Compared with Pandas): 
| No. | Performance Metrics                        | Pandas (Control) | Parallelize with Dask | Chunking | Sampling using 70% of dataset | Load Less Data (Less 4 columns) | Optimize Data Type |
| --- | ----------------------------------------- | ----------------- | ---------------------- | -------- | ----------------------------- | ------------------------------- | ------------------- |
| 1   | How many times faster (times)              | -                | 3116.75                | 0.72     | 5.11                          | 1.2                             | NA                |
| 2a  | Total memory usage reduced (GB)            | -                | 0                      | 0        | 1.22                          | 0.86                            | 2.92              |
| 2b  | Percentage of memory usage reduced (%)    | -                | 0%                     | 0%       | 29%                           | 20%                             | 69%               |
| 3   | Total size reduced (GB)                   | -               | NA                      | 0        | 1.22                          | 0.86                            | 2.92              |

#### Step 5 Conclusion: 

In conclusion, Dask can perform much more faster than Pandas. The reported size of the Dask DataFrame as "0.00 GB" in the output is likely due to the lazy evaluation nature of Dask. Dask operates on larger-than-memory datasets by breaking them into smaller chunks and performing operations on those chunks in a lazy manner. This means that Dask doesn't actually compute the result or load the entire dataset into memory until an action is explicitly triggered.

Total runtime for "after using Chunking" is higher than "before using Chunking". It's important to note that the benefits of chunking are often more pronounced when dealing with datasets that are significantly larger than the available memory, as chunking allows us to work with data in a memory-efficient manner. In scenarios where the entire dataset easily fits into memory, chunking might not provide a substantial performance improvement and can even introduce some additional overhead.

Both Sampling and Load Less Data show good performance in reducing runtime and memory usage, whereas Optimize Data Type able to significantly reduce the memory usage, which is 69% reduction compared to the original dataset.

By employing these strategies, we can effectively handle and analyze big data while overcoming challenges related to memory, computational resources, and efficiency. These approaches enable the extraction of meaningful insights from large datasets without overwhelming the available resources.



## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.
