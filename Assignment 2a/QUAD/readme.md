    
# Introduction to Polars 🐻‍❄️

<br>
 <p align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTKH6i3lJ9tW7bna90G-1SO7QB__e3ri_8MCw&usqp=CAU"/>
 </p>
</br>

## 🚀 Group Members QUAD (Team 8)
> 1. CHONG KAI ZHE (A20EC0186)
> 2. TERENCE A/L LOORTHANATHAN (A20EC0165)
> 3. RISHMA FATHIMA BINTI BASHER (A20EC0137)
> 4. NUR SYAMALIA FAIQAH BINTI MOHD KAMAL (A20EC0118)

 **Polars** is both lazy and semi-lazy. It allows you to accomplish most of your work eagerly, similar to Pandas, but it also provides a sophisticated expression syntax that will be optimised and processed within the query engine.

- Polars' purpose is to deliver a lightning-fast DataFrame library that makes use of all available cores on your machine. Unlike dask, which attempts to parallelize existing single-threaded libraries such as NumPy and Pandas, Polars is intended from the ground up for parallelization of queries on DataFrames.

Polars goes to great lengths to:

1.   Reduce redundant copies
2.   Traverse memory cache efficiently
3.   Minimize contention in parallelism


For more information about Polars, you can view from [Polars](https://pola-rs.github.io/polars-book/user-guide/index.html).

# Dataset **nyc-yellow-taxi-trip-data** 
Sources: [Kaggle](https://www.kaggle.com/datasets/elemento/nyc-yellow-taxi-trip-data)

Data Collection:
In this dataset, we have collected the data for 4 months particularly:
- Jan 2015: 1.99 GB
- Jan 2016: 1.71 GB
- Feb 2016: 1.78 GB
- Mar 2016: 1.91 GB

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
Tools ⚙

- Google Collab
- Github

# Conclusion
- To conclude, we can observe that Polars is a very quick EDA project creator to conduct a lot of data processing on huge datasets or big data.
