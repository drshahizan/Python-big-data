<h1 align="center">
  Project : Amazon Books Review
  <br>
</h1>
<h1 align="center">
  <img src="https://user-images.githubusercontent.com/97009588/215264901-4e1b869c-a5b3-466b-a9ab-b6a714d51842.jpg">
  <br>
</h1>
<br>
<h2 align="center">
  Group Name
  <br>
</h2>

<p align="center">
  <a>SDS</a><br>
</p>

<h2 align="center">
  Group Members
  <br>
</h2>

<p align="center">
  <a>ONG HAN WAH</a><br>
  <a>GOO YE JUI</a><br>
  <a>MAIZATUL AFRINA SAFIAH BINTI SAIFUL AZWAN</a><br>
</p>

---
# **Introduction**
This project will be analysed by using 3 different libraries which are **Pandas, Polars and Koalas.** This is to find out which library has the highest efficiency among them as well as finding answers for our inquiries.

| Library Used | Pandas | Polars | Koalas |
| ------------- | ------------- | ------------- | ------------- |
| Library Image | ![68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f6d61782f3634302f312a307170565a7735714b6e636f4642594a6634446c70412e77656270](https://user-images.githubusercontent.com/97009588/215579512-ee542ed6-4dcb-46ce-991d-e29162de78a5.jpg) | <img src='https://raw.githubusercontent.com/pola-rs/polars-static/master/web/polars-logo-python.svg' height=200px width=200px alt='Polars'> | ![koalas-logo-docs](https://user-images.githubusercontent.com/97009588/215579582-6783868e-58c6-44fb-8afe-86369aa5b43b.png) |
| Installation method | <code>!import pandas as pd</code> | <code>!pip install polars</code> | <code>!pip install koalas </code>

---
# **About Dataset**

The dataset was obtained from Kaggle titled Amazon Book Reviews from https://www.kaggle.com/datasets/mohamedbakhet/amazon-books-reviews .This dataset contain the feedback about 3M user on 212404 unique books. It contains product reviews and metadata from Amazon, including 142.8 million reviews spanning May 1996 - July 2014 and this file has these attributes.

<table align="center">
  <tr>
    <th>Columns</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>Id</th>
    <th>The Id of the book</th>
  </tr>
  <tr>
    <th>Title</th>
    <th>The title of the book</th>
  </tr>
  <tr>
    <th>Price</th>
    <th>The price of the book</th>
  </tr>
  <tr>
    <th>User_id</th>
    <th>Id of the user</th>
  </tr>
  <tr>
    <th>profileName</th>
    <th>Name of the user</th>
  </tr>
  <tr>
    <th>review/helpfulness</th>
    <th>Helpfulness rating</th>
  </tr>
  <tr>
    <th>review/score</th>
    <th>Book's rating</th>
  </tr>
  <tr>
    <th>review/time</th>
    <th>Time given for review</th>
  </tr>
  <tr>
    <th>review/summary</th>
    <th>Review summary</th>
  </tr>
  <tr>
    <th>review/text</th>
    <th>Full text review</th>
  </tr>
</table>

---

# **Pandas vs Polars vs Koalas**

- Perhaps the major difference of Polars from Pandas and Koalas is that **Polars does not have an index**. Polars also allow creating or assigning multiple columns in one statement using `with_columns` method.

- Pandas and Koalas use the same function since Koalas implements the Pandas API on top of Apache Spark. Whereas, Polars has some common function and similar function but different name.

- In term of visualization, Pandas dataframe has a `plot()` method which return a **matplotlib** graph while Koalas `plot()` returns **plotly** graph by default. Polars on the other hand does not provide such method.

![performance-comparison](https://user-images.githubusercontent.com/69034742/215641725-23b0ed2d-d79e-47c2-88d0-9a5b3b3d4a5a.png)

The graph above show the time taken in seconds for the three libraries to run the functions. From the graph, it can be seen that:

- **Pandas** is the fastest in **head** and **sample** while it is the slowest in selecting columns, dropping duplicates and dropping nulls.

- **Polars** is the fastest in **read csv, info, shape, select columns** and **count null** but relatively slower in joining dataframe.

- **Koalas** is the fastest in **joining dataframe, dropping duplicates** and **dropping nulls** but extremely slow in head, info, shape and count nulls compared to Pandas and Polars.

---

# **Conclusion**

> From all the books from Amazon that have been reviewed, we can conclude that **Fiction** category has the highest amount of books followed by **Juvenile Fiction**. Meanwhile for publishers, the publisher that published the most amount of books is **Penguin** followed by **Simon and Schuster**. Other than that we discover that the authors that has written the highest amount of books is **J.R.R. Tolkien** followed by **Jane Austen** and from this we also find out  the most frequent words used in review for positive rated(rating>3.0) books is **"book"**.

> Throughout this case study project where we investigate which library is the most effiecient among the 3 libraries, Pandas, Polars and Koalas, **Polars** turns out to be the library that has the highest efficiency compared to other 2 libraries. 
