# Project Title: **nyc-yellow-taxi-trip-data**

<br>
<p align="center">
<img src="https://github.com/Terence172/FirstR/blob/main/Pictures/nycTaxi.jpg" style="text-align:center;" height="200" />
</p>

## 🚀 Group Members QUAD (Team 8)
> 1. CHONG KAI ZHE (A20EC0186)
> 2. TERENCE A/L LOORTHANATHAN (A20EC0165)
> 3. RISHMA FATHIMA BINTI BASHER (A20EC0137)
> 4. NUR SYAMALIA FAIQAH BINTI MOHD KAMAL (A20EC0118)
<br>

The purpose of this notebook is to record and analyse performance between three different libraries, namely Polars, Koalas and Datatable. Not to mention, assess the learning curve of each of these libraries. We will be using documentation provided for each of these libraries, and usefulness of each libraries and their respective learning curve will be analysed as well.

Sources: [Kaggle](https://www.kaggle.com/datasets/elemento/nyc-yellow-taxi-trip-data)

Libraries Used:
> 1. Polars
> 2. Koalas
> 3. Datatable

Data Collection:
In this dataset, we have collected the data for 4 months particularly:
- Jan 2015: 1.99 GB
- Jan 2016: 1.71 GB
- Feb 2016: 1.78 GB
- Mar 2016: 1.91 GB

However, in this notebook only data collected on January 2015 will be used.

In this notebook, we use 'yellow_tripdata_2015-01.csv'. This dataset contain 12748986 records and 19 columns. The variables are:

| Field Name	| Description |
|-------------|-------------|
|VendorID |	A code indicating the TPEP provider that provided the record (Creative Mobile Technologies & VeriFone Inc. )|
|tpep_pickup_datetime	| The date and time when the meter was engaged. |
|tpep_dropoff_datetime	| The date and time when the meter was disengaged. |
| Passenger_count |	The number of passengers in the vehicle. This is a driver-entered value. |
| Trip_distance |	The elapsed trip distance in miles reported by the taximeter.|
| Pickup_longitude	| Longitude where the meter was engaged. |
| Pickup_latitude	| Latitude where the meter was engaged. |
| RateCodeID |	The final rate code in effect at the end of the trip. |
|Store_and_fwd_flag |	This flag indicates whether the trip record was held in vehicle memory before sending to the vendor, aka “store and forward,” because the vehicle did not have a connection to the server. (Y= store and forward trip N= not a store and forward trip ) |
| Dropoff_longitude	| Longitude where the meter was disengaged. |
| Dropoff_ latitude |	Latitude where the meter was disengaged. |
| Payment_type |	A numeric code signifying how the passenger paid for the trip. |
| Fare_amount |	The time-and-distance fare calculated by the meter. |
| Extra |	Miscellaneous extras and surcharges. Currently, this only includes. the $0.50 and $1 rush hour and overnight charges. |
| MTA_tax	| 0.50 MTA tax that is automatically triggered based on the metered rate in use. |
| Improvement_surcharge	| 0.30 improvement surcharge assessed trips at the flag drop. the improvement surcharge began being levied in 2015. |
| Tip_amount |	Tip amount – This field is automatically populated for credit card tips.Cash tips are not included. |
| Tolls_amount |	Total amount of all tolls paid in trip. |
| Total_amount |	The total amount charged to passengers. Does not include cash tips. |

<br>

**Findings in this Notebook :**
Based on the analysis of the performance of three libraries for big data processing, it can be concluded that datatable is the fastest in terms of execution time, but it has a steep learning curve. Polar is a close second in terms of execution time and is easier to learn compared to datatable. Finally, Koalas, although slower in execution time, is easier to learn than datatable. Based on these results, the choice of library would depend on the trade-off between processing time and ease of learning.
<br>
Based on our opinion, we think polars and koalas has a really good site that documented their own individual functions and methods. This really helps lower their learning curve and make the whole process so much easier. However, when it comes to Datatable, it is quite the opposite. A huge reason to why we took so long learning datatable is because their documentation was not easily understandable compared to its peers.
<br>
All things said, with our experience using pandas, we think that polars is the best library among these libraries as it has the sweet spot between learning curve and good processing time.



