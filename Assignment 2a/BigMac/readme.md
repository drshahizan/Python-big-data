# **Dataset: Health Insurance Marketplace**
<img src="https://github.com/drshahizan/Python-big-data/blob/main/Assignment%202a/team%203/Pandas_logo.svg.png"  width="300" height="100"><img src="https://github.com/drshahizan/Python-big-data/blob/main/Assignment%202a/team%203/1_MEcMeVoX9Mdqtk83oLBuEQ.png" width="350" height="90">
## _Group 3_
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Muhammad Imran Hakim Bin Mohb Shukri </th>
    <th>A20EC0</th>
  </tr>
  <tr>
    <th>Afif Hazmie Arsyad Bin Agus</th>
    <th>A20EC0</th>
  </tr>
    <tr>
    <th>Kong Jia Rou</th>
    <th>A20EC0198</th>
  </tr>
    <tr>
    <th>Rasmin Kaur Sandhu</th>
    <th>A19ET0216</th>
  </tr>
</table>

---
**Introduction**
---
The use of Python and Pandas, its most well-liked data wrangling library, is growing rapidly. Python and Pandas make data exploration and transformation easier when compared to rivals like Java. But scalability and efficiency problems with Python and Pandas are well recognised. It therefore comes as no surprise that numerous developers are attempting to increase Python and Pandas' capability in various ways. In this project, we are comparing Pandas and Vaex. Vaex is a partial substitute for Pandas that makes advantage of slow evaluation and memory mapping to let programmers work with huge datasets on common computers.

This folder contains two files:<br>
File 1: Basic concept of Vaex and code implementation<br>
File 2: Comparison between Pandas and Vaex

We are going to compare both libraries based on :
- Reading Files
- Data Cleaning
- Data Transformation
- Visualization

---
**Dataset**

For this project we decided to use a medical dataset [Rate.csv](https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv). 

Medical datasets are electronic collections of data that are related to the healthcare industry. It uses a virtual memory approach to allow processing of large datasets that do not fit in memory. Vaex also provides a variety of functions for data visualization and exploration. Pandas is another popular Python library for data manipulation and analysis. It is well-suited for small to medium-sized datasets that can be loaded into memory, but it can become slow and unwieldy when working with large datasets. In this assignment, we will show you how which library are the most suitable to use with large dataset.

| Functions | Pandas | Vaex |
| ------ | ------ | ------ |
| Reading Files | 56.4 s| 12.2 s|
| Data transformation | 108 ms| 1.67 ms|
| Data filtering | 1.88s| 1.46s|
| Data filtering | 1.88s| 1.46s|
