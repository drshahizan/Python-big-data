<h1>Airline Delay in 2017</h1>

<p align="center">
  <img src="https://www.thetimes.co.uk/imageserver/image/%2Fmethode%2Fsundaytimes%2Fprod%2Fweb%2Fbin%2Fa919ce06-72b3-11eb-b6bc-1d2ce6b7b794.jpg?crop=2250%2C1266%2C0%2C117" />
</p>

All data files are downloaded from [Transtats](https://www.transtats.bts.gov/Homepage.asp), which stores flights on-time performance from 1987 to 2018 through [Kaggle](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018). However, we chose only 2017 data file, since it is large enough to perform methods in handling big data.

We are motivated to do EDA on this dataset because we, ourselves are curious about the insights that can be obtain from this dataset. The dataset also has many columns with numerical values which we believe, could give more meaningful analysis.

<h2>Prepared by:</h2>
<li>Nur Izzah Mardhiah binti Rashidi A20EC0116</li>
<li>Radin Dafina binti Zulkar Nain A20EC0135</li>

<h2>Submission to:</h2>
Prof. Madya. Ts. Dr. Mohd Shahizan Bin Othman
SECP3133-01

<h2>About Dataset</h2>
<table>
  <tr>
    <th>Columns</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>FL_DATE</td>
    <td>Date of the flight, yy/mm/dd</td>
  </tr>
  <tr>
    <td>OP_CARRIER</td>
    <td>Airline identifier.</td>
  </tr>
  <tr>
    <td>OP_CARRIER_FL_NUM</td>
    <td>Flight Number</td>
  </tr>
  <tr>
    <td>ORIGIN</td>
    <td>Starting Airport Code</td>
  </tr>
  <tr>
    <td>DEST</td>
    <td>Destination Airport Code</td>
  </tr>
  <tr>
    <td>CRS_DEP_TIME</td>
    <td>Planned Departure Time</td>
  </tr>
    <tr>
    <td>DEP_TIME</td>
    <td>Actual Departure Time</td>
  </tr>
    <tr>
    <td>DEP_DELAY</td>
    <td>Total Delay on Departure in minutes</td>
  </tr>
    <tr>
    <td>TAXI_OUT</td>
    <td>The time duration elapsed between departure from the origin airport gate and wheels off</td>
  </tr>
  <tr>
    <td>WHEELS_OFF</td>
    <td>The time point that the aircraft's wheels leave the ground</td>
  </tr>
  <tr>
    <td>WHEELS_ON</td>
    <td>The time point that the aircraft's wheels touch on the ground</td>
  </tr>
  <tr>
    <td>TAXI_IN</td>
    <td>The time duration elapsed between wheels-on and gate arrival at the destination airport</td>
  </tr>
  <tr>
    <td>CRS_ARR_TIME</td>
    <td>Planned arrival time</td>
  </tr>
  <tr>
    <td>ARR_TIME</td>
    <td>Actual Arrival Time</td>
  </tr>
  <tr>
    <td>ARR_DELAY</td>
    <td>Total Delay on Arrival in minutes</td>
  </tr>
    <tr>
    <td>CANCELLED</td>
    <td>Flight Cancelled (1 = cancelled)</td>
  </tr>
    <tr>
    <td>CANCELLATION_CODE</td>
    <td>Reason for Cancellation of flight: A - Airline/Carrier; B - Weather; C - National Air System; D - Security</td>
  </tr>
    <tr>
    <td>DIVERTED</td>
    <td>Aircraft landed on airport that out of schedule</td>
  </tr>
    <tr>
    <td>CRS_ELAPSED_TIME</td>
    <td>Planned time amount needed for the flight trip</td>
  </tr>
    <tr>
    <td>ACTUAL_ELAPSED_TIME</td>
    <td>AIR_TIME+TAXI_IN+TAXI_OUT</td>
  </tr>
    <tr>
    <td>AIR_TIME</td>
    <td>The time duration between wheels_off and wheels_on time</td>
  </tr>
    <tr>
    <td>DISTANCE</td>
    <td>Distance between two airports</td>
  </tr>
  <tr>
    <td>CARRIER_DELAY</td>
    <td>Delay caused by the airline in minutes</td>
  </tr>
  <tr>
    <td>WEATHER_DELAY</td>
    <td>Delay caused by weather</td>
  </tr>
  <tr>
    <td>NAS_DELAY</td>
    <td>Delay caused by air system</td>
  </tr>
  <tr>
    <td>SECURITY_DELAY</td>
    <td>Delay caused by security</td>
  </tr>
  <tr>
    <td>LATE_AIRCRAFT_DELAY</td>
    <td>-</td>
  </tr>

    
</table>

<h2>Result & Insights</h2>

- All of the top 5 most delayed airlines (Southwest Airlines, SkyWest Airlines, Delta Airlines, American Airlines, United Airlines) are all listed in the top 5 busiest airports in the United States in 2017. There could be a line of aeroplanes waiting to take off on the runway in a congested or unusually busy airport. Thus, it is expected that they have higher number of delays compared to other airlines.

- On the other hand, the possible factor that contributes to the delay of these airlines on the beginning and end of the year is due to annual holidays. However, the highest average delay of all airlines is between April to July due to factors that we cannot predict and need more resources and informations about the dataset. Thus, we can conclude that the delay of airlines is highly affected by the number of airlines being in one airport at the same time.

- Every airline have different rate of efficiency of their operations and management systems which contribute to the different hours of delay. Southwest Airlines maintained to be the least delayed airlines compared to the other four popular airlines in 2017. Southwest Airlines may have a better management and operation systems thus contribute less to the average hours of delay over the year. Therefore, the average hours of delay over the year is highly affected by the performance of their operations system that controls the carrier delay, aircraft delay and security delay.

<h2>Reference & Future Work</h2>
In a further project, we would like to examine more data from more years and obtain more information each airline may have regarding the reason for a delay.


References:

   1. [Data Guide](https://pandas.pydata.org/docs/user_guide/text.html)
   2. [Data Visualization Guide](https://www.analyticsvidhya.com/blog/2021/02/an-intuitive-guide-to-visualization-in-python/)
   3. [Dataset](https://www.kaggle.com/datasets/yuanyuwendymu/airline-delay-and-cancellation-data-2009-2018)
    
