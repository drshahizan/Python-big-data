# Project: Amazon Book Review

<p align="center">
  <img src="https://apicms.thestar.com.my/uploads/images/2022/03/04/1502291.jpg" width="600" />
</p>

This file has information about 3M book reviews for 212404 unique book and users who gives these reviews for each book spanning May 1996 - July 2014.This dataset was found from Kaggle and its size is 2.86 GB.

<strong> Data Source: </strong> [Amazon Books Reviews](https://www.kaggle.com/datasets/mohamedbakhet/amazon-books-reviews?select=Books_rating.csv)
<br>
<strong> File Name: </strong> Books_rating.csv

## Group Members: 
<table align = "center">
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Madina Suraya binti Zharin</th>
    <th>A20EC0203</th>
  </tr>
  <tr>
    <th>Nur Izzah Mardhiah binti Rashidi</th>
    <th>A20EC0116</th>
  </tr>
    <tr>
    <th>Tan Yong Sheng</th>
    <th>A20EC0157</th>
  </tr>
    <tr>
    <th>Chloe Racquelmae Kennedy</th>
    <th>A20EC0026</th>
  </tr>
</table>

## Content:
This dataset contains 3000000 records and 10 columns which are:

| Features | Description |
| --- | ----------- |
| id | The ID of Book |
| Title | 	Book Title |
| Price | The price of Book |
| User_id | 	ID of the user who rates the book |
| profileName | 	Name of the user who rates the book |
| review/helpfulness | Helpfulness rating of the review |  
| review/score | Rating from 0 to 5 for the book |  
| review/time | Time of given the review |  
| review/summary | The summary of a text review |  
| review/text | The full text of a review |

### Comparing Three Libraries
- Pandas
- PySpark
- Koalas

### Data Cleaning
- Get information of dataframe
- Get shape
- Drop columns
- Drop null rows
- Drop duplicated rows
- Change data type

### Exploratory Data Analysis
- describe()
- Box plot
- Distribution of Review
- Top 5 Books with 1 star Review
- Percentage of Books with Over 100 Reviews
- Helpfulness of Review Graph

### Question & Answer
- Question 1: Top 5 user gave the most number of review
- Question 2: Does users who gave reviews are helpful, in general?
- Question 3: Top 10 books which have the most number of reviews
- Question 4: Most frequent word in 5 rated review summary
- Question 5: How many books which users consider as a great book ?
- Question 6: Which 10 books have the highest average review score?

## Summary
The Koalas project makes data scientists more productive when interacting with big data, by implementing the Pandas DataFrame API on top of Apache Spark. Pandas is the de facto standard (single-node) DataFrame implementation in Python, while Spark is the de facto standard for big data processing.

However, in this project we did not get the chance to experience how fast Koalas and PySpark can be compared to Pandas using Google Colab. According to our [readings](https://stackoverflow.com/questions/49360888/google-colab-is-very-slow-compared-to-my-pc), these are the tips and tricks which we overlooked that may be used to accelerate your processing time using Google Colab:-

- It can be very slow when we are reading data from Google Drive. Try to upload zip file to Colab and unzip there.
- Or you can try upload Kaggle API json file to Google Colab. Can refer [here](https://saedhussain.medium.com/google-colaboratory-and-kaggle-datasets-b57a83eb6ef8#:%7E:text=Step%203%3A%20Upload%20Kaggle%20API%20json%20file%20to%20Google%20Colab&text=PS%3A%20You%20could%20use%20this,the%20files%20in%20the%20directory.). 
- Make sure GPU is enabled by going to Runtime -> Change runtime type, and choosing GPU as your Hardware accelerator.
- Mount the drive in Colab and then unzip the dataset file 'in' a separate folder(other than ../drive) in Colab itself.
- Load your data as numpy array (.npy format) and use flow method instead of flow_from_directory

Furthermore, from the analysis and questions answered above, we can observe that only least amount of buyers will choose to leave reviews after buying online. However, online customers rely on reviews a lot as it helps them make a decision whether to purchase it or not. Other than that, it is also important for customers to leave helpful reviews instead of just ‘Great’ or ‘Bad’. This is because it could help reduce the number of helpful reviews being undiscoverable. Therefore, customers need to write their reviews properly so it could add value to others’ shopping experience.
