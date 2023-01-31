<h1 align="center">
  <img src="https://user-images.githubusercontent.com/97009588/211754866-b88f8f71-dbe1-4735-9e5d-5890d747d211.png">
  <br>
</h1>

<h1 align="center">
  Koalas vs Pandas on NYC Yellow Taxi Trip Dataset
  <br>
</h1>

<h2 align="center">
  Group Members
  <br>
</h2>

<p align="center">
  <a>ONG HAN WAH</a><br>
  <a>GOO YE JUI</a><br>
  <a>MAIZATUL AFRINA SAFIAH BINTI SAIFUL AZWAN</a><br>
</p>

<h2 align="center">
  KOALAS
  <br>
</h2>

<p align="center">
  <a>The Koalas project makes data scientists more productive when interacting with big data, by implementing the pandas DataFrame API on top of Apache Spark.

  With this package, you can:

Be immediately productive with Spark, with no learning curve, if you are already familiar with pandas.

Have a single codebase that works both with pandas (tests, smaller datasets) and with Spark (distributed datasets).
</p> 

## Comparison between koalas vs pandas:
| Methods | Koalas | Pandas |
| --- | --- | --- |
| **Read csv**| 1min 40s | 49.1s  |
| **Head** | 263ms | 395 µs |
| **Tail** | 2min 7s | 231 µs |
| **Describe Dataset** | 5min 10s |  21.2s |
| **Sum Operation** | 24.3 s |  36.3 ms |
| **Aggregate** | 1.73 s |  3.95 s |
| **Grouping** | 955 ms |  3.85 s |
| **isNull** | 1min 7s |  2.46 s |
| **fillNa** | 1.48 s | 4.64 s |
| **dropNa** | 885 ms |  3.76 s |

![comparison](https://user-images.githubusercontent.com/69034742/215643655-80d66e4b-27ab-47a0-99c8-c9c3da24ec8e.png)

## Conclusion
Pandas is more optimized for performance for most use cases compared to koalas. Pandas is 2.03x faster than Koalas in reading a dataset. Koalas only performs better than Pandas in Aggregating(2.28x faster) and Grouping(4.03x faster). 
