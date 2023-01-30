## Group Members:
<table border="solid">
  <tr>
    <th>Name</th>
    <th>Matric Number</th>
  </tr>
  <tr>
    <td>FARAH IRDINA BINTI AHMAD BAHARUDIN</td>
    <td>A20EC0035</td>
  </tr>
  <tr>
    <td>LOW JUNYI</td>
    <td>A20EC0071</td>
  </tr>
  <tr>
    <td>NURFARRAHIN BINTI CHE ALIAS</td>
    <td>A20EC0121</td>
  </tr>
  <tr>
    <td>YONG ZHI YAN</td>
    <td>A20EC0172</td>
  </tr>
</table>

<h1>Airline Delay and Cancellation Data 2017 - 2018 (PySpark vs Polars vs Pandas)</h1>

![PySpark](https://static.javatpoint.com/tutorial/pyspark/images/pyspark.png)
<br>
PySpark is the Python API for Apache Spark, an open-source distributed data processing system designed for large-scale data processing. Some of the <b>key features</b> of PySpark are listed as below:
<ul>
  <li>PySpark provides <b>real-time computation</b> on big data since it focuses on in-memory processing, and shows low latency. </li>

  <li>PySpark framework is able to <b>support multiple languages</b> such as Scala, Java, Python, and R, hence making it compatible in handling various kinds of huge datasets. </li>

  <li>PySpark has <b>powerful caching and disk constancy.</b></li>

  <li>PySpark can achieve <b>high data processing speed</b>, which is around 100 times faster in memory and 10 times faster on the disk. </li>

</ul>

<h3>Application of PySpark in real life</h3>
<ul>
  <li><b>Entertainment Industry</b>
    <ul>
      <li>Netflix company used PySpark for real-time processing of personalized movies or web series to its customers.</li>
      <li>It processes approximately 450 billion events per day. </li>
    </ul>
  </li>
  
  <li><b>Commercial Sector</b>
    <ul>
      <li>Bank and other financial sectors use PySpark in obtaining and analysing their customers' social media to get useful information which aid in decision making for credit risk assessment, targeted ad and customer segmentation. </li>
      <li>Here, Spark is important in Fraud Detection. </li>
    </ul>
  </li>
  
  <li><b>Healthcare</b>
    <ul>
      <li>PySpark is used to analyse the patients' records and previous medical reports to predict possible health issues in future. </li>
    </ul>
  </li>
  
</ul>

<h3>Install PySpark</h3>
<code>!pip install pyspark</code>




<h1>Content</h1>
File 1: Airline Delay and Cancellation Data 2017 - 2018

This dataset is about the Health Insurance Marketplace. The dataset you provided is from the Health Insurance Marketplace on Kaggle, and specifically, it is the Rate.csv file. This dataset includes data on rates for health insurance plans in the Marketplace for the years 2014 to 2022. The data includes information such as the rate, the rating area, the issuer, the plan type, and the metal level. This information can be used to analyze trends in health insurance pricing and plan options over time. This dataset was retrieved from [here](https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv). 

#### Attribute Information:
| Acronym | Description |
| --- | --- |
| **FL_DATE** |   The year of the business.  |
|**OP_CARRIER** |  The two-letter code for the state where the health insurance plan is offered.  |
| **OP_CARRIER_FL_NUM** | Unique identifier of insurer who offers the health insurance plan. |
| **ORIGIN** |  The source of the rate information (e.g. the insurer, the state insurance department). |
| **DEST** | A version number for the rate information.  |
| **CRS_DEP_TIME** |  The date on which the rate information was imported into the Marketplace database.   |
| **DEP_TIME** | Another unique identifier of the insurer who offers the health insurance plan.  |
| **DEP_DELAY** | Federal income taxes  |
| **TAXI_OUT** |  The effective date of the rate.   |
|**WHEELS_OFF** |  The expiration date of the rate. |
| **WHEELS_ON** | Unique identifier for the health insurance plan. |
| **TAXI_IN** | The age of the insured person for which the rate information applies.  |
| **CRS_ARR_TIME** | The age of the insured person for which the rate information applies.  |
| **ARR_TIME** | The rate which applies to tobacco person and non-tobacco person. |
| **ARR_DELAY** |   The rate according to the age of the insured person.  |
| **CANCELLED** |  The monthly premium (cost) for the health insurance plan for an individual.  |
| **CANCELLATION_CODE** | The monthly premium for the health insurance plan for an individual tobacco user.  |
| **DIVERTED** | The monthly premium for the health insurance plan for couple.  |
|**CRS_ELAPSED_TIME** |  The primary subscriber for the health insurance plan with one dependent. |
| **ACTUAL_ELAPSED_TIME** | The primary subscriber for the health insurance plan with two dependent. |
| **AIR_TIME** | The monthly premium for the health insurance plan for couple with one dependent. |
| **DISTANCE** | The monthly premium for the health insurance plan for couple with two dependents.  |
| **CARRIER_DELAY** |  The monthly premium for the health insurance plan for couple with three or more dependents.   |
| **WEATHER_DELAY** | The row number of rate information.  |
| **NAS_DELAY** | The row number of rate information.  |
| **SECURITY_DELAY** | The row number of rate information.  |
| **LATE_AIRCRAFT_DELAY** | The row number of rate information.  |
| **Unnamed: 27** | The row number of rate information.  |


