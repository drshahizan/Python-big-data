## 🚀 Case Study 2 : Alternatives to Pandas for Processing Large Datasets

Pandas library has became the de facto library for data manipulation in python and is widely used by data scientist and analyst. However, there are times when the dataset is too large and Pandas may run into memory errors. Here are 8 alternatives to Pandas for dealing with large datasets. For each alternative library, we will examine how to load data from CSV and perform a simple groupby operation. Fortunately many of these libraries have similar syntax as Pandas hence making the learning curve less steep.
1. Data Table
2. Polars
3. Vaex
4. Pyspark
5. Koalas
6. cuDF
7. Dask
8. Modin

## 🌟 Case Study 2b: Solutions

| Team | Title | Colab |  GitHub |
| ----- | ----- | ------ | ------ | 
| 1 | Pandas vs DataTable | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 2 | Pandas vs Polars | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 3 | Pandas vs Vaex | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 4 | Pandas vs Pyspark | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://colab.research.google.com/drive/1Ta8kvxB4NlMHO204WZtrnfnVToPVr2J5?usp=sharing) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://github.com/drshahizan/Python_EDA/tree/main/Malaysia%20EDA/Boboiboy) |
| 5 | Pandas vs Koalas | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 6 | Pandas vs cuDF | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 7 | Pandas vs DataTable | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 8 | Pandas vs Polars | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 9 | Pandas vs Vaex | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 10 | Pandas vs Pyspark | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |
| 11 | Pandas vs Koalas | [![Open in Colab](https://img.shields.io/static/v1?label=&message=Open%20in%20Colab&labelColor=grey&color=blue&logo=google-colab)](https://) | [![Open in GitHub](https://img.shields.io/static/v1?label=&message=Open%20in%20GitHub&labelColor=grey&color=blue&logo=github)](https://) |


## 🏥 Case Study 2 : Koalas Vs Pandas Library on Health Insurance Marketplace Dataset

![image](https://user-images.githubusercontent.com/99240177/212251329-77469daa-6e5a-464d-915d-a8cb4be0c674.png)

  
## Group Members

<table width = 700>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>AHMAD MUHAIMIN BIN AHMAD HAMBALI</th>
    <th>A20EC0006</th>
  </tr>
  <tr>
    <th>NAYLI NABIHAH BINTI JASNI</th>
    <th>A20EC0105</th>
  </tr>
    <tr>
    <th>SAKINAH AL’IZZAH BINTI MOHD ASRI</th>
    <th>A20EC0142</th>
  </tr>
    <tr>
    <th>LEE JIA XIAN</th>
    <th>A20EC0200</th>
  </tr>
</table> 

<table>

  <tr>

    <th>Name</th>

    <th>Matric</th>

  </tr>

  <tr>

    <th>AHMAD MUHAIMIN BIN AHMAD HAMBALI</th>

    <th>A20EC0006</th>

  </tr>

  <tr>

    <th>NAYLI NABIHAH BINTI JASNI</th>

    <th>A20EC0105</th>

  </tr>

    <tr>

    <th>SAKINAH AL’IZZAH BINTI MOHD ASRI</th>

    <th>A20EC0142</th>

  </tr>

    <tr>

    <th>LEE JIA XIAN</th>

    <th>A20EC0200</th>

  </tr>

</table>


Koalas is a data science library that implements the pandas APIs on top of Apache Spark so that data scientists can use their favourite APIs on datasets of any size.The file will compare koalas and pandas to see which libraries are more efficient to use in the health insurance marketplace dataset. The following operations and visualisations will be used to perform the comparison:

  ● Comparison between read CSV

  ● Comparison between mean from one column

  ● Comparison between bar chart

  ● Comparison between counting of null values 

  ● Comparison between calculation of numerical data

  ● Comparison between histogram

## Dataset

The Health Insurance Marketplace Public Use Files contain information on health and dental plans available through the US Health Insurance Marketplace to individuals and small businesses. We chose rate.csv as our analysis datase from the combined csv file because it has the biggest file size (1.97 GB).

The dataset can be downloaded from Kaggle: <a href="https://www.kaggle.com/datasets/hhs/health-insurance-marketplace?select=Rate.csv">Health Insurance Marketplace from Rate dataset</a>
