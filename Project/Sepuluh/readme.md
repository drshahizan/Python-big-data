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

![PySpark](https://static.javatpoint.com/tutorial/pyspark/images/pyspark.png)
<br>
PySpark is the Python API for Apache Spark, an open-source distributed data processing system designed for large-scale data processing. Some of the <b>key features</b> of PySpark are listed as below:
<ul>
  <li>PySpark provides <b>real-time computation</b> on big data since it focuses on in-memory processing, and shows low latency. </li>

  <li>PySpark framework is able to <b>support multiple languages</b> such as Scala, Java, Python, and R, hence making it compatible in handling various kinds of huge datasets. </li>

  <li>PySpark has <b>powerful caching and disk constancy.</b></li>

  <li>PySpark can achieve <b>high data processing speed</b>, which is around 100 times faster in memory and 10 times faster on the disk. </li>

</ul>

<h3>Application of PySpark in real life</h3>
<ul>
  <li><b>Entertainment Industry</b>
    <ul>
      <li>Netflix company used PySpark for real-time processing of personalized movies or web series to its customers.</li>
      <li>It processes approximately 450 billion events per day. </li>
    </ul>
  </li>
  
  <li><b>Commercial Sector</b>
    <ul>
      <li>Bank and other financial sectors use PySpark in obtaining and analysing their customers' social media to get useful information which aid in decision making for credit risk assessment, targeted ad and customer segmentation. </li>
      <li>Here, Spark is important in Fraud Detection. </li>
    </ul>
  </li>
  
  <li><b>Healthcare</b>
    <ul>
      <li>PySpark is used to analyse the patients' records and previous medical reports to predict possible health issues in future. </li>
    </ul>
  </li>
  
</ul>

<h3>Install PySpark</h3>
<code>!pip install pyspark</code>




<h1>Content</h1>
File 1: Airline Delay and Cancellation Data 2017 - 2018

In this project, we will be analysing 

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


