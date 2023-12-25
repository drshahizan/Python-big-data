<a href="https://github.com/drshahizan/HPDP/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/HPDP" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/network/members"><img src="https://img.shields.io/github/forks/drshahizan/HPDP" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/HPDP" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/HPDP"><img src="https://img.shields.io/github/issues/drshahizan/HPDP" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/HPDP/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/HPDP?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FHPDP&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

# Assignment 7: Comparison between libraries

### Group Name : KOKONAT

### Group Members

| Name                                     | Matrix Number | Task |
| :---------------------------------------- | :-------------: | ------------- |
|NG SUANG JOO        | A21EC0102     | Pandas  |
|LING WAN YIN         | A21EC0047     | Datatable  |
|FONG KHAH KHEH         | A21EC0026   | Pyspark   |

### Table of Contents
+ [1. Introduction](#intro)
+ [2. Dataset Selection](#dataset_selection)
+ [3. Data Acquisition](#data_acquisition)
+ [4. Data Preparation and Cleaning](#data_prep)
  + [4.1. Install necessary library](#library)
  + [4.2. Load the dataset](#data_loading)
  + [4.3. Display first five rows](#rows)
  + [4.4. Explore the number of rows & columns](#num_rows)
  + [4.5 Handling Missing Value](#missing_value)
  + [4.6. Column type](#column_type)
  + [4.7. Number of unique values per columns](#unique)
+ [5. Exploratory Data Analysis](#eda)
  + [5.1. Summary Statistics](#sum_stat)
  + [5.2. Data Visualization](#data_visual)
    + [5.2.1 Total Volume Produced by Beer Style](#total_volume)
    + [5.2.2 Average Fermentation Time by Beer Style](#avg)
    + [5.2.3 Fermentation Time by Beer Style](#fermentation_time)
    + [5.2.4 Correlation between the Fermentation_Time, Temperature, pH_Level, Gravity, and Quality_Score](#corr)
    + [5.2.5 Total Sales by Beer Style](#sales)
    + [5.2.6 Total Loss by Beer Style](#loss)
+ [6. Asking and Answering Questions](#qna)
  + [6.1 Which beer style has the highest average quality score?](#q1)
  + [6.2 What is the total volume produced for each location?](#q2)
  + [6.3 What is the relation between fermentation time and alcohol content?](#q3)
  + [6.4 Which ingredient ratio is associated with the highest total sales?](#q4)
  + [6.5 What is the average loss during brewing, fermentation, and bottling/kegging for each beer style?](#q5)
+ [7. Inferences and Conclusion](#conclusion)
+ [8. References and Future Work](#future)
+ [9. Contributions](#contribution)

## 1. Introduction <a name = "intro"></a>
In the field of big data, there are unique challenges associated with efficiently processing enormous datasets for analysis. Three strong libraries are compared and contrasted in this assignment: **Pandas**, **Datatable**, and **PySpark**. When tackling the difficulties of large-scale Python data processing, each of these libraries approaches the problem in a different way.

A data science mainstay, **Pandas** is well known for being user-friendly and versatile, especially when working with datasets of a moderate size. Its DataFrame and Series structures offer a user-friendly interface for analyzing and manipulating data.

Large dataset handling is a notable feature of **Datatable**, a scalability and performance package. To bridge the gap between the simplicity of Pandas and the scalability of distributed computing frameworks, Datatable has a syntax similar to that of Pandas.

Built on top of Apache Spark, **PySpark** is a powerful tool for distributed data processing. It is a top option for big data analytics because of its superiority in managing enormous datasets across clusters. The fault tolerance and resilience of PySpark provide dependability in large-scale computations.

This assignment will compare and contrast **Pandas**, **Datatable**, and **PySpark**, taking into account scalability, syntax, and performance. Let's go out on this comparative and exploratory voyage!

## 2. Dataset Selection <a name = "dataset_selection"></a>
The selected dataset pertains to a comprehensive examination of brewing factors, market sales trends, and quality measures in the manufacturing of craft beer from 2020 to 2024. This large dataset comes from a craft beer company and includes a comprehensive collection of data from January 2020 to January 2024. With a wide range of brewing factors, sales information, and quality evaluations, it offers a comprehensive understanding of the brewing processes and their effects on the market. This dataset contains 20 columns of attributes and is approximately **2 GB** in size.

**Attribute details:**
| Attribute                                     | Description |
| :---------------------------------------- | :-------------: | 
|Batch_ID       | A unique identifier assigned to each batch of beer produced.    | 
|Brew_Date         | The date on which the beer batch was brewed.    | 
|Beer_Style        | The style or type of beer, such as IPA, Stout, Lager, Ale, etc.   | 
|SKU|The packaging type in which the beer is sold, like Kegs, Bottles, Cans, or Pints.|
|Location|The packaging type in which the beer is sold, like Kegs, Bottles, Cans, or Pints|
|Fermentation_Time|The duration of the fermentation process, measured in days.|
|Temperature|The average temperature (in Celsius) maintained during the brewing process|
|pH_Level|The pH level of the beer, indicating its acidity or alkalinity.|
|Gravity|A measure of the density of the beer as compared to water, indicating the potential alcohol content.|
|Alcohol_Content|The percentage of alcohol by volume in the beer.|
|Bitterness|The bitterness of the beer, measured in International Bitterness Units (IBU).|
|Color|The color of the beer measured using the Standard Reference Method (SRM).|
|Ingredient_Ratio|The ratio of different ingredients used in the beer, such as malt, hops, etc.|
|Volume_Produced|The volume of beer produced in the batch, measured in liters.|
|Total_Sales|The total sales generated from the batch, expressed in a currency unit.|
|Quality_Score|An overall quality score assigned to the beer batch, rated out of 10.|
|Brewhouse_Efficiency|The efficiency of the brewing process, expressed as a percentage.|
|Loss_During_Brewing|The percentage of volume loss during the brewing process.
|Loss_During_Fermentation|The percentage of volume loss during the fermentation process.
|Loss_During_Bottling_Kegging|The percentage of volume loss during the bottling or kegging process.|


**Dataset URL:**
[Brewery Operations and Market Analysis Dataset](https://www.kaggle.com/datasets/ankurnapa/brewery-operations-and-market-analysis-dataset)

## 3. Data Acquisition <a name = "data_acquisition"></a>
The Brewery Operations and Market Analysis dataset is sourced from Kaggle where we can utilised the Kaggle API to download the dataset.

1. Import the necessary library for file upload.
   ![image](https://github.com/drshahizan/Python-big-data/assets/146581747/f7428bb9-4a80-4708-b9c1-6f964b17351c)

2. Upload the Kaggle API token file ('kaggle.json') using the file upload widget. The file 'kaggle.json' can be found under your account settings in Kaggle.
   ![image](https://github.com/drshahizan/Python-big-data/assets/146581747/7aad9085-a6b3-4cd3-b40a-3aa3341cfa5d)

3. Utilise the Kaggle API Token to extract the dataset.
   ![image](https://github.com/drshahizan/Python-big-data/assets/146581747/d143c3cc-9a0a-4245-bc56-18119f048ba2)

4. The dataset has been downloaded, extracted and is ready for further process.

## 4. Data Preparation and Cleaning <a name = "data_prep"></a>

### 4.1 Install necessary library <a name = "library"></a>
Library 1: **Pandas**

Library 2: **Datatable**

- Installing the Datatable package:
```ruby
!pip install datatable
```
- Importing the Datatable library:
```ruby
import datatable as dt
```
Library 3: **PySpark**
- Installing the Pyspark package:
```ruby
!pip install pyspark
```
- Importing the Pyspark library
```ruby
from pyspark.sql import SparkSession
from pyspark.sql.functions import col
import pyspark.sql.functions as F
from pyspark.sql.types import StringType, DoubleType
```
### 4.2 Load the dataset <a name = "data_loading"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
def load_data():
    # Load the data
    brewery_df = spark.read.csv("brewery_data_complete_extended.csv", header=True, inferSchema=True)
    return brewery_df
# Load the data
brewery_df = load_data()
```
Memory usage: 100.83203125 MB

Computation Time: 118.19355058 seconds

### 4.3 Display first five rows <a name = "rows"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
brewery_df.show(5, truncate=False)
```
Memory usage: 115.92578125 MB

Computation Time: 0.9608330726623535 seconds

### 4.4 Explore the number of rows & columns <a name = "num_rows"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
num_rows = brewery_df.count()
num_columns = len(brewery_df.columns)
print(f"Number of Rows: {num_rows}")
print(f"Number of Columns: {num_columns}")
```
Memory usage: 115.92578125 MB

Computation Time: 5.4734203815460205 seconds

### 4.5 Handling Missing Value <a name = "missing_value"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
missing_values = brewery_df.select([F.count(F.when(F.col(c).isNull(), c)).alias(c) for c in brewery_df.columns])
missing_values.show()
```
Memory usage: 115.92578125 MB

Computation Time: 45.46979260444641 seconds

### 4.6 Column type <a name = "column_type"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
# Get column types
column_types = brewery_df.dtypes

# Print column types
print("Column Types:")
for col_name, col_type in column_types:
    print(f"{col_name}: {col_type}")
```
Memory usage: 100.83203125 MB

Computation Time: 0.01815199851989746 seconds

### 4.7 Number of unique values per columns <a name = "unique"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

## 5. Exploratory Data Analysis  <a name = "eda"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

### 5.1  Summary Statistics  <a name = "sum_stat"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
brewery_df.describe().show()
```
Memory usage: 201.609375 MB

Computation Time: 196.83882665634155 seconds

### 5.2  Data Visualization  <a name = "data_visual"></a>

#### 5.2.1  Total Volume Produced by Beer Style  <a name = "total_volume"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
# Group by beer style and calculate the total volume produced
total_volume_by_style = brewery_df.groupBy("Beer_Style").agg(sum("Volume_Produced").alias("Total_Volume_Produced"))

# Show the result
total_volume_by_style.show()
```
Memory usage: 201.609375 MB

Computation Time: 15.084449291229248 seconds

#### 5.2.2  Average Fermentation Time by Beer Stylee  <a name = "avg"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
average_fermentation_time_by_style = (
    brewery_df.groupBy("Beer_Style")
    .agg(avg("Fermentation_Time").alias("Average_Fermentation_Time"))
)

# Show the result
average_fermentation_time_by_style.show()
```
Memory usage: 201.828125 MB

Computation Time: 15.111161470413208 seconds

#### 5.2.3  Fermentation Time by Beer Style  <a name = "fermentation_time"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

#### 5.2.4 Correlation between the Fermentation_Time, Temperature, pH_Level, Gravity, and Quality_Score <a name = "corr"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
# Create a vector assembler
vector_assembler = VectorAssembler(inputCols=selected_columns, outputCol="features")

# Transform the DataFrame to include the feature vector
assembled_df = vector_assembler.transform(brewery_df)

# Calculate the correlation matrix
correlation_matrix = Correlation.corr(assembled_df, "features").head()

# Show the correlation matrix
print("Correlation Matrix:")
print(correlation_matrix[0])

# Extract the correlation matrix values
corr_values = correlation_matrix[0].toArray()

# Create a DataFrame for the correlation matrix
corr_matrix_df = pd.DataFrame(corr_values, columns=selected_columns, index=selected_columns)

# Create a heatmap
plt.figure(figsize=(10, 8))
sns.heatmap(corr_matrix_df, annot=True, cmap="coolwarm", fmt=".2f", linewidths=.5)
plt.title('Correlation Heatmap')
plt.show()
```
Memory usage: 216.1015625 MB

Computation Time: 78.82638359069824 seconds

#### 5.2.4  Total Sales by Beer Style <a name = "sales"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
# Create a Spark session
spark = SparkSession.builder.appName("BeerAnalysis").getOrCreate()

# Check the exact column names in your dataset
brewery_df.show()

# Assuming the correct column name is "Total_Sales"
selected_columns = ["Beer_Style", "Total_Sales"]

# Group by beer style and calculate the total sales
total_sales_by_style = brewery_df.groupBy("Beer_Style").agg(sum(col("Total_Sales")).alias("Total_Sales"))


# Convert the PySpark DataFrame to Pandas for visualization
total_sales_pd = total_sales_by_style.toPandas()

# Sort the DataFrame
total_sales_pd = total_sales_pd.sort_values(by='Total_Sales', ascending=True)

# Create a line plot
plt.figure(figsize=(12, 6))
line2 = sns.lineplot(x='Beer_Style', y='Total_Sales', data=total_sales_pd, marker='o', color='blue')
plt.xlabel('Beer Style')
plt.ylabel('Total Sales')
plt.title('Total Sales by Beer Style')
plt.xticks(rotation=0)
plt.show()

```
Memory usage: 228.1796875 MB

Computation Time: 20.969558000564575 seconds

#### 5.2.5  Total Loss by Beer Style <a name = "loss"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

## 6. Asking and Answering Questions <a name = "qna"></a>

### 6.1 Which beer style has the highest average quality score?<a name = "q1"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

### 6.2 What is the total volume produced for each location? <a name = "q2"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

### 6.3 What is the relation between fermentation time and alcohol content?<a name = "q3"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

### 6.4 Which ingredient ratio is associated with the highest total sales?<a name = "q4"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

### 6.5 What is the average loss during brewing, fermentation, and bottling/kegging for each beer style?<a name = "q5"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby

```

## 7. Inferences and Conclusion <a name = "conclusion"></a>

### 1. Pandas:
**Strengths:**
- **Ease of Use:** Pandas is widely known for its user-friendly syntax and ease of learning.
- **Rich Functionality:** Pandas provides a plethora of functions for data manipulation, cleaning, and analysis.
- **Integration with Ecosystem:** It seamlessly integrates with other data science libraries, such as NumPy, Matplotlib, and Scikit-Learn.

**Weaknesses:**
- **Limited Scalability:** Pandas is not designed for distributed computing, making it less suitable for large datasets that don't fit into memory.
- **Performance:** Performance can be a concern for large datasets, and certain operations might be slow compared to other big data tools.

### 2. Data Table:
**Strengths:**
- **High Performance:** Data Table is built for performance, making it efficient for large datasets.
- **Memory Efficiency:** It's designed to handle datasets that are too large to fit into memory efficiently.
- **Data Manipulation:** Data Table provides a powerful set of tools for data manipulation and transformation.

**Weaknesses:**
- **Learning Curve:** Data Table may have a steeper learning curve compared to Pandas for new users.
- **Ecosystem Integration:** While it has good integration with R, its ecosystem is not as extensive as Pandas in the Python ecosystem.

### 3. PySpark:
**Strengths:**
- **Distributed Computing:** PySpark is built on top of Apache Spark, allowing it to scale horizontally and handle large datasets distributed across a cluster.
- **Performance:** Spark's in-memory processing and lazy evaluation contribute to excellent performance.
- **Built for Big Data:** PySpark is specifically designed to handle big data processing and analytics.

**Weaknesses:**
- **Complexity:** Setting up and configuring a Spark cluster can be complex, and there might be a learning curve for users new to distributed computing.
- **Overhead:** For small to medium-sized datasets, the overhead of setting up a Spark cluster might outweigh the benefits.

## Use Case Comparison:
### 1. Pandas:
Pandas is best suited for:
- Exploratory data analysis on small to medium-sized datasets.
- Prototyping and quick analysis where distributed computing is not necessary.

### 2. Data Table:
Data Table is well-suited for:
- Large datasets that do not fit into memory.
- Performance-critical data manipulation tasks.

### 3. PySpark:
PySpark excels in:
- Processing and analyzing massive datasets that require distributed computing.
- Scalable machine learning and data processing pipelines.

## Conclusion:
- **Pandas** is excellent for smaller datasets and is widely used in the data science community for its simplicity.
- **Data Table** shines in scenarios where memory efficiency and high performance are crucial, making it suitable for large datasets.
- **PySpark** is the go-to choice for big data processing, providing scalability and performance for large-scale distributed computing.


## 8. References and Future Work <a name = "future"></a>
## 9. Contributions<a name = "contribution"></a>





