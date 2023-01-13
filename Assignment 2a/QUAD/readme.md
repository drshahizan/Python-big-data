    
# Introduction to Polars 🐻‍❄️

<br>
 <p align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTKH6i3lJ9tW7bna90G-1SO7QB__e3ri_8MCw&usqp=CAU"/>
 </p>
</br>

- **Polars** is both lazy and semi-lazy. It allows you to accomplish most of your work eagerly, similar to Pandas, but it also provides a sophisticated expression syntax that will be optimised and processed within the query engine.

Polars' purpose is to deliver a lightning-fast DataFrame library that makes use of all available cores on your machine. Unlike dask, which attempts to parallelize existing single-threaded libraries such as NumPy and Pandas, Polars is intended from the ground up for parallelization of queries on DataFrames.

Polars goes to great lengths to:

1.   Reduce redundant copies
2.   Traverse memory cache efficiently
3.   Minimize contention in parallelism


For more information about Polars, you can view from [Polars](https://pola-rs.github.io/polars-book/user-guide/index.html).