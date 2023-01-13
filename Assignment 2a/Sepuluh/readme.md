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

<h1>PySpark as an alternative to Pandas</h1>

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

<h1>Install PySpark</h1>
<code>!pip install pyspark</code>


<h1>Content</h1>
File 1: Pyspark on Health Insurance Marketplace

#### Attribute Information:
| Acronym | Description |
| --- | --- |
| **BusinessYear** |   The year of the business.  |
|**StateCode** |  The two-letter code for the state where the health insurance plan is offered.  |
| **IssuerId** | Unique identifier of insurer who offers the health insurance plan. |
| **SourceName** |  The source of the rate information (e.g. the insurer, the state insurance department). |
| **VersionNum** | A version number for the rate information.  |
| **ImportDate** |  The date on which the rate information was imported into the Marketplace database.   |
| **IssuerId2** | Another unique identifier of the insurer who offers the health insurance plan.  |
| **FederalTIN** | Federal income taxes  |
| **RateEffectiveDate** |  The effective date of the rate.   |
|**RateExpirationDate** |  The expiration date of the rate. |
| **PlanId** | Unique identifier for the health insurance plan. |
| **RatingAreaId** | The age of the insured person for which the rate information applies.  |
| **Tobacco** | The rate which applies to tobacco person and non-tobacco person. |
| **Age** |   The rate according to the age of the insured person.  |
| **IndividualRate** |  The monthly premium (cost) for the health insurance plan for an individual.  |
| **IndividualTobaccoRate** | The monthly premium for the health insurance plan for an individual tobacco user.  |
| **Couple** | The monthly premium for the health insurance plan for couple.  |
|**PrimarySubscriberAndOneDependent** |  The primary subscriber for the health insurance plan with one dependent. |
| **PrimarySubscriberAndTwoDependents** | The primary subscriber for the health insurance plan with two dependent. |
| **CoupleAndOneDependent** | The monthly premium for the health insurance plan for couple with one dependent. |
| **CoupleAndTwoDependents** | The monthly premium for the health insurance plan for couple with two dependents.  |
| **CoupleAndThreeOrMoreDependents** |  The monthly premium for the health insurance plan for couple with three or more dependents.   |
| **RowNumber** | The row number of rate information.  |



