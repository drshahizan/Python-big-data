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
<h2> Libraries: Pandas, Koalas, Modin</h2>

<p>Pandas:
Pandas is a popular and widely-used data analysis library in Python. It provides data structures for efficiently storing and manipulating large datasets and tools for working with them. It is designed to be flexible, fast and expressive, making it a popular choice for data analysis and manipulation tasks.

Koalas:
Koalas is a library built on top of Apache Spark and Pandas. It aims to provide a pandas-like API for working with large datasets, leveraging the scalability and performance benefits of Apache Spark. Koalas provides a familiar interface for data analysis and manipulation tasks, making it easier for Pandas users to scale their workloads to big data environments.

Modin:
Modin is a library that speeds up data processing in Python, especially for Pandas operations. It is designed to work seamlessly with Pandas and drop-in replacement for it. It uses the Ray library to provide parallel processing capabilities to Pandas operations, resulting in substantial speed improvements. Modin can handle large datasets and provides faster results compared to Pandas, making it a popular choice for big data processing tasks.</P>

<br>
<h2> Dataset </h2>

<br>
<h4>Dataset description</h4>
<p>The "Airline Delay and Cancellation Data 2015-2016" found on Kaggle is an 
extensive collection of data that showcases the performance of different airlines for the two-year span of 2015 to 2016. This dataset is quite comprehensive, as it comprises of information about the delays, cancellations, and a range of other performance metrics of various airlines. The details included in this database are the airline carrier, flight number, departure and arrival airports, departure and arrival times, as well as information about the delays and cancellations experienced.</p>

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
