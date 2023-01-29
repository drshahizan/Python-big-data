<h1 align='center'>Project: New York City Automated Traffic Volume Counts</h1>

<img src="https://user-images.githubusercontent.com/120595244/215332876-47eabd62-29a3-494f-883c-7a46470ed26f.png" width="1000" height="500"/>

<h2 align='center'>Team Members: QwQ</h2>

<p align="center">
  <img src="https://user-images.githubusercontent.com/120595244/215343565-46c61886-4c14-479e-bd13-914a56c20bbd.jpg" alt="QwQ image" width="400" height="130"/>
</p>

<p align='center'>
1.   MUHAMMAD DINIE HAZIM BIN AZALI<br>                                                                                                                                 
2.   KELVIN EE<br>
3.   ADRINA ASYIQIN BINTI MD ADHA<br>
4.   RADIN DAFINA BINTI RADIN ZULKAR NAIN<br>
</p>
<br>

----------------------------------------------------------------------------------------------------------------------

<h2 align='center'>Libraries Used</h2>

<p align='center'>
  We evaluated several libraries, including pandas, polars, and datatable, but they proved to be insufficient for processing our large data due to crashes. Our final choice of these 3 libraries was based on their ability to handle the size of our data without crashing and to provide efficient processing without long wait times.
</p>

<br>

| <h3 align='center'>Koalas</h3> | <h3 align='center'>PySpark</h3>    | <h3 align='center'>Dask</h3>    |
| :---:   | :---: | :---: |
| <img src="https://raw.githubusercontent.com/databricks/koalas/master/icons/koalas-logo.png" width="330"/> | <img src="https://user-images.githubusercontent.com/120595244/215350941-4694c41a-dc3b-49f4-95c0-d7aa8b9d18ad.png" width="330"/> | <img src="https://user-images.githubusercontent.com/120595244/215351069-7855f88b-1a32-47cc-852b-9e9ddddb57c2.png" width="330"/>   |

----------------------------------------------------------------------------------------------------------------------

<h2 align='center'>About Dataset</h2>
<p align='center'>This is a link to our dataset: https://www.kaggle.com/datasets/aadimator/nyc-automated-traffic-volume-counts</p>
<p align='center'>
This project aims to study the volume of traffic in NYC at bridge crossings and roadways. The dataset consists of 14 columns and 27.4M rows. It is considered as big data and occupies 3.33GB of memory. The dataset is obtained from Kaggle. We have selected this dataset because we like to analyze the traffic volume in NYC. We will perform a series of steps like data processing, data cleaning and visualization on this dataset. Google Colab will be used in this project.
</p>
<table>
  <tr>
    <th>Columns</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>RequestID</td>
    <td>An unique ID that is generated for each counts request.</td>
  </tr>
  <tr>
    <td>Boro</td>
    <td>Lists which of the five administrative divisions of New York City the location is within, written as a word</td>
  </tr>
  <tr>
    <td>Yr</td>
    <td>The two digit year portion of the date when the count was conducted.</td>
  </tr>
  <tr>
    <td>M</td>
    <td>The two digit month portion of the date when the count was conducted.</td>
  </tr>
  <tr>
    <td>D</td>
    <td>The two digit day portion of the date when the count was conducted.</td>
  </tr>
  <tr>
    <td>HH</td>
    <td>The two digit hour portion of the time when the count was conducted.</td>
  </tr>
    <tr>
    <td>MM</td>
    <td>The two digit start minute portion of the time when the count was conducted.</td>
  </tr>
    <tr>
    <td>Vol</td>
    <td>The total sum of count collected within a 15 minute increments.</td>
  </tr>
    <tr>
    <td>SegmentID</td>
    <td>The ID that identifies each segment of a street in the LION street network version 14.</td>
  </tr>
  <tr>
    <td>WktGeom</td>
    <td>A text markup language for representing vector geometry objects on a map and spatial reference systems of spatial objects.</td>
  </tr>
  <tr>
    <td>street</td>
    <td>The 'On Street' where the count took place.</td>
  </tr>
  <tr>
    <td>fromSt</td>
    <td>The 'From Street' where the count took place.</td>
  </tr>
  <tr>
    <td>toSt</td>
    <td>The 'To Street' where the count took place.</td>
  </tr>
  <tr>
    <td>Direction</td>
    <td>The text-based direction of traffic where the count took place.</td>
  </tr>
 
    
</table>

----------------------------------------------------------------------------------------------------------------------

<h2 align='center'>Overview</h2>

<h3 align='left'>1. Data Preparation & Cleaning</h3>
<p>In this phase, we installed and utilized all 3 libraries, performing data cleaning tasks including:<br>
  
  - Removing null values<br>
  - Removing duplicated rows<br>
</p>

<h3 align='left'>2. Exploratory Analysis & Visualization</h3>
<p>During this phase, we utilized the "describe" function to calculate various statistics, such as mean, sum, range, and others, for numerical columns. Additionally, we conducted exploratory analysis of certain columns within the dataset.<br>
</p>

<h3 align='left'>3. Asking and Answering Questions</h3>
<p>We were asking 5 questions throughout this phase and we visualize a chart such as bar chart, line chart and pie chart to answer our question.<br>
  These are the list of our questions:<br>

  1. Which division has the most cars?<br>
      - We wanted to know which part of New York has the highest count of cars.<br>
  <br>
  
  2. What is the top 3 street that most cars go?<br>
      - We wanted to determine the street with the highest number of cars.<br>
  <br>
  
  3. In Brooklyn, what year has the highest count of cars?<br>
      - Our objective was to identify the year with the highest number of cars recorded in Brooklyn.<br>
  <br>
  
  4. What is the 5 year that has the least request ID?<br>
      - We wanted to know what year record the lowest request ID.<br>
  <br>
  
  5. Which direction has the most cars headed to?<br>
      - Our goal was to identify the direction that most cars were headed towards.<br>
</p>

----------------------------------------------------------------------------------------------------------------------
<h2 align='center'>Conclusion</h2>
<p align='center'>
The dataset shows the Manhattan has the highest amount of cars followed by Queens, and Brooklyn. It is safe to assume that it is among the busiest city. In 2014, it has the highest distribution of administrative placed in New York. We has also found out most cars goes through a dead end. It is very strange to think a place as busy as New York has many Dead Ends, but there had been reports and pictures throughout the Internet about the Dead Ends in New York.
</p>
<p align='center'>
Based on the EDA above, we can conclude that Koalas library compute the fastest in the overall tasks. Koalas is the best fit which could process operations many times(100x) faster than Pandas without getting crash. To rank the three in terms of speed of computing, Koalas takes the first place, PySpark, then Dask.
</p>
