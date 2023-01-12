<img src="https://www.google.com/imgres?imgurl=https%3A%2F%2Fraw.githubusercontent.com%2Fpola-rs%2Fpolars-static%2Fmaster%2Flogos%2Fpolars_github_logo_rect_dark_name.svg&imgrefurl=https%3A%2F%2Fgithub.com%2Fpola-rs%2Fpolars&tbnid=MCfyT2yHsQwe4M&vet=12ahUKEwjDyITylcL8AhUVMbcAHd2LDDIQMygFegUIARC1AQ..i&docid=iBJXAWbzEP6oHM&w=1965&h=454&q=polars%20python%20image&ved=2ahUKEwjDyITylcL8AhUVMbcAHd2LDDIQMygFegUIARC1AQ"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
     
# Introduction to Polars 🐻‍❄️

- **Polars** is both lazy and semi-lazy. It allows you to accomplish most of your work eagerly, similar to Pandas, but it also provides a sophisticated expression syntax that will be optimised and processed within the query engine.

Polars' purpose is to deliver a lightning-fast DataFrame library that makes use of all available cores on your machine. Unlike dask, which attempts to parallelize existing single-threaded libraries such as NumPy and Pandas, Polars is intended from the ground up for parallelization of queries on DataFrames.

Polars goes to great lengths to:

1.   Reduce redundant copies
2.   Traverse memory cache efficiently
3.   Minimize contention in parallelism


For more information about Polars, you can view from [Polars](https://pola-rs.github.io/polars-book/user-guide/index.html).
