## Group Members: 
<table align = "center">
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>LUQMAN ARIFF BIN NOOR AZHAR</th>
    <th>A20EC0202</th>
  </tr>
  <tr>
    <th>AHMAD AIMAN HAFIZI BIN MUHAMMAD</th>
    <th>A20EC0177</th>
  </tr>
    <tr>
    <th>LEE CAI XUAN</th>
    <th>A20EC0062</th>
  </tr>
    <tr>
    <th>MYZA NAZIFA BINTI NAZRY</th>
    <th>A20EC0219</th>
  </tr>
</table>

<h1>PySpark as an alternative to Pandas</h1>

![Pyspark](https://miro.medium.com/max/1200/1*qgkjkj6BLVS1uD4mw_sTEg.png)

PySpark is an interface for Apache Spark in Python. It enables you to write Spark applications using Python API and also provides the PySpark shell for interactively analyzing data in a distributed environment. PySpark supports most of Spark’s features such as Spark SQL, DataFrame, Streaming, MLlib (Machine Learning) and Spark Core.

The key features of PySpark are as follows:

- In-memory computation

- Distributed processing using parallelize

- Can be used with many cluster managers (Spark, Yarn, Mesos e.t.c)

- Fault-tolerant

- Immutable

- Lazy evaluation

- Cache & persistence

- Inbuild-optimization when using DataFrames


<hr>

<h1>Installation</h1>
<code> !pip install pyspark </code>

<hr>

<h1>Content</h1>
DataTable-File2

For this assignment, we have decided to use the dataset, 1000000 Sales Records which provides the information regarding the information of sales record from various countries such as the region, country, item type, sales channel, order priority, order date and so on. We will be implementing and comparing the processing time of PySpark with Pandas.

#### Attribute Information:
| Attribute | Description |
| --- | --- |
| **Region** |   The region of the sales originated.  |
|**Country** |   The country of the sales originated. |
| **Item Type** | The type of item being sold. |
| **Sales Channel** |  The type of channels used by the company. |
| **Order Priority** | The priority of the order.  |
| **Order Date** |  The date on which the item has been ordered.   |
| **Order ID** | The unique identifier for the order.  |
| **Ship Date** | The date on which the item will be shipped.  |
| **Units Sold** |  The number of units of item has been sold.   |
|**Unit Price** |  The price the item has been sold. |
| **Unit Cost** | The expense incurred for item by the company. |
| **Total Revenue** | The total amount of money the company brings in from selling the item.  |
| **Total Cost** | The total cost that has been incurred by the company. |
| **Total Profit** |   The total profit gainned by the company.  |

<h1>Results</h1>

#### Time Performance results:

|  | Pandas (unit:µs) | PySpark (unit:µs) |
| --- | --- | --- |
| **Reading File** |   11.40  |   9.06  |
|**Display Dataset** |   8.34 |   8.34  |
| **Checking Info** | 8.85 |   8.82  |
| **Checking Null Value** |  9.06 |   6.20  |


Based on the results above, we can conclude that Pyspark has a better performance compared to Pandas.
