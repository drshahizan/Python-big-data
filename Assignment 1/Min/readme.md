# **Group Members:**
1. MIKHEL ADAM BIN MUHAMMAD EZRIN (A20EC0237)
2. AHMAD MUHAIMIN BIN AHMAD HAMBALI (A20EC0006)

## **US Accidents (2016 - 2021) Analysis**

The dataset contains car accident information from all 49 states in the USA, and the data was gathered from February 2016 to December 2021. For this analysis, we will use Python and several libraries including mathplotlib, pandas, seaborn, and numpy as well as using sampling to perform our analysis.

## **Downloading the Dataset**

The dataset we'll be using is titled [US Accidents (2016 - 2021)](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents), taken from Kaggle. Instead of downloading the data set onto our own system, we will be using an API command to download the dataset directly into Google Colab.

### Dataset Description

1) `ID`: unique identifier of the accident record
2) `Severity`: shows the severity of the accident, a number between 1 and 4, where 1 indicates the least impact on traffic and 4 indicates a significant impact on traffic
3) `Start_Time`: shows the start time of the accident in the local time zone
4) `End_Time`: shows the end time of the accident in the local time zone, referring to when the impact of the accident on traffic flow was dismissed
5) `Start_Lat`: shows the latitude in GPS coordinates of the start point
6)`Start_Lng`: shows the longitude in GPS coordinates of the start point
7) `End_Lat`: shows the latitude in GPS coordinates of the end point
8) `End_Lng`: shows the longitude in GPS coordinates of the end point
9) `Distance(mi)`: shows the length of the road extent affected by the accident
10) `Description`: shows a human-provided description of the accident
11) `Number`: shows the street number in the address field
12) `Street`: shows the street name in the address field
13) `Side`: shows the relative side of the street (right or left) in the address field
14) `City`: shows the city in the address field
15) `County`: shows the county in the address field
16) `State`: shows the state in the address field
17) `Zipcode`: shows the zip code in the address field
18) `Country`: shows the country in the address field
19) `Timezone`: shows the time zone based on the location of the accident (eastern, central, etc.)
20) `Airport_Code`: denotes an airport-based weather station that is the closest one to the location of the accident
21) `Weather_Timestamp`: shows the time stamp of the weather observation record in the local time zone
22) `Temperature(F)`: shows the temperature in degrees Fahrenheit
23) `Wind_Chill(F)`: shows the wind chill in degrees Fahrenheit
24) `Humidity(%)`: shows the humidity as a percentage
25) `Pressure(in)`: shows the air pressure in inches
26) `Visibility(mi)`: shows the visibility in miles
27) `Wind_Direction`: shows the wind direction
28) `Wind_Speed(mph)`: shows the wind speed in miles per hour
29) `Precipitation(in)`: shows the amount of precipitation in inches, if any
30) `Weather_Condition:` shows the weather condition (e.g. rain, snow, thunderstorm, fog, etc.)
31) `Amenity`: a POI annotation indicating the presence of an amenity in a nearby location
32) `Bump`: a POI annotation indicating the presence of a speed bump or hump in a nearby location
33) `Crossing`: a POI annotation indicating the presence of a crossing in a nearby location
34) `Give_Way`: a POI annotation indicating the presence of a give_way in a nearby location
35) `Junction`: a POI annotation indicating the presence of a junction in a nearby location
36) `No_Exit`: a POI annotation indicating the presence of a no_exit in a nearby location
37) `Railway`: a POI annotation indicating the presence of a railway in a nearby location
38) `Roundabout`: POI annotation indicating the presence of a roundabout in a nearby location
39) `Station`: POI annotation indicating the presence of a station in a nearby location
40) `Stop`: POI annotation indicating the presence of a stop in a nearby location
41) `Traffic_Calming`: POI annotation indicating the presence of traffic calming measures in a nearby location
42) `Traffic_Signal`: POI annotation indicating the presence of a traffic signal in a nearby location
43) `Turning_Loop`: POI annotation indicating the presence of a turning loop in a nearby location
44) `Sunrise_Sunset`: Indicator of the period of day (day or night) based on sunrise and sunset times
45) `Civil_Twilight`: Indicator of the period of day (day or night) based on civil twilight times
46) `Nautical_Twilight`: Indicator of the period of day (day or night) based on nautical twilight times
47) `Astronomical_Twilight`: Indicator of the period of day (day or night) based on astronomical twilight times
