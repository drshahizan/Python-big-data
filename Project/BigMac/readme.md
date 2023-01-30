# **Dataset: Airline Delay and Cancellation Data(2016 - 2018.csv)**
<img src="https://github.com/drshahizan/Python-big-data/blob/main/Project/BigMac/vaex.png"  width="320" height="100"><img src="https://github.com/drshahizan/Python-big-data/blob/main/Project/BigMac/koalas.png" width="320" height="100"><img src="https://github.com/drshahizan/Python-big-data/blob/main/Project/BigMac/Pyspark.png" width="320" height="100">

---
# **Introduction**
Welcome to our Python project where we will be comparing the use of three popular libraries: Koalas, PySpark, and Vaex. These libraries are widely used in the data science community for data manipulation and analysis. In this project, we will be exploring the strengths and limitations of each library by applying them to a specific dataset. Koalas is a powerful library that allows for easy data manipulation with a familiar pandas-like syntax. PySpark is a library that allows for efficient distributed data processing with the use of Spark. Finally, Vaex is a library that is known for its efficient handling of large datasets. Through this project, we will be comparing the performance and functionality of these libraries to see which one is the best fit for our specific use case. Let's dive in and see how these libraries compare!

Throughout this project, we will be analysing the libraries by performing the tasks below:
* Reading Dataset into Dataframe
* Data Preparation & Data Cleaning
* Visualization

---
## _Group 3_
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Muhammad Imran Hakimi Bin Mohd Shukri </th>
    <th>A20EC0213</th>
  </tr>
  <tr>
    <th>Afif Hazmie Arsyad Bin Agus</th>
    <th>A20EC0176</th>
  </tr>
    <tr>
    <th>Kong Jia Rou</th>
    <th>A20EC0198</th>
  </tr>
    <tr>
    <th>Rasmin Kaur Sandhu</th>
    <th>A19ET0216</th>
  </tr>
</table>

---
# **About the Dataset** 

In this project, we will be analysing Airline Delay and Cancellation from year 2016 - 2018 obtained from [Kaggle](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2018.csv). 

The dataset is collected by U.S. Department of Transportation's (DOT) Bureau of Transportation Statistics by tracking the on-time performance of domestic flights operated by large air carriers. Summary information on the number of on-time, delayed, canceled, and diverted flights is published in DOT's monthly Air Travel Consumer Report and in this dataset of 2016 flight delays and cancellations.

The dataset from the Kaggle are seperated to different csv files based on year of airline delay and cancellation. As mentioned before that we will be analysing the airline delay and cancellation from year 2016 - 2018, we download the three csv files for year 2016, 2017 and 2018 and then we combine them into a single dataframe.

---
# Dataset Attribute

<table>
  <tr>
    <th>Column</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>FL_DATE</th>
    <th>Date of the flight</th>
  </tr>
    <tr>
    <th>OP_CARRIER</th>
    <th>Airline Identifier</th>
  </tr>
    <tr>
    <th>OP_CARRIER_FL_NUM</th>
    <th>Flight Number</th>
  </tr>
    <tr>
    <th>ORIGIN</th>
    <th>Starting Airport Code</th>
  </tr>
    <tr>
    <th>DEST</th>
    <th>Destination Airport Code</th>
  </tr>
    <tr>
    <th>CRS_DEP_TIME</th>
    <th>Planned Departure Time</th>
  </tr>
    <tr>
    <th>DEP_TIME</th>
    <th>Actual Departure Time</th>
  </tr>
    <tr>
    <th>DEP_DELAY</th>
    <th>Total Delay on Departure in minutes</th>
  </tr>
    <tr>
    <th>TAXI_OUT</th>
    <th>The time duration elapsed between departure from the origin airport gate and wheels off</th>
  </tr>
    <tr>
    <th>WHEELS_OFF</th>
    <th>The time point that the aircraft's wheels leave the ground</th>
  </tr>
    <tr>
    <th>WHEELS_ON</th>
    <th>The time point that the aircraft's wheels touch on the ground</th>
  </tr>
    <tr>
    <th>TAXI_IN</th>
    <th>The time duration elapsed between wheels-on and gate arrival at the destination airport</th>
  </tr>
    <tr>
    <th>CRS_ARR_TIME</th>
    <th>Planned arrival time</th>
  </tr>
    <tr>
    <th>ARR_TIME</th>
    <th>Actual Arrival Time</th>
  </tr>
    <tr>
    <th>FLARR_DELAY_DATE</th>
    <th>Total Delay on Arrival in minutes</th>
  </tr>
    <tr>
    <th>CANCELLED</th>
    <th>Flight Cancelled (1 = cancelled)</th>
  </tr>
    <tr>
    <th>CANCELLATION_CODE</th>
    <th>Reason for Cancellation of flight: A - Airline/Carrier; B - Weather; C - National Air System; D - Security</th>
  </tr>
    <tr>
    <th>DIVERTED</th>
    <th>Aircraft landed on airport that out of schedule</th>
  </tr>
    <tr>
    <th>CRS_ELAPSED_TIME</th>
    <th>Planned time amount needed for the flight trip</th>
  </tr>
    <tr>
    <th>ACTUAL_ELAPSED_TIME</th>
    <th>AIR_TIME+TAXI_IN+TAXI_OUT</th>
  </tr>
    <tr>
    <th>AIR_TIME</th>
    <th>The time duration between wheels_off and wheels_on time</th>
  </tr>
    <tr>
    <th>DISTANCE</th>
    <th>Distance between two airports</th>
  </tr>
    <tr>
    <th>CARRIER_DELAY</th>
    <th>Delay caused by the airline in minutes</th>
  </tr>
    <tr>
    <th>WEATHER_DELAY</th>
    <th>Delay caused by weather</th>
  </tr>
    <tr>
    <th>NAS_DELAY</th>
    <th>Delay caused by air system</th>
  </tr>
    <tr>
    <th>SECURITY_DELAY</th>
    <th>The time duration elapsed between wheels-on and gate arrival at the destination airport</th>
  </tr>
    <tr>
    <th>LATE_AIRCRAFT_DELAY</th>
    <th>Delay caused by security</th>
  </tr>
    <tr>
    <th>Unnamed: 27</th>
    <th>Useless column</th>
  </tr>
  
</table>

---
# Questions

* Which airline has the highest number of flights from year 2016 - 2018?
* Does the departure delay affects the arrival delay?
* Which carrier has the highest total flight distance ?
* What is the average departure delay for each origin airport ?
* What is the average arrival delay for every destination airport?

---
# Conclusion
After performing EDA on the dataset, we can say that PySpark was the fastest followed by Vaex. Vaex provides fast data exploration and is often faster than Pandas, but it may not be as fast as PySpark for large datasets. For visualisation, PySpark does not have any visualisation libraries and Vaex has limited visualisation functions. When visualising with Vaex and Pyspark, we had to convert it to a pandas dataframe and use the pandas library to plot graphs. Several open source tools exist to aid visualization in Python such as matplotlib, Seaborn, Bokeh etc. However, none of these visualization tools can be used directly with PySpark's and Vaex's DataFrames. In conclusion, the fastest option will depend on the specific use case and dataset, but PySpark is generally the fastest due to its native optimized implementation for Spark.
