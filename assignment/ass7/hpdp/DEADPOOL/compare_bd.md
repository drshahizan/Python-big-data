# Assignment 7: Comparison between libraries


### Group Name : DEADPOOL
### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
|MUHAMMAD AMIR JAMIL BIN JAMLUS          | A21EC0202     |Polars|
|KEE SHIN PEARL         | A21EC0190     |Comparison|
|MUHAMMAD IZZUDDIN BIN SHABRIN           | A21EC0083   |Dask|
|UMAR HAZIQ BIN MUHAMAD NORHISHAM            |  A21EC0235   |Pandas|


## Table of Content
1. [Introduction](#introduction)
2. [Dataset Selection](#dataset-selection)
3. [Downloading Dataset](#downloading-dataset)
4. [Installing Libraries](#installing-libraries)
    * [Pandas](#pandas)
    * [Dask](#dask)
    * [Polars](#polars)
5. [Data Preparation and Cleaning](#data-preparation-and-cleaning)
    * [Loading Dataset](#comparative-analysis)
    * [Explore the number of rows & columns, ranges of values etc.](#dask)
    * [Handle missing, incorrect and invalid data](#polars)
    * [Comparative Analysis](#comparative-analysis)
6. [Exploratory Analysis and Visualization](#exploratory-analysis-and-visualization)
    * [Top 10 Rated Anime Titles](#dask)
    * [Number of Ratings per Anime vs. Average Anime Rating](#polars)
7. [Asking and Answering Questions](#asking-and-answering-questions)
    * [What are the top-rated anime titles?](#comparative-analysis)
    * [How many unique users and anime titles are in the dataset?](#dask)
    * [What is the distribution of ratings given by users?](#polars)
    * [Who are the top users with the most rated anime?](#comparative-analysis)
8. [Inference and Conclusion](#inference-and-conclusion)
9. [Reference](#reference)


## Introduction
In this assignment 7, it is a challenge for our group as we delve into working with datasets exceeding 1GB in size with Google Colab. Our primary objective revolves around conducting comprehensive exploratory data analysis (EDA) and employing various data operations to extract insights from our selected dataset. To accomplish this, we'll be exploring 3 useful library tools which are Pandas, Dask and Polars that are functioned for handling large-scale datasets in python. This assignment involves investigating and assessing the efficiency of these tools in terms of their impact on data collection, manipulation, and the overall extraction of insights from these expansive datasets. By involving different libraries and studying the performance, we aim to uncover how each tool's functionalities and optimizations influence the efficiency of our data operations, providing valuable insights into their respective strengths and limitations in handling substantial volumes of data.


## Dataset Selection
The dataset our group had chosen is [Anime Dataset 2023](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset?select=users-score-2023.csv) sourced from Kaggle. This dataset comprises data of 3 csv files, totalling over 70 million records and encompassing 44 columns, resulting in a data size exceeding 8.0GB. For this assignment the one file that we will be using is users-score-2023.csv

Column features and description from the User Score Dataset
| Column    | Description                                      |
|-----------|--------------------------------------------------|
| user_id   | Unique ID for each user.                          |
| Username  | The username of the user.                         |
| anime_id  | Unique ID for each anime.                         |
| Anime Title | The title of the anime.                         |
| rating    | The rating given by the user to the anime.        |

The User Score Dataset enables various analyses and insights into user interactions with anime. By examining user ratings for different anime titles, we can identify highly-rated and popular anime among users. Additionally, you can explore user preferences and watch patterns for specific anime titles. This dataset also forms the foundation for building recommendation systems based on user ratings, helping to suggest anime that align with individual tastes. Furthermore, you can perform collaborative filtering and similarity analysis to discover patterns of similar user interests. Overall, this dataset offers valuable information for understanding user engagement and preferences on the anime platform.

## Downloading Dataset
To begin accessing Kaggle datasets within Google Colab, start by visiting your Kaggle account. Within your account settings, navigate to the API section. If there's a previous token, ensure to invalidate it by selecting "Expire API Token." Following this, generate a new API token by clicking on "Create New API Token." This action will automatically download a 'kaggle.json' file, which contains your credentials, to your local machine.

Now moving back to the project file in Google Colab, we will install the kaggle library:
```python
!pip install kaggle
```

The next code will upload files from your local machine to the Google Colab Notebook. It will locate and upload the 'kaggle.json' file that you downloaded earlier from Kaggle:
```python
from google.colab import files
files.upload()
```

Once uploaded, proceed by running the subsequent commands in another code cell within Google Colab. These commands install the Kaggle package, create the necessary directory, allocate the 'kaggle.json' file into it, and adjust permissions for security:
```python
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

To download the dataset, execute code with actual Kaggle username and dataset name that is selected:
```python
! kaggle datasets download -d dbdmobile/myanimelist-dataset
```

As the file is zipped, we will have to unzip it to extract the dataset from the file downloaded:
```python
! unzip myanimelist-dataset.zip
```


## Installing Libraries
[Pandas]( https://pandas.pydata.org/)

Pandas one of the powerful and popular library within the Python ecosystem. It serve as a foundational tool which is widely used for data manipulation, analysis, and exploration. The library provides a robust arsenal of tools tailored for handling structured data and time-series data, predominantly through its versatile DataFrame objects. What sets Pandas apart is its conventional, offering a user-friendly interface coupled with a rich array of functionalities. From data ingestion to cleaning, manipulation, and in-depth analysis, Pandas empowers users with comprehensive tools, making complex operations more accessible and enabling efficient exploration and understanding of diverse datasets. 

Install Pandas:
```python
!pip install pandas
```

Importing Pandas library:
```python
import pandas as pd
```
  
[Dask](https://www.dask.org/)

Dask is a parallel computing library designed to scale Python workflows. Dask is capable at handling large datasets that don't fit into memory by providing parallel processing capabilities and enabling distributed computing. Dask seamlessly integrates with existing Python libraries, offering DataFrame and Array abstractions that mimic Pandas and NumPy structures. By splitting computations into smaller tasks and utilizing parallelism, Dask can efficiently manages computations across multiple cores or even clusters, enabling the processing of datasets too large.

Install Dask:
```python
!pip install dask
```

Importing Dask library:
```python
import dask.dataframe as dd
```

[Polars](https://pola.rs/)

Polars dataFrame library that is written in Rust which shares similarities with Pandas but mainly on elevating the memory efficiency performance. Polars library is designed to handle large-scale data processing, offering a high-performance alternative to Pandas. Polars leverages the scalability of Rust and performance benefits while providing a Pandas-like unique environment. This enables users who are familiar with pandas to perform data manipulations and transformations more efficiently. Polars’ query engine leverages Apache Arrow to execute vectorized queries. Where is exploits the power for columnar data processing, reducing memory overhead and enhancing computational speed for various operations

Install Polars:
```python
!pip install polars
```
Importing Polars library:
```python
import polars as pl
```

## Data Preparation and Cleaning

### Loading dataset

Pandas :
```python
df = pd.read_csv('users-score-2023.csv')
```

Dask : 
```python
ddf = dd.read_csv('users-score-2023.csv')
```
to trigger the computation on Dask Dataframe:
```python
dask_df= ddf.compute()
```

Polars : 
```python
pol_df = pl.read_csv('users-score-2023.csv')
```

|    | Pandas      |Dask    |Polars     |
|-----------|--------------|--------------|--------------|
| Computation Time (sec) | 16.34       |0.08      |6.49      |
| Memory Usage (MB) | 0     |0      |0     |


### Explore the number of rows & columns, ranges of values etc

* General Statistics

Pandas :
```python
df.describe()
```

Dask : 
```python
dask_df.describe()
```

Polars : 
```python
pol_df.describe()
```

|    | Pandas      |Dask    |Polars     |
|-----------|--------------|--------------|--------------|
| Computation Time (sec) | 3.67     |3.15     |6.25     |
| Memory Usage (MB) |8300.44   |8300.44  | 8297.64    |


* Number of rows and column

Pandas :
```python
df.shape
```

Dask : 
```python
dask_df.shape
```

Polars : 
```python
pol_df.shape
```

|    | Pandas      |Dask    |Polars     |
|-----------|--------------|--------------|--------------|
| Computation Time (sec) | 0     |0      |0     |
| Memory Usage (MB) | 6031.90   |8291.49   | 8291.49  |

### Handle missing, incorrect and invalid data
* Check duplicates
Pandas :
```python
df.drop_duplicates(inplace=True)
```

Dask : 
```python
df.drop_duplicates()
```

Polars : 
```python
pol_df.describe()
```

* Check Number of Null values
Pandas :
```python
df.isnull().sum()
```

Dask : 
```python
dask_df.isna().sum()
```

Polars : 
```python
pol_df.null_count()
```

 ## Exploratory Analysis and Visualization

* Top 10 Rated Anime Titles
  
Pandas :
```python
top_rated_anime = df.groupby('Anime Title')['rating'].mean().sort_values(ascending=False).head(10)
print('Top 10 Rated Anime Titles:')
print(top_rated_anime)
```

Dask : 
```python
client = Client()
avg_ratings = df.groupby('Anime Title')['rating'].mean()
top_rated = avg_ratings.nlargest(10)
plt.figure(figsize=(12, 8))
sns.barplot(x=top_rated.values, y=top_rated.index, palette='viridis')
plt.title('Top Rated Anime')
plt.xlabel('Average Rating')
plt.ylabel('Anime Title')
plt.show()
client.close()
```

Polars : 
```python
grouped_df = pol_df.groupby('Anime Title').agg(pl.col('rating').mean().alias('average_rating'))
top_rated_anime = grouped_df.sort('average_rating', descending=True).head(10)
print('Top 10 Rated Anime Titles:')
print(top_rated_anime)
```

* Number of Ratings per Anime vs. Average Anime Rating
  
Pandas :
```python
plt.figure(figsize=(12, 8))
sns.scatterplot(x='num_ratings_anime', y='avg_anime_rating', data=df)
plt.title('Number of Ratings per Anime vs. Average Anime Rating')
plt.xlabel('Number of Ratings per Anime')
plt.ylabel('Average Anime Rating')
plt.show()
```

Dask : 
```python
client = Client()
agg_data = df.groupby('anime_id')['rating'].agg(['mean', 'count'])
agg_data.columns = ['Average Rating', 'Number of Ratings']
plt.figure(figsize=(10, 6))
plt.scatter(agg_data['Number of Ratings'], agg_data['Average Rating'], alpha=0.5)
plt.title('Correlation between Number of Ratings and Average Rating')
plt.xlabel('Number of Ratings')
plt.ylabel('Average Rating')
plt.grid(True)
plt.show()
client.close()
```

Polars : 
```python
plt.figure(figsize=(12, 8))
sns.scatterplot(x='num_rating_anime', y='average_anime_rating', data=pan_df)
plt.title('Number of Ratings per Anime vs. Average Anime Rating')
plt.xlabel('Number of Ratings per Anime')
plt.ylabel('Average Anime Rating')
plt.show()
```

    
## Asking and Answering Questions

* What are the top-rated anime titles?
   
Pandas :
```python
top_anime = df.groupby('Anime Title')['rating'].mean().sort_values(ascending=False).head(10)
print(top_anime)
```

Dask : 
```python
client = Client()
agg_data = df.groupby('anime_id')['rating'].agg(['mean', 'count'])
agg_data.columns = ['Average Rating', 'Number of Ratings']
plt.figure(figsize=(10, 6))
plt.scatter(agg_data['Number of Ratings'], agg_data['Average Rating'], alpha=0.5)
plt.title('Correlation between Number of Ratings and Average Rating')
plt.xlabel('Number of Ratings')
plt.ylabel('Average Rating')
plt.grid(True)
plt.show()
client.close()
```

Polars : 
```python
top_anime = pol_df.groupby('Anime Title').agg(pl.col('rating').mean().alias('average_
print(top_anime)
```

* How many unique users and anime titles are in the dataset?

Pandas :
```python
unique_users = df['user_id'].nunique()
unique_anime_titles = df['Anime Title'].nunique()

print(f"Unique Users: {unique_users}")
print(f"Unique Anime Titles: {unique_anime_titles}")
```

Dask : 
```python
client = Client()
unique_users = df["user_id"].nunique()
unique_animes = df["anime_id"].nunique()

table = PrettyTable()
table.field_names = ["Category", "Count"]

table.add_row(["Unique Users", unique_users])
table.add_row(["Unique Animes", unique_animes])

print(table)
client.close()
```

Polars : 
```python
unique_users = pol_df['user_id'].n_unique()
unique_anime_titles = pol_df['Anime Title'].n_unique()

print(f"Unique Users: {unique_users}")
print(f"Unique Anime Titles: {unique_anime_titles}")
```

* What is the distribution of ratings given by users?
  
Pandas :
```python
import matplotlib.pyplot as plt

plt.hist(df['rating'], bins=5, edgecolor='black')
plt.title('Distribution of Ratings')
plt.xlabel('Rating')
plt.ylabel('Frequency')
plt.show()
```

Dask : 
```python
client = Client()

plt.figure(figsize=(10, 6))
sns.histplot(df['rating'], bins=5)
plt.title(f'Distribution of Rating')
plt.xlabel('rating')
plt.ylabel('Frequency')
plt.show()

client.close()
```

Polars : 
```python
plt.hist(pan_df['rating'], bins=5, edgecolor='black')
plt.title('Distribution of Ratings')
plt.xlabel('Rating')
plt.ylabel('Frequency')
plt.show()
```

* Who are the top users with the most rated anime?
  
Pandas :
```python
top_users = df['user_id'].value_counts().head(10)
print(top_users)
```

Dask : 
```python
client = Client()

top_10_users = df['Username'].value_counts().head(10)
plt.figure(figsize=(10, 6))
sns.barplot(x=top_10_users.index, y=top_10_users.values, palette='viridis')
plt.title('Top 10 Users with the Most Ratings')
plt.xlabel('Username')
plt.ylabel('Number of Ratings')
plt.xticks(rotation=45, ha='right')
plt.show()

client.close()
```

Polars : 
```python
top_users = pol_df['user_id'].value_counts().head(10)
print(top_users)
```


## Comparative Analysis

## Inference and Conclusion
Pandas:
Pandas remains a go-to library for data manipulation and analysis in scenarios where datasets comfortably fit within memory limits. Its ease of use, rich functionalities, and widespread adoption make it ideal for smaller to moderately sized datasets, enabling seamless exploratory data analysis, cleaning, and manipulation.

Dask:
Dask's strength lies in its ability to handle datasets larger than available memory by leveraging parallel and distributed computing. It excels in scalability and performance, allowing operations on larger-than-memory datasets efficiently. Dask is particularly beneficial for scalable data processing and machine learning tasks.

Polars:
Polars, optimized for performance and memory efficiency, presents an alternative to Pandas with faster execution, especially for large-scale data processing. Its columnar data processing and Rust-based architecture offer advantages in speed and memory usage. Polars suits scenarios demanding high-speed computation and memory efficiency, potentially outperforming Pandas in specific use cases with substantial datasets.

Overall Summary:
Scalability: Dask and Polars outperform Pandas when handling larger-than-memory datasets due to their distributed computing or memory-efficient designs.
Performance: While Pandas is robust for smaller datasets, Dask and Polars provide enhanced performance and efficiency for big data scenarios.
Usability: Pandas maintains its user-friendly interface, making it accessible for beginners and suitable for smaller tasks. Dask and Polars require familiarity with distributed computing or columnar processing paradigms but offer substantial performance benefits for large-scale operations.
Choosing among these libraries hinges on the specific use case, dataset size, and the balance between ease of use and performance requirements. Each tool has its strengths, and understanding their nuances aids in selecting the most suitable one for a given data analysis or manipulation task in the context of dataset size and available computational resources.


## Reference



