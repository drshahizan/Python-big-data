## Group Members:
<table border="solid">
  <tr>
    <th>Name</th>
    <th>Matric Number</th>
  </tr>
  <tr>
    <td>FARAH IRDINA BINTI AHMAD BAHARUDIN</td>
    <td>A20EC0035</td>
  </tr>
  <tr>
    <td>LOW JUNYI</td>
    <td>A20EC0071</td>
  </tr>
  <tr>
    <td>NURFARRAHIN BINTI CHE ALIAS</td>
    <td>A20EC0121</td>
  </tr>
  <tr>
    <td>YONG ZHI YAN</td>
    <td>A20EC0172</td>
  </tr>
</table>

<h1>Airline Delay and Cancellation Data 2017 - 2018 (PySpark vs Polars vs Pandas)</h1>

In this project, we will carry out an analysis on the data of airline delay and cancellation using 3 different Python libraries, which are PySpark, Polars and Pandas. We aim to investigate and <b>compare the time completion</b> of the three selected libraries on the similiar tasks. A short intoduction of each selected library will be shown as below. 

<h2>PySpark</h2>
<img src='https://static.javatpoint.com/tutorial/pyspark/images/pyspark.png' alt='PySpark'>
PySpark is the Python API for Apache Spark, an open-source distributed data processing system designed for large-scale data processing. Some of the <b>key features</b> of PySpark are listed as below:
<ul>
  <li>PySpark provides <b>real-time computation</b> on big data since it focuses on in-memory processing, and shows low latency. </li>

  <li>PySpark framework is able to <b>support multiple languages</b> such as Scala, Java, Python, and R, hence making it compatible in handling various kinds of huge datasets. </li>

  <li>PySpark has <b>powerful caching and disk constancy.</b></li>

  <li>PySpark can achieve <b>high data processing speed</b>, which is around 100 times faster in memory and 10 times faster on the disk. </li>

</ul>

<h4>Install PySpark</h4>
<code>!pip install pyspark</code>
<br>

<h2>Polars</h2>
<img src='https://raw.githubusercontent.com/pola-rs/polars-static/master/web/polars-logo-python.svg' height=200px width=200px alt='Polars'>
Polars is a Python library for creating interactive plots and charts using the Plotly library. It is built on top of Plotly, which means that it inherits the functionality and features of Plotly, but provides a simpler and more convenient API for creating plots and charts. Polars is particularly useful for creating polar plots and radar charts, which are not natively supported by Plotly. With Polars, we can easily create interactive plots and charts with a few lines of code, and customize them with a wide range of options.

<h4>Install Polars</h4>
<code>!pip install polars</code>
<br>

<h2>Pandas</h2>
<img src='https://miro.medium.com/max/640/1*0qpVZw5qKncoFBYJf4DlpA.webp' alt='Pandas'>
Pandas is an open-source data analysis and data manipulation library for Python. It provides fast, flexible and expressive data structures, designed to make working with structured data in "human-friendly" way. Pandas makes it easy to handle missing data, aggregate and manipulate data, create new variables, and visualize data using plots and graphs. With its simple yet powerful APIs, Pandas has become a popular tool for data analysis and manipulation for both academia and industry.

<h4>Import Pandas</h4>
<code>import pandas as pd</code>
<br>

<h1>Content</h1>
<b>Dataset: Airline Delay and Cancellation Data 2017 - 2018</b><br><br>

In this project, we will be performing analysis on the dataset of airline delay and cancellation which includes data on flight delays, cancellations, and various other performance metrics for a large number of airlines. The dataset also includes information on the carrier, flight number, departure and arrival airports, departure and arrival times, and delay and cancellation information. 

The objectives of this project are listed as below:
1.   Comparing the time completion between three libraries (PySpark, Polars, Pandas).
2.   Performing analysis and visualizations.
3.   Asking and answering five possible questions regarding the dataset.

There are two datasets obtained from kaggle which included in this project, this is because the one dataset alone is not big enough to meet the requirement of dataset size (1 GB and above), hence the combination of two datasets with the size of 1.5 GB solve this problem. The datasets retrieved are [Airline Delay and Cancellation Data 2017](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2017.csv) and [Airline Delay and Cancellation Data 2018](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2018.csv). 

#### Attribute Information:
| Acronym | Description |
| --- | --- |
| **FL_DATE** |  The date of flight in year/month/day (yyyy-mm-dd) format.  |
|**OP_CARRIER** |  The two-letter code of the airline identifier.  |
| **OP_CARRIER_FL_NUM** | The flight number. |
| **ORIGIN** |  The unique idenifier code of the starting airport.  |
| **DEST** | The unique idenifier code of the destination airport.  |
| **CRS_DEP_TIME** |  The planned departure time.   |
| **DEP_TIME** | The actual departure time.  |
| **DEP_DELAY** | The total delay of departure recorded in minutes.  |
| **TAXI_OUT** |  The time duration elapsed between departure from the origin airport gate and wheels off.   |
|**WHEELS_OFF** |  The time point that the aircraft's wheels leave the ground. |
| **WHEELS_ON** | The time point that the aircraft's wheels touch on the ground. |
| **TAXI_IN** | The time duration elapsed between wheels-on and gate arrival at the destination airport.  |
| **CRS_ARR_TIME** | The planned arrival time.  |
| **ARR_TIME** | The actual arrival time. |
| **ARR_DELAY** |   The total delay on arrival recorded in minutes.  |
| **CANCELLED** |  The code to represent flight cancellation, where 1 indicates the flight being cancelled and 0 indicates the flight fly as usual.  |
| **CANCELLATION_CODE** | The code to represent flight cancellation reason, where A indicates the flight being cancelled due to the airline or carrier, B for weather reason, C for national air system reason and D due to security reason.  |
| **DIVERTED** | The code to represent the aircraft landed on airport that out of schedule, where 1 indicates out of schedule and 0 otherwise.  |
|**CRS_ELAPSED_TIME** |  The planned time amount needed for the flight trip. |
| **ACTUAL_ELAPSED_TIME** | Calculated by the sum of AIR_TIME, TAXI_IN and TAXI_OUT. |
| **AIR_TIME** | The time duration between wheels_off and wheels_on time. |
| **DISTANCE** | The distance between two airports.  |
| **CARRIER_DELAY** |  The delay caused by the airline in minutes.   |
| **WEATHER_DELAY** | The delay caused by the weather in minutes.  |
| **NAS_DELAY** | The delay caused by the air system in minutes.  |
| **SECURITY_DELAY** | The delay caused by the security issues in minutes.  |
| **LATE_AIRCRAFT_DELAY** | The delay caused by the late aircraft in minutes.   |
| **Unnamed: 27** | Useless columns in this dataset which can be ignored.  |


