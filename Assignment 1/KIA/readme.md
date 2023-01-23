# US Road Construction and Closures 2016-2021 Analysis.

# Group Members:

1.   Afif Hazmie Arsyad bin Agus (A20EC0176)
2.   Muhammad Imran Hakimi bin Mohd Shukri (A20EC0213)

## Group Members
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Muhammad Imran Hakimi Bin Mohd Shukri </th>
    <th>A20EC0213</th>
  </tr>
  <tr>
    <th>Afif Hazmie Arsyad Bin Agus</th>
    <th>A20EC0176</th>
  </tr>
</table>

The dataset is about the US Road Construction and Closures 2016-2021. It is taken from Kaggle and we are going to analyse the dataset to see the performance of the construction cases throughout the year. For this analysis, we will be using the Python language with the help of libraries such as mathplotlib, pandas, seaborn, numpy and much more. Since the dataset that we used are more than 1GB, we have to use chunking and sampling in order to have a smooth and faster runtime. 

## What we do:
- Importing data from Kaggle
- Do some data preparation and cleaning
- Chunking and Sampling
- Visualization on the dataset. 

### Dataset Description
[`US_Constructions_Dec21.csv `]: State results By candidate 

1) `ID`: This is a unique identifier of construction record.
2) `Severity`: Shows the severity of the construction, an integer between 1 and 4, where 1 indicates the least impact on traffic (i.e., short delay)
3) `Start_Time`: Shows start time of construction in local time zone.
3) `End_Time`: Shows end time of construction in local time zone. 
4) `Start_Lat`: Shows latitude in GPS coordinate of the start point.
5) `Start_Lng`: Shows longitude in GPS coordinate of the start point.
6) `End_Lat`: Shows latitude in GPS coordinate of the end point.
7) `End_Lng`: Shows longitude in GPS coordinate of the end point.
8) `Distance(mi)`: The length of the road extent affected by the construction.
9) `Description`: Shows a human provided description of the event.


