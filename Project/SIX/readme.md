# 🚀 Project: NYC Parking Ticket Analysis Using 3 Different Libraries

| Name | Matric Number |
| ----- | ----- |
| LEE MING QI | A20EC0064|
| NUR IRDINA ALIAH BINTI ABDUL WAHAB |A20EC0115 |
| SINGTHAI SRISOI| A20EC0147|
| AMIRAH RAIHANAH BINTI ABDUL RAHIM |A20EC0182 |

---
# **Introduction**
In this project, we will be comparing the performance of 3 different python libraries which are Dask, PySpark and Koalas on a large dataset.
These 3 libraries are the alternatives to Pandas library for faster and better performance. Every libraries has its own strength and weakness and this project will help you to determine which library you can use for your python project. We use NYC Parking Tickets dataset from Kaggle that you can download using this link. This dataset has 10 million rows and 51 columns with the size of 2GB. We will perform an EDA on the dataset using the libraries stated and give our opinions on performance, ease of use and help documentation. You will find each operation in 3 different libraries and time taken for each operation.

We will evaluate the 3 libraries using the operations performed on EDA that consists of:
* Import CSV file into dataframe
* Data Cleaning
* Data Visualization
* Data Questions and Answers 

---

# **Dataset**
NYC Parking Ticket dataset that can be obtained from Kaggle is about parking tickets issued in NYC on the year 2018. There are more than 10 million tickets issued every year! This is a large dataset that contains 10 million rows and 51 columns. Below are the attributes information.

| Columns | Description |
| ----- | ----- |
| Summons Number| Summons ID|
| Plate ID |No plate of tickets issued |
| Registration State| Registration state of the vehicle|
| Plate Type | Plate type of the vehicle |
| Issue Date | Date of ticket issued |
| Violation Code | Code on violation made |
| Vehicle Body Type | Type of vehicle body |
| Vehicle Make | Brand of the vehicle |
| Issuing Agency | Agency that will be issuing |
| Street Code 1 | Street code 1 where vehicle violates |
| Street Code 2 | Street code 2 where vehicle violates |
| Street Code 3 | Street code 3 where vehicle violates |
| Vehicle Expiration Date | Vehicle expired date |
| Violation Location | Location of the vehicle violates |
| Violation Precint | Precint of the vehicle violates |
| Issuer Precint | Issuer precint |
| Issuer Code | Code of the issuer |
| Issuer Command | Command of the issuer |
| Issuer Squed  | Which squed the issuer is from |
| Violation Time | When is the violation made |
| Time First Observed | Time of the first observed |
| Violation County | County of the violation made |
| Violation In Front Or Opposite | Violation in front or opposite county |
| House Number | House number of the parking ticket issued |
| Street Name | Street Name of the ticket issued |
| Intersecting Street | Intersecting street |
| Date First Observed | Date first observed |
| Law Section | Law section of the violation |
| Sub Division | Sub Division of the law violation |
| Violation Legal Code | Violation legal code |
| To Hours In Effect | Hours ticket effect |
| Vehicle Color | Colour of the vehicle |
| Unregistered Vehicle? | Is it unregistered vehicle |
| Vehicle Year | Year of the vehicle |
| Meter Number | Meter number |
| Feet From Curb | Feet from curb |
| Violation Post Code | Postcode of the violation |
| Violation Description | Description of the violation |
| No Standing or Stopping Violation | Standing or stopping violation |
| Hydrant Violation | Hydrant violation or not |
| Double Parking Violation | Is it double parking violation |
--
 # **Inferences and Conclusion**
 After conducting Exploratory Data Analysis (EDA) on the NYC parking ticket dataset using Dask, PySpark, and Koalas, it is clear that each library has its own strengths and weaknesses. Dask is a powerful library for parallel processing and is well-suited for large datasets, but it can be challenging to set up and can be less intuitive than other libraries. PySpark is widely used in the big data community and is known for its scalability and ability to handle large datasets, but it can be challenging to use and has a steep learning curve. Koalas, on the other hand, provides a familiar interface to users who are familiar with Pandas, and is relatively easy to use, but its performance may not be as robust as other libraries for larger datasets.
