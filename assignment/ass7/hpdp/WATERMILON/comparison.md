<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

![image](https://github.com/drshahizan/Python-big-data/assets/95710157/e715e561-bb25-4f7f-ae3c-9638b989008d)



# Assignment 7: Comparative Analysis of Data Analysis Libraries

## Group Information
**Group Name**: WATERMILON

**Group Members:**

| Name                | Matrix Number | Task   |
| ------------------- | ------------- | ------ |
| NG ZI XING          | A21EC0213     | Modin  |
| LOO ZHI YUAN        | A21EC0197     | Vaex   |
| YEW RUI XIANG       | A21EC0149     | Dask   |
| SAM CHIA YUN        | A21EC0127     | Vaex   |

### Table of Contents
+ [1. Introduction](#intro)
+ [2. Dataset Selection](#dataset_selection)
+ [3. Data Acquisition](#data_acquisition)
  + [3.1. Import Dataset](#import_data)
+ [4. Setting Up the Environment](#setup_environment)
  + [4.1. Install Necessary Tools & Libraries](#install_lib) 
+ [5. Data Preprocessing](#dataset_preprocessing)
  + [5.1. Data Exploration](#data_explore)
  + [5.2. Data Cleaning and Handling](#data_clean)
    + [5.2.1. Handle Missing Values](#missing_value)
    + [5.2.2. Handle Duplicated](#handle_dup)
    + [5.2.3. Handle Datatypes](#handle_dt)
    + [5.2.4. Column 'price'](#price)
+ [6. Exploratory Data Analysis](#eda)
  + [6.1. Summary Statistics](#sum_stat)
  + [6.2. Data Visualization](#data_visual)
  + [6.3. Data Exploration](#data_explore_eda)
  + [6.4. Feature Engineering](#fe)
+ [7. Conclusion](#conclusion)
+ [Contributions](#contribution)

## 1. Introduction <a name = "intro"></a>


## 2. Dataset Selection <a name = "dataset_selection"></a>

### 2.1. About the Dataset

This dataset offers a comprehensive overview of property sales in England and Wales, drawing data from the HM Land Registry, a key source endorsed by the UK government. It serves as a valuable resource for analysts, researchers, and businesses, providing in-depth insights into property transactions, sale prices, and property characteristics. The records span from January 1995 to the latest monthly data, encompassing various transaction types, including residential and commercial properties.

#### Key Features/Columns:

| Attribute                             | Description                                                     |
|-----------------------------------|-----------------------------------------------------------------|
| **Postcode**                      | The postal code denoting the property's location.               |
| **PAON (Primary Addressable Object Name)** | Typically the house number or name.                    |
| **SAON (Secondary Addressable Object Name)** | Additional information if the building is divided into flats or sub-buildings. |
| **Street**                        | The street name where the property is situated.                 |
| **Locality**                      | Supplementary locality information.                            |
| **Town/City**                     | The town or city where the property is positioned.             |
| **District**                      | The district in which the property is situated.                |
| **County**                        | The county where the property is located.                      |
| **Price Paid**                    | The amount for which the property was sold.                    |

#### Usefulness:

Analysts and businesses can leverage this dataset to discern market trends, assess property valuations, and identify investment opportunities within the dynamic real estate sector of England and Wales.

#### Dataset Link:

[UK Property Price Data (1995-2023)](https://www.kaggle.com/datasets/willianoliveiragibin/uk-property-price-data-1995-2023-04)

## 3. About the Libraries Chosen <a name = "about_lib"></a>

For assignment 7 that regarding "Comparative Analysis of Data Analysis Libraries", our group have choose three libraries which are Modin, Dask and Vaex.

### 3.1. Modin

<a target="_blank" href="https://colab.research.google.com/github/drshahizan/Python-big-data/blob/main/assignment/ass7/hpdp/WATERMILON/modin.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

Modin serves as a seamless upgrade library for Pandas which is one of the most popular data manipulation library in Python. While Pandas operates in a single-threaded fashion, Modin introduces a significant speed boost by effortlessly scaling across all available cores. This is especially advantageous for handling bigger datasets from from 1MB to 1TB+, while Pandas might encounter performance bottlenecks or memory usage limitations which lead to problems like system crashing.

#### Getting Started:

To install Modin using pip, run the following code segment in the Google Colab:

```ruby
!pip install -U modin[all]
```

To use the Modin in Google Colab, replace the importing of Pandas with Modin through the code segment below:

```ruby
import pandas
import modin.pandas as pd
```

#### Strengths: 

1. Distributed and Parallel Computing:

Modin effectively uses all of the CPU cores that are available to it, excelling in distributed and parallel computing. This is especially helpful for accelerating tasks related to data analysis on big datasets.

2. API Compatibility for Pandas:

Modin's compatibility with the Pandas API is built in. Because of this, switching from Pandas to Modin is often simple and requires little modification to the code.

3. Effective Pandas Functions:

Modin significantly improves performance for tasks like filtering, grouping, and joining by parallelizing common Pandas operations.

4. Beyond-Core Processing:

Modin allows for out-of-core computation, which makes it possible to analyze datasets bigger than what the system memory can hold. It can handle large datasets because of its versatility and efficient chunk processing of data.

5. Adaptable Backend:

Users can customize Modin to meet their unique needs thanks to the freedom to select from a variety of backends. Scalability is provided by the default Dask backend, which supports distributed and parallel computing.

#### Weaknesses:

1. Learning Curve:

Although Modin is compatible with Pandas, new users may encounter a learning curve, particularly if they are unfamiliar with distributed computing concepts.

2. Overhead for Small Datasets:

Modin's advantages are greatest when applied to sizable datasets. The overhead of parallelization may not yield as noticeable performance gains as using Pandas directly for smaller datasets that fit comfortably in memory.

3. Limited Choices for Backend:

Modin offers a greater range of backends than some other distributed computing libraries, but it still allows for flexibility in backend selection. For some users, this might mean fewer options for customization.

4. Reliances:

Modin's default backend is dependent on other programs, like Dask. Handling these dependencies can be complicated, particularly in settings where access to external packages is restricted or version control is enforced.

#### References:
1. [Modin in Github](https://github.com/modin-project/modin)
2. [Documentation of Modin](https://modin.readthedocs.io/en/stable/)

### 3.2. Dask

<a target="_blank" href="https://colab.research.google.com/github/drshahizan/Python-big-data/blob/main/assignment/ass7/hpdp/WATERMILON/dask.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

As the Python library for parallel and distributed computing, Dask can help users to handle datasets that are larger than memory by utilizing the capabilities of distributed and parallel computing. It is especially useful for tasks involving data analysis and manipulation, and it offers a more sophisticated option than single-node tools such as Pandas.

#### Getting Started:

To install Dask using pip, run the following code segment in the Google Colab:

```ruby
!pip install "dask[complete]"
```

To use the Dask in Google Colab, run the code segment below in Google Colab to import the Dask DataFrame:

```ruby
import dask.dataframe as dd
```

#### Strengths: 

1. Distributed and Parallel Computing:

Users can scale their computations across multiple cores or even cluster environments with Dask's proficiency in parallel and distributed computing. This is especially useful for managing large amounts of data that are too large for a single machine to handle.

2. Pandas-Like API:

For users who are already familiar with working with Pandas, Dask offers an API that is similar to Pandas. This reduces the difficulty of acclimating to distributed computing.

3. Lazy Evaluation:

Dask builds a task graph for the whole computation before executing it because it uses lazy evaluation. This makes it possible to schedule tasks more effectively and carry them out quickly, especially when working with complicated operations on big datasets.

4. Out-of-Core Processing:

Dask works flawlessly with datasets that are no longer in use. By cleverly managing data in smaller chunks, it enables processing of data larger than the available RAM, much like Pandas does in-memory.

5. Scalability:

Dask can grow from a single machine to a cluster of machines thanks to its scalable design. Because of its scalability, it can be used for a wide range of data analysis tasks, from small datasets to large distributed environments.

#### Weaknesses:

1. Learning Curve:

There might be a learning curve when switching from Pandas to Dask, particularly for users who are unfamiliar with distributed computing ideas. It takes some learning to figure out how to use Dask for a given set of use cases.

2. Limited Functionality:

Dask does not implement the entire Pandas API, despite covering a large portion of Pandas functionality. Users may need to modify their code to accommodate for the possibility that some advanced Pandas features or particular operations won't be directly supported.

3. Overhead Usage for Small Dataset:

Dask's distributed and parallel architecture comes with an inherent overhead. This overhead may outweigh the advantages for smaller datasets that fit in memory, in which case simpler tools like Pandas might be more appropriate.

4. Debugging Complexity:

Compared to debugging single-node computations, debugging Dask computations can be more complex, particularly in a distributed setting. Issue detection and resolution in a distributed environment may call for extra knowledge.

#### References:
1. [Dask in Github](https://github.com/dask/dask)
2. [Documentation of Dask](https://docs.dask.org/en/stable/)

### 3.3. Vaex

<a target="_blank" href="https://colab.research.google.com/github/drshahizan/Python-big-data/blob/main/assignment/ass7/hpdp/WATERMILON/vaex.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

Vaex is a high-performance Python library that allows large tabular datasets to be explored and visualized using lazy Out-of-Core DataFrames (like Pandas). It performs over a billion (10^9) samples/row calculations per second on an N-dimensional grid, calculating statistics like mean, sum, count, standard deviation, etc. Histograms, density plots, and three-dimensional volume rendering are used in visualization to enable interactive big data exploration. For optimal performance (zero memory waste), Vaex employs memory mapping, zero memory copy policy, and lazy computations.

#### Getting Started:

To install Vaex using pip, run the following code segment in the Google Colab:

```ruby
!pip install vaex
```

To use the Vaex in Google Colab, run the code segment below in Google Colab to import the Vaex:

```ruby
import vaex
```

#### Strengths: 

1. High Performance:

Vaex excels in processing huge tabular data, boasting the capability to handle over 10^9 rows per second. This makes it a powerful choice for working with massive datasets efficiently.

2. Lazy / Virtual Columns:

Vaex supports lazy or virtual columns, enabling on-the-fly computations without unnecessary RAM usage. This contributes to efficient memory utilization and allows for dynamic data manipulation.

3. Memory Efficiency:

Vaex is designed to be memory-efficient, particularly during operations like filtering, selections, and subsets. It avoids unnecessary memory copies, making it suitable for working with large datasets that may not fit entirely into memory.

4. Visualization Integration:

Vaex directly supports visualization, often requiring just a one-liner for creating plots. This built-in visualization capability simplifies the process of exploring and understanding the data.

5. User-Friendly API:

Vaex provides a user-friendly API, focusing on a DataFrame object. The API is designed to be intuitive, and features such as tab completion and docstrings make it easy for users to navigate and interact with the data.

6. Modular and Lean Structure:

Vaex is organized into multiple packages, each serving a specific purpose. This modular structure includes core algorithms (vaex-core), memory-mapped arrays (vaex-hdf5), visualization (vaex-viz), and more. Users can choose and install only the components they need.

7. Wide Range of Additional Packages:

Vaex offers a diverse set of additional packages, enhancing its functionality and catering to specific use cases. These include packages for arrow support, astronomy-related transformations, server access, machine learning (vaex-ml), and more.

8. Jupyter Integration:

Vaex seamlessly integrates with Jupyter notebooks and Jupyter Lab through vaex-jupyter. This integration provides interactive visualization and selection capabilities directly within the Jupyter environment.

9. Cross-Language Data Sharing:

Vaex supports Arrow, facilitating cross-language data sharing. This feature enhances interoperability, allowing data to be easily exchanged between different programming languages.

10. Lean Meta Package:

The vaex meta package simplifies the installation process by bundling all necessary packages. Users can install vaex, which includes the core functionality as well as optional components, making it convenient to set up Vaex according to their needs.

11. Qt GUI Support:

Vaex provides a Qt-based graphical user interface (GUI) through vaex-qt, offering an alternative way to interact with and explore data.

#### Weaknesses:

1. Limited Functionality:

Although strong, Vaex might not be able to cover all of Pandas' or other comprehensive data analysis libraries' functionality. It's possible that some sophisticated features found in Pandas aren't directly accessible in Vaex.

2. Learning Curve:

There may be a learning curve when switching from more popular data analysis libraries like Pandas to Vaex. To fully utilize Vaex, users must be aware of the unique features and optimizations that it offers.

3. Ecosystem and Community:

Compared to more well-known libraries like Pandas or Dask, Vaex may have a smaller community as of my most recent knowledge update in January 2022. The accessibility of third-party extensions and community support may be impacted by this.

4. Less Flexibility in Operations:

Vaex is effective for a wide range of numerical operations, but it may not be as flexible or performant for some operations that Pandas supports well. Users should carefully consider the requirements of their particular use case.

#### References:
1. [Vaex in Github](https://github.com/vaexio/vaex)
2. [Documentation of Vaex](https://vaex.readthedocs.io/en/latest/)

## 4. Comparative Analysis of Libraries <a name = "comp_analysis"></a>

### 4.1. Data Preparation and Cleaning

#### 4.1.1. Dataset Loading

1. **Modin:**
   
    ```ruby
    colnames=['Transaction_unique_identifier', 'price', 'Date_of_Transfer', 'postcode', 'Property_Type',
          'Old/New', 'Duration', 'PAON', 'SAON', 'Street', 'Locality', 'Town/City', 'District', 'County', 'PPDCategory_Type','Record_Status - monthly_file_only']

    data = pd.read_csv("/content/202304.csv", header = None, names = colnames, parse_dates = ["Date_of_Transfer"])
    ```

    Time Consumed: 3 minutes 35 seconds

2. **Dask:**
   
   ```ruby
    colnames=['Transaction_unique_identifier', 'price', 'Date_of_Transfer', 'postcode', 'Property_Type',
          'Old/New', 'Duration', 'PAON', 'SAON', 'Street', 'Locality', 'Town/City', 'District', 'County', 'PPDCategory_Type','Record_Status - monthly_file_only']
    dtypes = {'PAON': 'object', 'SAON': 'object', 'postcode': 'str', 'Property_Type': 'str', 'Duration': 'str', 'PAON': 'str', 'Street': 'str', 'Town/City': 'str',
          'District': 'str', 'County': 'str', 'Old/New': 'str', 'PPDCategory_Type': 'str'}

    data = dd.read_csv("/content/202304.csv", dtype={'PAON': 'object', 'SAON': 'object', }, header = None, names = colnames, parse_dates = ["Date_of_Transfer"])
    ```

   Time Consumed: 50.5 milliseconds
   
3. **Vaex:**

   ```ruby
    colnames=['Transaction_unique_identifier', 'price', 'Date_of_Transfer', 'postcode', 'Property_Type',
          'Old/New', 'Duration', 'PAON', 'SAON', 'Street', 'Locality', 'Town/City', 'District', 'County', 'PPDCategory_Type','Record_Status - monthly_file_only']

    df = vaex.from_csv('/content/202304.csv', convert=True, header = None, chunk_size=1_000_000 )
    df = vaex.open("/content/*.hdf5")

    for i, c in enumerate(colnames):
      df.rename(str(i),c)
    ```

   Time Consumed: 3 minutes 55 seconds

#### 4.1.2. Observe the Information of Dataframe

1. **Modin:**

   ```ruby
    data.info()
    ```

   Time Consumed: 1 minutes 57 seconds

2. **Dask:**

   ```ruby
    data.info()
    ```

   Time Consumed: 4.36 milliseconds
   
3. **Vaex:**

   ```ruby
    df.info()
    ```

   Time Consumed: 17.5 milliseconds
   

#### 4.1.3. Removes the Specified Row/Column ("Transaction_unique_identifier" & "Record_Status - monthly_file_only")

1. **Modin:**

   ```ruby
    data.drop(["Transaction_unique_identifier", "Record_Status - monthly_file_only"], axis = 1, inplace = True)
    ```

   Time Consumed: 31.5 milliseconds

2. **Dask:**

   ```ruby
    data = data.drop(["Transaction_unique_identifier", "Record_Status - monthly_file_only"], axis = 1)
    ```

   Time Consumed: 11.6 milliseconds
   
3. **Vaex:**

   ```ruby
    columns_to_drop = ["Transaction_unique_identifier", "Record_Status - monthly_file_only"]
    df = df.drop(columns_to_drop)
    ```

   Time Consumed: 1.09 milliseconds

#### 4.1.4. Calculate the Percentage of Missing Values

1. **Modin:**

   ```ruby
    data.isna().sum() / data.shape[0]
    ```

   Time Consumed: 1.51 seconds

2. **Dask:**

   ```ruby
    data.isna().sum().compute() / data.shape[0].compute()
    ```

   Time Consumed: 6 minutes 23 seconds
   
3. **Vaex:**

   ```ruby
    for column in df.column_names:
      missing_fraction = df[column].isna().mean(progress='widget')
      print(f"Column '{column}': {missing_fraction}")
    ```

   Time Consumed: 2.6 seconds

#### 4.1.5. Removes the Specified Row/Column ("SAON" & "Locality")

1. **Modin:**

   ```ruby
    data.drop(["SAON", "Locality"], axis = 1, inplace = True)
    ```

   Time Consumed: 6.47 milliseconds

2. **Dask:**

   ```ruby
    data = data.drop(["SAON", "Locality"], axis = 1)
    ```

   Time Consumed: 7.41 milliseconds
   
3. **Vaex:**

   ```ruby
    columns_to_drop = ["SAON", "Locality"]
    df = df.drop(columns_to_drop)
    ```

   Time Consumed: 2.32 milliseconds
   

#### 4.1.6. Replace the Missing Values

1. **Modin:**

   ```ruby
    data.fillna({"postcode" : "UNK", "PAON" : 0, "Street" : "UNK"}, inplace = True)
    ```

   Time Consumed: 229 milliseconds

2. **Dask:**

   ```ruby
    data = data.fillna({"postcode" : "UNK", "PAON" : 0, "Street" : "UNK"})
    ```

   Time Consumed: 12.2 milliseconds
   
3. **Vaex:**

   ```ruby
    df.fillna(value="UNK", column_names=["postcode"], inplace=True)
    df.fillna(value="0", column_names=["PAON"], inplace=True)
    df.fillna(value="UNK", column_names=["Street"], inplace=True)
    ```

   Time Consumed: 6.29 milliseconds

#### 4.1.7. Review the Cleaning Results

1. **Modin:**

   ```ruby
    data.isna().sum() / data.shape[0]
    ```

   Time Consumed: 3 minutes 1 seconds

2. **Dask:**

   ```ruby
    data.isna().sum().compute() / data.shape[0].compute()
    ```

   Time Consumed: 7 minutes 13 seconds
   
3. **Vaex:**

   ```ruby
    for column in df.column_names:
      missing_fraction = df[column].isna().mean(progress='widget')
      print(f"Column '{column}': {missing_fraction}")
    ```

   Time Consumed: 2.51 seconds

#### 4.1.8. Convert All Object Columns to String Type

1. **Modin:**

   ```ruby
    colnames = ["postcode", "Property_Type", "Duration", "PAON", "Street", "Town/City", "District", "County", "Old/New", "PPDCategory_Type"]

    data[colnames] = data.astype( { col : str for col in colnames} )[colnames]
    ```

   Time Consumed: 3 minutes 19 seconds

2. **Dask:**

   Not required for our analysis.

   Time Consumed: -
   
3. **Vaex:**

   Not required for our analysis.

   Time Consumed: -


### 4.2. Exploratory Analysis and Visualization

#### 4.2.1. Data Observation

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.2.2. Coefficient of Skewness for the Property Prices

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.2.3. Exploring Property Prices specifically in Greater London

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.2.4. Explore How Number of Classes Influence Property Prices by using Bar Chart

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.2.5. Understand the Heights of Prices

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

### 4.3. Asking and Answering Questions

#### 4.3.1. To what degree is the price distribution skewed?

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.3.2. Does the country where the property is located significantly influence its price?

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.3.3. How does the district affect the price and its dispersion in property?

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.3.4. How does the combination of PPDCategory_Type and Old/New property status influence property prices?

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.3.5. What is the trend in property prices over time?

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**

#### 4.3.6. How does the price of property vary based on different property types over time?

1. **Modin:**

2. **Dask:**
   
3. **Vaex:**


## 5. Conclusion <a name = "conclusion"></a>


## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
