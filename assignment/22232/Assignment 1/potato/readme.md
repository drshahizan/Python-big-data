## Group Members: 
<table border="solid">
  <tr>
    <th>Name</th>
    <th>Matric Number</th>
  </tr>
  <tr>
    <td>KONG JIA ROU</td>
    <td>A20EC0198</td>
  </tr>
  
  <tr>
    <td>YONG ZHI YAN</td>
    <td>A20EC0172</td>
  </tr>
</table>

<h1>Flight Delays and Cancellations at 2015</h1>

This project aims to investigate the flight delays and cancellations in United States (U.S.) at 2015. The dataset consists of 5819079 rows and 31 columns. It is considered as big data and occupies the memory 564 MB. We choose this dataset because we are interested in finding the pattern of flights cancellation in U.S.. We will handle the data through data processing, data cleaning, and data visualization. To carry out this project, we will be using Google Colab and then post it to Github once we have done it.  

<b>Dataset:<b>
<a href="https://www.kaggle.com/datasets/usdot/flight-delays?select=flights.csv">Flight Delays and Cancellations at 2015</a>


Attribute Information:

| Attribute | Description |
| --- | --- |
| **YEAR** |  Year of the Flight Trip |
|**MONTH** |   Month of the Flight Trip |
| **DAY** | Day of the Flight Trip |
| **DAY_OF_WEEK** |  Day of week of the Flight Trip |
| **AIRLINE** |  Airline Identifier |
| **FLIGHT_NUMBER** |    Flight Identifier |
| **TAIL_NUMBER** |   Aircraft Identifier |
| **ORIGIN_AIRPORT** |   Starting Airport |
|**DESTINATION_AIRPORT** |   Destination Airport |
| **SCHEDULED_DEPARTURE** |    Planned Departure Time |
|**DEPARTURE_TIME** |   WHEEL_OFF - TAXI_OUT |
| **DEPARTURE_DELAY** | Total Delay on Departure |
| **TAXI_OUT** |  The time duration elapsed between departure from the origin airport gate and wheels off |
| **WHEELS_OFF** |  The time point that the aircraft's wheels leave the ground |
| **SCHEDULED_TIME** |    Planned time amount needed for the flight trip |
| **ELAPSED_TIME** |   AIR_TIME+TAXI_IN+TAXI_OUT |
| **AIR_TIME** |   The time duration between wheels_off and wheels_on time |
|**DISTANCE** |   Distance between two airports |
| **WHEELS_ON** |   The time point that the aircraft's wheels touch on the ground |
| **TAXI_IN** |   The time duration elapsed between wheels-on and gate arrival at the destination airport |
|**SCHEDULED_ARRIVAL**|Planned arrival time|
|**ARRIVAL_TIME**|WHEELS_ON+TAXI_IN|
|**ARRIVAL_DELAY**|ARRIVAL_TIME-SCHEDULED_ARRIVAL|
|**DIVERTED**|Aircraft landed on airport that out of schedule|
|**CANCELLED**|Flight Cancelled (1 = cancelled)|
|**CANCELLATION_REASON**|Reason for Cancellation of flight: A - Airline/Carrier; B - Weather; C - National Air System; D - Security|
|**AIR_SYSTEM_DELAY**|Delay caused by air system|
|**SECURITY_DELAY**|Delay caused by security|
|**AIRLINE_DELAY**|Delay caused by the airline|
|**LATE_AIRCRAFT_DELAY**|Delay caused by aircraft|
|**WEATHER_DELAY**|Delay caused by weather|
