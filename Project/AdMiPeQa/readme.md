<h1>Air Flight Analysis  <img width=50px; height=50px src="https://user-images.githubusercontent.com/120556342/215304943-6df48d0a-d866-4f2c-91bf-263d47579dc2.png"></h1>

<p align="center">
  <img width=1000px; height=500px src="https://user-images.githubusercontent.com/120556342/215265584-6f73a09a-ac06-48db-b53c-58bcd370c320.png">
</p>

<h2>Group Members</h2>
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>ADAM WAFII BIN AZUAR</th>
    <th>A20EC0003</th>
  </tr>
  <tr>
    <th>HONG PEI GEOK</th>
    <th>A20EC0044</th>
  </tr>
    <tr>
    <th>MIKHEL ADAM BIN MUHAMMAD EZRIN</th>
    <th>A20EC0237</th>
  </tr>
    <tr>
    <th>QAISARA BINTI ROHZAN</th>
    <th>A20EC0133</th>
  </tr>
</table>

<h2>Introduction</h2>
This project aims to investigate the Air Flight in 2022. The dataset consists of 61 columns and 4078318 rows. It is considered as big data and occupies 1.42GB of memory. The dataset is obtained from Kaggle which contains many kinds of dataset ranging from agriculture to education. We have selected this dataset because we like to analyze the flight status. We will perform a series of steps like data processing, data cleaning and visualization on this dataset. Google Colab will be used in this project. Other than that, there will be three libraries related to big data processing which are Pandas, Dask and Koalas being used in this project. At the end, we will compare the processing results from these libraries.

<h2>Libraries</h2>
<h3>1. Pandas</h3>
<h3>2. Dask</h3>
<h3>3. Koalas</h3>

<h2>Dataset</h2>
<a href="https://www.kaggle.com/datasets/robikscube/flight-delay-dataset-20182022?select=Combined_Flights_2022.csv">Kaggle: Air Flight Dataset</a><br>
<h4>Attribute Information:</h4>
<table>
  <tr>
    <th>Acronym</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>FlightDate</th>
    <td>Flight Date (yyyymmdd)</td>
  </tr>
    <tr>
    <th>Airline</th>
    <td>Name of Airline</td>
  </tr>
    <tr>
    <th>OP_CARRIER_FL_NUM</th>
    <td>Flight Number</td>
  </tr>
    <tr>
    <th>Origin</th>
    <td>Origin Airport</td>
  </tr>
    <tr>
    <th>Dest</th>
    <td>Destination Airport</td>
  </tr>
    <tr>
    <th>Cancelled</th>
    <td>Cancelled Flight Indicator (1=Yes)</td>
  </tr>
    <tr>
    <th>Diverted</th>
    <td>Diverted Flight Indicator (1=Yes)</td>
  </tr>
    <tr>
    <th>CRSDepTime</th>
    <td>CRS Departure Time (local time: hhmm)</td>
  </tr>
    <tr>
    <th>DepTime</th>
    <td>Actual Departure Time (local time: hhmm)</td>
  </tr>
    <tr>
    <th>DepDelayMinutes</th>
    <td>Difference in minutes between scheduled and actual departure time. Early departures set to 0.</td>
  </tr>
    <tr>
    <th>DepDelay</th>
    <td>Difference in minutes between scheduled and actual departure time. Early departures show negative numbers.</td>
  </tr>
    <tr>
    <th>ArrTime</th>
    <td> Actual Arrival Time (local time: hhmm)</td>
  </tr>
    <tr>
    <th>ArrDelayMinutes</th>
    <td>Difference in minutes between scheduled and actual arrival time. Early arrivals set to 0.</td>
  </tr>
    <tr>
    <th>AirTime</th>
    <td>Flight Time, in Minutes</td>
  </tr>
    <tr>
    <th>CRSElapsedTime</th>
    <td>CRS Elapsed Time of Flight, in Minutes</td>
  </tr>
    <tr>
    <th>ActualElapsedTime</th>
    <td>Elapsed Time of Flight, in Minutes</td>
  </tr>
    <tr>
    <th>Distance</th>
    <td>Distance between airports (miles)</td>
  </tr>
    <tr>
    <th>Year</th>
    <td>Year</td>
  </tr>
    <tr>
    <th>Quarter</th>
    <td>Quarter (1-4)</td>
  </tr>
    <tr>
    <th>Month</th>
    <td>Month</td>
  </tr>
    <tr>
    <th>DayofMonth</th>
    <td>Day of Month</td>
  </tr>
    <tr>
    <th>DayOfWeek</th>
    <td>Day of Week</td>
  </tr>
</table> 
