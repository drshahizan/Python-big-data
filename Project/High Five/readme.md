<h1> 🛫Airline Delay and Cancellation Dataset Analysis from 2015-2016 </h1>

**Group Members:**

<br>

<table width = 700>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>AHMAD MUHAIMIN BIN AHMAD HAMBALI</th>
    <th>A20EC0006</th>
  </tr>
  <tr>
    <th>NAYLI NABIHAH BINTI JASNI</th>
    <th>A20EC0105</th>
  </tr>
    <tr>
    <th>SAKINAH AL’IZZAH BINTI MOHD ASRI</th>
    <th>A20EC0142</th>
  </tr>
    <tr>
    <th>LEE JIA XIAN</th>
    <th>A20EC0200</th>
  </tr>
</table> 
<br>
<h2> Libraries: Pandas 🐼, Koalas 🐨, Modin</h2>

<p>Pandas:
Pandas is a popular and widely-used data analysis library in Python. It provides data structures for efficiently storing and manipulating large datasets and tools for working with them. It is designed to be flexible, fast and expressive, making it a popular choice for data analysis and manipulation tasks.

Koalas:
Koalas is a library built on top of Apache Spark and Pandas. It aims to provide a pandas-like API for working with large datasets, leveraging the scalability and performance benefits of Apache Spark. Koalas provides a familiar interface for data analysis and manipulation tasks, making it easier for Pandas users to scale their workloads to big data environments.

Modin:
Modin is a library that speeds up data processing in Python, especially for Pandas operations. It is designed to work seamlessly with Pandas and drop-in replacement for it. It uses the Ray library to provide parallel processing capabilities to Pandas operations, resulting in substantial speed improvements. Modin can handle large datasets and provides faster results compared to Pandas, making it a popular choice for big data processing tasks.</P>

<br>
<h2> Dataset 📑 </h2>
<h4>Dataset description</h4>
<p>The "Airline Delay and Cancellation Data 2015-2016" found on Kaggle is an extensive collection of data that showcases the performance of different airlines for the two-year span of 2015 to 2016. This dataset is quite comprehensive, as it comprises of information about the delays, cancellations, and a range of other performance metrics of various airlines. The details included in this database are the airline carrier, flight number, departure and arrival airports, departure and arrival times, as well as information about the delays and cancellations experienced.</p>


<a href="https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018?select=2009.csv">link to the dataset</a>


<br>
<table>
  <tr>
    <th>Column</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>FL_DATE</th>
    <th>Date of the flight, yy/mm/dd</th>
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
<br>
<h2>Exploratory Analysis and Visualization 📊</h2>

<ol>
  <li>Histogram: Flight Delay Times Distribution</li>
  <li>Bar Chart: Flight Delays Count by each Airlines</li>
  <li>Bar Chart: Average Flight Distance by Airlines</li>
  <li>Pie Chart: Top 5 Airlines with most flight numbers</li>
</ol>

<br>
<h2>List of questions ❓</h2>

<ol>
  <li>Top 5 Airlines that have the most flight numbers</li>
  <li>Top 10 days with the most number of delay flights</li>
  <li>What is the longest and shortest of flight delay time?</li>
  <li>What is the percentage of delay flight for each airlines?</li>
  <li>What is the average flight distance for each airlines?</li>
</ol>

<h4>Summary of the questions</h4>

<p>In 2015-2016, the top airline with the most flights was Southwest Airlines (2522917 flights). The day with the highest rate of delayed flights was January 4th, 2015. The longest and shortest delay time was 2214 minutes and 1 minute, respectively. Spirit Airlines had the highest percentage of delayed flights, while Virgin America had the highest average traveled distance and Envoy Air had the least.</p>

<h2> Running Time for Data Cleaning 🏃</h2>

<h3>Replace Operation:</h3>
<table>
  <tr>
    <th>Library</th>
    <th>CPU Time (ms)</th>
    <th>Wall Time (ms)</th>
  </tr>
    <tr>
    <td>Pandas</td>
    <td>6.71 s</td>
    <td>6.9 s</td>
  </tr>
  <tr>
    <td>Koalas</td>
    <td>65.3</td>
    <td>416</td>
  </tr>
  <tr>
    <td>Modin</td>
    <td>264</td>
    <td>8.77 s</td>
  </tr>

</table>
<h3>Remove Missing Values Operation:</h3>
<table>
  <tr>
    <th>Library</th>
    <th>CPU Time (ms)</th>
    <th>Wall Time (ms)</th>
  </tr>
    <tr>
    <td>Pandas</td>
    <td>6.77 s</td>
    <td>7.02 s</td>
  </tr>
  <tr>
    <td>Koalas</td>
    <td>1.06 s</td>
    <td>1min 2s</td>
  </tr>
  <tr>
    <td>Modin</td>
    <td>511</td>
    <td>26.5 s</td>
  </tr>
</table>
<h3>Drop Operation:</h3>
<table>
  <tr>
    <th>Library</th>
    <th>CPU Time (ms)</th>
    <th>Wall Time (ms)</th>
  </tr>
    <tr>
    <td>Pandas</td>
    <td>796</td>
    <td>809</td>
  </tr>
  <tr>
    <td>Koalas</td>
    <td>31.6</td>
    <td>183</td>
  </tr>
  <tr>
    <td>Modin</td>
    <td>3.87</td>
    <td>8.19</td>
  </tr>
</table>
<h3>Read CSV Operation:</h3>
<table>
  <tr>
    <th>Library</th>
    <th>CPU Time (ms)</th>
    <th>Wall Time (ms)</th>
  </tr>
  <tr>
    <td>Pandas</td>
    <td>40.4 s</td>
    <td>1min 23s</td>
  </tr>
    <tr>
    <td>Koalas</td>
    <td>537</td>
    <td>1min 2s</td>
  </tr>
  <tr>
    <td>Modin</td>
    <td>2.18 s</td>
    <td>1min 12s</td>
  </tr>

</table>

<h2>Conclusion</h2>

<p>In conclusion, the performance of Pandas, Koalas, and Modin libraries varies depending on the specific operation being performed on the DataFrame. Based on the results, Modin had the best performance in terms of CPU time and wall time for operations like removing columns, whereas Koalas performed better for operations like replacing values in a column. However, Pandas had the longest CPU and wall times for all operations. It is recommended to evaluate the performance of each library for a specific use case to determine the most suitable option for a given situation.</p>
