<h1 align='center'>Project: New York City Automated Traffic Volume Counts</h1>

![image](https://user-images.githubusercontent.com/120595244/215332876-47eabd62-29a3-494f-883c-7a46470ed26f.png)

<h2 align='center'>Team Members: QwQ</h2>

<p align="center">
  <img src="https://user-images.githubusercontent.com/120595244/215343565-46c61886-4c14-479e-bd13-914a56c20bbd.jpg" alt="QwQ image"/>
</p>

<p align='center'>
1.   MUHAMMAD DINIE HAZIM BIN AZALI<br>                                                                                                                                 
2.   RADIN DAFINA BINTI RADIN ZULKAR NAIN<br>
3.   ADRINA ASYIQIN BINTI MD ADHA<br>
4.   KELVIN EE<br>
</p>

<h2>Libraries Used</h2>

<h3>Koalas</h3>
<h3>Pyspark</h3>
<h3>Dask</h3>
----------------------------------------------------------------------------------------------------------------------
<h5><p>Dataset Link: https://www.kaggle.com/datasets/aadimator/nyc-automated-traffic-volume-counts</p></h5>
<h2>About Dataset</h2>
<h4>
This project aims to study the volume of traffic in NYC at bridge crossings and roadways. The dataset consists of 14 columns and 27.4M rows. It is considered as big data and occupies 3.33GB of memory. The dataset is obtained from Kaggle. We have selected this dataset because we like to analyze the traffic volume in NYC. We will perform a series of steps like data processing, data cleaning and visualization on this dataset. Google Colab will be used in this project.
</h4>
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

<h2>Conclusion<h/2>

<h4>
<p>
The dataset shows the Manhattan has the highest amount of cars followed by Queens, and Brooklyn. It is safe to assume that it is among the busiest city. In 2014, it has the higest distribution of administrative placed in New York. We has also found out most cars goes through a dead end. It is very strange to think a place as busy as New York has many Dead Ends, but there had been reports and pictures throughout the Internet about the Dead Ends in New York.

Based on the EDA above, we can conclude that Koalas library compute the fastest in the overall tasks. Koalas is the best fit which could process operations many times(100x) faster than Pandas without getting crash. To rank the three in terms of speed of computing, Koalas takes the first place, PySpark, then Dask.
</p>
</h4>
