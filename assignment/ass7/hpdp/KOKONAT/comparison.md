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
```ruby
from google.colab import files
```
2. Upload the Kaggle API token file ('kaggle.json') using the file upload widget. The file 'kaggle.json' can be found under your account settings in Kaggle.
```ruby
uploaded = files.upload()
```

3. Utilise the Kaggle API Token to extract the dataset.
```ruby
# Move Kaggle API Token to the Correct Directory
!mkdir -p /root/.kaggle
!cp kaggle.json /root/.kaggle/
!chmod 600 /root/.kaggle/kaggle.json

# Download the Kaggle dataset
!kaggle datasets download -d ankurnapa/brewery-operations-and-market-analysis-dataset

# Unzip the downloaded dataset
!unzip brewery-operations-and-market-analysis-dataset
```

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
```ruby
dt_df = dt.fread('brewery_data_complete_extended.csv')
```
- Memory usage: 1490.3573122024536 MB
- Computation Time: 1.3939999803369574e-06 seconds

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
```ruby
dt_df.head(5)
```
- Memory usage: 1589.36328125 MB
- Computation Time: 0.0002989768981933594 seconds
  
Library 3: **PySpark**
```ruby
brewery_df.show(5, truncate=False)
```
Memory usage: 115.92578125 MB

Computation Time: 0.9608330726623535 seconds

### 4.4 Explore the number of rows & columns <a name = "num_rows"></a>
Library 1: **Pandas**

Library 2: **Datatable**
```ruby
num_rows, num_cols = dt_df.shape
print(f"Number of rows: {num_rows}")
print(f"Number of columns: {num_cols}")
```
- Memory usage: 1589.36328125 MB
- Computation Time: 0.004721879959106445 seconds
  
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
```ruby
# Check for missing values using countna() in datatable
missing_values = dt_df.countna()
print("Missing values per column:")
print(missing_values.to_pandas().transpose())
```
- Memory usage: 1635.71875 MB
- Computation Time: 0.670168399810791 seconds
  
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
```ruby
# Display the data types of each column
column_types = list(zip(dt_df.names, dt_df.stypes))
print("\nData types of each column:\n")
for column, column_type in column_types:
    print(f"{column}: {column_type}")
```
- Memory usage: 1589.36328125 MB
- Computation Time: 0.010242223739624023 seconds
  
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
```ruby
dt_df.nunique()
```
- Memory usage: 1636.140625 MB
- Computation Time: 24.82753849029541 seconds
  
Library 3: **PySpark**
```ruby
# Assuming you have a PySpark DataFrame named brewery_df
unique_values = [(column, brewery_df.select(approx_count_distinct(column)).collect()[0][0]) for column in brewery_df.columns]

# Print number of unique values per column
print("\nNumber of Unique Values per Column:")
for col_name, unique_count in unique_values:
    print(f"{col_name}: {unique_count}")
```
Memory usage: 116.2578125 MB

Computation Time: 584.2389488220215 seconds

## 5. Exploratory Data Analysis  <a name = "eda"></a>

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
selected_columns = ["Beer_Style", "Fermentation_Time"]
filtered_data = brewery_df.select(selected_columns).filter(col("Fermentation_Time").isNotNull())

# Sample a fraction of the data (adjust fraction as needed)
sampled_data = filtered_data.sample(fraction=0.0001, seed=42)

# Convert PySpark DataFrame to Pandas for visualization
pandas_df = sampled_data.toPandas()

# Plot the boxplot using Matplotlib and Seaborn
plt.figure(figsize=(12, 6))
sns.boxplot(x='Beer_Style', y='Fermentation_Time', data=pandas_df)
plt.title('Boxplot of Fermentation Time by Beer Style')
plt.xlabel('Beer Style')
plt.ylabel('Fermentation Time')
plt.xticks(rotation=45, ha='right')  # Rotate x-axis labels for better visibility
plt.show()

```
Memory usage: 220.65234375 MB

Computation Time: 47.033284187316895 seconds

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
# Assuming the correct column names for loss are "Loss_During_Brewing", "Loss_During_Fermentation", and "Loss_During_Bottling_Kegging"
selected_columns_loss = ["Beer_Style", "Loss_During_Brewing", "Loss_During_Fermentation", "Loss_During_Bottling_Kegging"]

# Group by beer style and calculate the total loss
total_loss_by_style = brewery_df.groupBy("Beer_Style").agg(
    sum(col("Loss_During_Brewing")).alias("Total_Loss_During_Brewing"),
    sum(col("Loss_During_Fermentation")).alias("Total_Loss_During_Fermentation"),
    sum(col("Loss_During_Bottling_Kegging")).alias("Total_Loss_During_Bottling_Kegging")
)

# Convert PySpark DataFrame to Pandas for visualization
total_loss_by_style_pandas = total_loss_by_style.toPandas()

# Plotting
plt.figure(figsize=(12, 6))
plt.plot(total_loss_by_style_pandas['Beer_Style'], total_loss_by_style_pandas['Total_Loss_During_Brewing'], label='Loss During Brewing', color='blue')
plt.plot(total_loss_by_style_pandas['Beer_Style'], total_loss_by_style_pandas['Total_Loss_During_Fermentation'], label='Loss During Fermentation', color='green')
plt.plot(total_loss_by_style_pandas['Beer_Style'], total_loss_by_style_pandas['Total_Loss_During_Bottling_Kegging'], label='Loss During Bottling Kegging', color='orange')

plt.xlabel('Beer Style')
plt.ylabel('Total Loss')
plt.title('Total Loss by Beer Style')
plt.xticks(rotation=0, ha='right')
plt.legend()
plt.show()
```
Memory usage: 233.21875 MB

Computation Time: 27.439659595489502 seconds


## 6. Asking and Answering Questions <a name = "qna"></a>

### 6.1 Which beer style has the highest average quality score?<a name = "q1"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
# Create a Spark session
spark = SparkSession.builder.appName("BeerAnalysis").getOrCreate()

# Group by beer style and calculate the average quality score
average_quality_by_style = brewery_df.groupBy("Beer_Style").agg(avg(col("Quality_Score")).alias("Average_Quality_Score"))

# Find the beer style with the highest average quality score
highest_quality_style = average_quality_by_style.orderBy(col("Average_Quality_Score").desc()).first()

print("Beer Style with the Highest Average Quality Score:")
print(highest_quality_style)

```
Memory usage: 233.47265625 MB

Computation Time: 26.092206239700317 seconds

### 6.2 What is the total volume produced for each location? <a name = "q2"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
location_counts = brewery_df.groupBy("Location").count().orderBy("count", ascending=False).toPandas()
location_counts 

# Plot the bar chart with count labels
plt.figure(figsize=(10, 6))
bars = plt.bar(location_counts["Location"], location_counts["count"], color='skyblue')
plt.title('Distribution of Sales Data Across Different Locations')
plt.xlabel('Location')
plt.ylabel('Count')
plt.xticks(rotation=45, ha="right")

# Add count labels on top of each bar
for bar in bars:
    yval = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2, yval, round(yval, 2), ha='center', va='bottom')

plt.show()
```
Memory usage: 235.75390625 MB

Computation Time: 16.331711292266846 seconds

### 6.3 What is the relation between fermentation time and alcohol content?<a name = "q3"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
# Assuming your PySpark DataFrame is named brewery_df
selected_columns = ["Fermentation_Time", "Alcohol_Content"]
filtered_data = brewery_df.select(selected_columns).filter(
    col("Fermentation_Time").isNotNull() &
    col("Alcohol_Content").isNotNull()
)

# Sample a fraction of the data (adjust fraction as needed)
sampled_data = filtered_data.sample(fraction=0.0001, seed=42)

# Convert PySpark DataFrame to Pandas for visualization
pandas_df = sampled_data.toPandas()

# Sort the data by Fermentation_Time for a line plot
pandas_df = pandas_df.sort_values(by='Fermentation_Time')

# Plot the line plot using Matplotlib and Seaborn
plt.figure(figsize=(8, 6))
sns.lineplot(x='Fermentation_Time', y='Alcohol_Content', data=pandas_df, color='green')
plt.title('Line Plot: Fermentation Time vs Alcohol Content')
plt.xlabel('Fermentation Time')
plt.ylabel('Alcohol Content')
plt.show()
```
Memory usage: 223.80078125 MB

Computation Time: 30.488824605941772 seconds

### 6.4 Which ingredient ratio is associated with the highest total sales?<a name = "q4"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
selected_columns = ["Ingredient_Ratio", "Total_Sales"]
filtered_data = brewery_df.select(selected_columns).filter(col("Ingredient_Ratio").isNotNull() & col("Total_Sales").isNotNull())

# Group by ingredient ratio and calculate the total sales
total_sales_by_ratio = filtered_data.groupBy("Ingredient_Ratio").agg(sum("Total_Sales").alias("Total_Sales"))

# Find the ingredient ratio with the highest total sales
highest_sales_ratio = total_sales_by_ratio.orderBy(col("Total_Sales").desc()).first()["Ingredient_Ratio"]

print(f"The ingredient ratio associated with the highest total sales is: {highest_sales_ratio}")
```
Memory usage: 196.4296875 MB

Computation Time: 38.24022150039673 seconds

### 6.5 What is the average loss during brewing, fermentation, and bottling/kegging for each beer style?<a name = "q5"></a>
Library 1: **Pandas**

Library 2: **Datatable**

Library 3: **PySpark**
```ruby
selected_columns = ["Beer_Style", "Loss_During_Brewing", "Loss_During_Fermentation", "Loss_During_Bottling_Kegging"]
filtered_data = brewery_df.select(selected_columns).filter(
    col("Loss_During_Brewing").isNotNull() &
    col("Loss_During_Fermentation").isNotNull() &
    col("Loss_During_Bottling_Kegging").isNotNull()
)

# Group by beer style and calculate the average loss for each category
average_loss_by_style = filtered_data.groupBy("Beer_Style").agg(
    mean("Loss_During_Brewing").alias("Avg_Loss_Brewing"),
    mean("Loss_During_Fermentation").alias("Avg_Loss_Fermentation"),
    mean("Loss_During_Bottling_Kegging").alias("Avg_Loss_Bottling_Kegging")
)

# Convert PySpark DataFrame to Pandas for visualization
pandas_df = average_loss_by_style.toPandas()

# Plot the line plot using Matplotlib and Seaborn
plt.figure(figsize=(12, 6))
sns.lineplot(data=pandas_df.melt(id_vars="Beer_Style"), x="variable", y="value", hue="Beer_Style", marker='o')
plt.title('Average Loss by Beer Style')
plt.xlabel('Loss Category')
plt.ylabel('Average Loss')
plt.xticks(rotation=45, ha='right')
plt.legend(title='Beer Style', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.show()
```
Memory usage: 201.6640625 MB

Computation Time: 56.94319486618042 seconds

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

### Use Case Comparison:
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

### Conclusion:
- **Pandas** is excellent for smaller datasets and is widely used in the data science community for its simplicity.
- **Data Table** shines in scenarios where memory efficiency and high performance are crucial, making it suitable for large datasets.
- **PySpark** is the go-to choice for big data processing, providing scalability and performance for large-scale distributed computing.


## 8. References and Future Work <a name = "future"></a>
## 9. Contributions<a name = "contribution"></a>





