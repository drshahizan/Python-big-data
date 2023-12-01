<a href="https://github.com/drshahizan/Python-big-data/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/Python-big-data" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/network/members"><img src="https://img.shields.io/github/forks/drshahizan/Python-big-data" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/Python-big-data" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/issues"><img src="https://img.shields.io/github/issues/drshahizan/Python-big-data" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/Python-big-data/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/Python-big-data?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2FPython-big-data&labelColor=%23d9e3f0&countColor=%23697689&style=flat)

Don't forget to hit the :star: if you like this repo.

# About Us
The information on this Github is part of the materials for the subject High Performance Data Processing (SECP3133). This folder contains general big data information as well as big data case studies using Malaysian datasets. This case study was created by a [Bachelor of Computer Science (Data Engineering)](https://comp.utm.my/bachelor-of-computer-science-data-engineering/), Universiti Teknologi Malaysia student.

<p align="center">
<img src="https://raw.githubusercontent.com/drshahizan/HPDP/main/images/student23241.webp"  height="400" />
</p>

# 📚 Big data processing

**Big data processing** involves the systematic handling and analysis of vast and complex datasets that exceed the capabilities of traditional data processing methods. It encompasses the **storage, retrieval, and manipulation** of massive volumes of information to extract valuable insights. Key steps include **data ingestion**, where large datasets are collected from various sources, and **preprocessing**, involving cleaning and transformation to ensure data quality. Advanced **analytics**, **machine learning**, and **data mining** techniques are then applied to uncover patterns, trends, and correlations within the data. **Big data processing** is integral to informed decision-making, enabling organizations to derive meaningful conclusions from their data, optimize operations, and gain a competitive edge in today's **data-driven landscape**.


## Notes
- [Essential Skills for Big Data Processing with Google Colab: A Beginner's Guide](./materials/beginner-guide.md)
- [Nowogrodzki, A. (2020). Eleven tips for working with large data sets. Nature, 577(7790), 439–440. doi:10.1038/d41586-020-00062-z ]()

### Big Data: Pandas
Big Data processing with **Pandas**, a powerful Python library for data manipulation and analysis, involves implementing strategies to handle large datasets efficiently. Scaling to sizable datasets requires adopting techniques such as processing data in smaller chunks using the '**chunksize**' parameter in Pandas **read_csv** function. This approach facilitates reading and processing large datasets in more manageable portions, preventing memory overload. To further optimize memory usage, it's essential to leverage Pandas' features like data types optimization, using more memory-efficient data types when possible. Additionally, utilizing advanced functionalities like the '**skiprows**' parameter and filtering columns during data import can significantly enhance performance. By mastering these strategies, one can effectively manage and analyze vast datasets in Python with **Pandas**, ensuring both computational efficiency and memory optimization in the face of **Big Data** challenges.

- [Top 10 Python Libraries Data Scientists should know](https://www.edureka.co/blog/python-libraries/)
- [Top 5 Python Libraries For Big Data](https://www.geeksforgeeks.org/top-5-python-libraries-for-big-data/)
- [Python Pandas Dataframe Tutorial for Beginners](https://www.projectpro.io/article/python-pandas-dataframe-tutorials/405)
- [4 strategies how to deal with large datasets in Pandas](https://www.codementor.io/@guidotournois/4-strategies-to-deal-with-large-datasets-using-pandas-qdw3an95k)
- [Scaling to large dataset](https://pandas.pydata.org/docs/user_guide/scale.html)
- [3 ways to deal with large datasets in Python](https://towardsdatascience.com/5-ways-to-deal-with-large-datasets-in-python-9a80786c4182)
- [Reducing Pandas memory usage](https://pythonspeed.com/articles/pandas-load-less-data/)
- [How To Handle Large Datasets in Python With Pandas](https://pythonsimplified.com/how-to-handle-large-datasets-in-python-with-pandas/)
- [Efficient Pandas: Using Chunksize for Large Datasets](https://towardsai.net/p/data-science/efficient-pandas-using-chunksize-for-large-data-sets-c66bf3037f93)
- [How did I convert the 33 GB Dataset into a 3 GB file Using Pandas?](https://medium.com/aatomz-research/how-did-i-convert-the-33-gb-dataset-into-a-3-gb-file-using-pandas-b21d8da205c0)
- [Video: How to work with big data files (5gb+) in Python Pandas!](https://youtu.be/l34l-90UF7U)
- [Loading large datasets in Panda](https://towardsdatascience.com/loading-large-datasets-in-pandas-11bdddd36f7b)
- [Video: How to Read Very Big Files With SQL and Pandas in Python](https://youtu.be/xKMyk4wDHnQ)
- [Scaling to large datasets](https://pandas.pydata.org/pandas-docs/stable/user_guide/scale.html)
- [Video: How to Handle Very Large Datasets in Python Pandas (Tips & Tricks)](https://www.youtube.com/watch?v=E7iwJUzm3Jo&t=2s)
- [Video: 3 Tips to Read Very Large CSV as Pandas Dataframe](https://www.youtube.com/watch?v=GmG3dXhehJc&t=1s)
- [Kaggle: Largest Datasets](https://www.kaggle.com/code/benhamner/competitions-with-largest-datasets)
- [EDA for Amazon books reviews](https://www.kaggle.com/code/mohamedbakhet/eda-for-amazon-books-reviews/notebook)

### Big Data: Alternatives to Pandas for Processing Large Datasets
- [8 Alternatives to Pandas for Processing Large Datasets](https://towardsdatascience.com/8-alternatives-to-pandas-for-processing-large-datasets-928fc927b08c)
- [Tutorial compilation for handling larger datasets](https://www.kaggle.com/competitions/tabular-playground-series-oct-2021/discussion/275712)

#### Modin
- [Modin](https://modin.readthedocs.io/en/stable/)
- [Github Modin](https://github.com/modin-project/modin)
- [How to Speed Up Pandas with Modin](https://towardsdatascience.com/how-to-speed-up-pandas-with-modin-84aa6a87bcdb)
- [Kaggle: Speed up Pandas Workflow with Modin](https://www.kaggle.com/code/lordozvlad/speed-up-pandas-workflow-with-modin/notebook)
- [Video: Do these Pandas Alternatives actually work?](https://youtu.be/LEhMQhCv3Kg)

#### Dask
- [Video - Dask: An Introduction]()
- [Dask | Scale the Python tools you love]()
- [Dask – How to handle large dataframes in python using parallel computing]()
- [Dask (software)]()
- [Parallel Computing with Dask: A Step-by-Step Tutorial]()

#### Datatable
- [DatatableTon](https://github.com/vopani/datatableton)
- [Getting started with Python datatable](https://www.kaggle.com/code/sudalairajkumar/getting-started-with-python-datatable)

### 🎖️ Comparison between libraries
- [Faster Pandas with parallel processing: cuDF vs. Modin](https://towardsdatascience.com/faster-pandas-with-parallel-processing-cudf-vs-modin-f2318c594084)
- [Scaling Interactive Data Science with Modin and Ray](https://youtu.be/ycSf1IbBGWk)
- [Scaling Pandas: Comparing Dask, Ray, Modin, Vaex, and RAPIDS](https://www.datarevenue.com/en-blog/pandas-vs-dask-vs-vaex-vs-modin-vs-rapids-vs-ray)


### Big Data: Case study
- [7 Amazing companies that really get big data](https://www.bernardmarr.com/img/bigdata-case-studybook_final.pdf)
- [Data Science Case Studies: Solved using Python](https://thecleverprogrammer.com/2021/02/19/data-science-case-studies-solved-using-python/)
- [10 Real World Data Science Case Studies Projects with Example](https://www.projectpro.io/article/data-science-case-studies-projects-with-examples-and-solutions/519)
- [Top 8 Data Science Case Studies for Data Science Enthusiasts](https://www.knowledgehut.com/blog/data-science/top-data-science-case-studies)

## Lab
**Pandas**
- [Lab 1: 1,000,000 Sales Records](https://github.com/drshahizan/Python-big-data/blob/main/Pandas/Lab_1_1_million_Sales_Records.ipynb)
- [Lab 2: NYC Yellow Taxi Trip Data](https://github.com/drshahizan/Python-big-data/blob/main/Pandas/Lab_2_3_technique_handle_large_dataset.ipynb)
- [Lab 3: NYC Taxi Trip Duration EDA notebook](https://github.com/drshahizan/Python-big-data/blob/main/Pandas/Lab_3_NYC_EDA.ipynb)
- [Lab 4: Strategies to Deal With Large Datasets Using Pandas](https://github.com/drshahizan/Python-big-data/blob/main/Pandas/Lab_4_NYC_Large_Datasets.ipynb)
- [Lab 5: eCommerce behavior data from multi category store (285 million users)](https://github.com/drshahizan/Python-big-data/blob/main/Pandas/Lab_5_Dataset_285_million_users.ipynb)

**Modin**
- [Lab 1: How to use Modin](https://github.com/drshahizan/Python-big-data/blob/main/Modin/lab_1.ipynb)
- [Lab 2: Speed improvements](https://github.com/drshahizan/Python-big-data/blob/main/Modin/lab_2.ipynb)
- [Lab 3: Not Implemented](https://github.com/drshahizan/Python-big-data/blob/main/Modin/lab_3.ipynb)
- [Lab 4: Experimental Features](https://github.com/drshahizan/Python-big-data/blob/main/Modin/lab_4.ipynb)
- [Lab 5: Modin for Distributed Pandas](https://github.com/drshahizan/Python-big-data/blob/main/Modin/lab_5.ipynb)

**Dask**
- [Lab 1: Introducing Dask](https://github.com/drshahizan/Python-big-data/blob/main/Dask/Lab_1.ipynb)
- [Lab 2: Loading Data Into DataFrames](https://github.com/drshahizan/Python-big-data/blob/main/Dask/Lab_2.ipynb)
- [Lab 3: Introducing Dask DataFrames](https://github.com/drshahizan/Python-big-data/blob/main/Dask/Lab_3.ipynb)
- [Lab 4: Learning Dask With Python Distributed Computing](https://github.com/drshahizan/Python-big-data/blob/main/Dask/Lab_4.ipynb)
- [Lab 5: Parallelize code with dask.delayed](https://github.com/drshahizan/Python-big-data/blob/main/Dask/Lab_5.ipynb)

**Comparison between libraries**
- [Lab: Modin vs Pandas](https://github.com/drshahizan/Python-big-data/blob/main/Modin/lab_6_IntelModin_Vs_Pandas.ipynb)
- [Lab: Large datasets (100MB to 1TB+) Pandas_Modin_Dask_Vaex](https://github.com/drshahizan/Python-big-data/blob/main/Pandas/Lab_6_Pandas_Modin_Dask_Vaex.ipynb)

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/Python_EDA/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

