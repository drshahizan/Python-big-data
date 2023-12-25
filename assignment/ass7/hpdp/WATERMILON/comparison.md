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

2. Expenses for Tiny Datasets:

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

### 3.3. Vaex

<a target="_blank" href="https://colab.research.google.com/github/drshahizan/Python-big-data/blob/main/assignment/ass7/hpdp/WATERMILON/vaex.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

## 4. Comparative Analysis of Libraries <a name = "comp_analysis"></a>


## 5. Conclusion <a name = "conclusion"></a>


## Contribution 🛠️  <a name = "contribution"> </a>
Please create an [Issue](https://github.com/drshahizan/HPDP/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)
