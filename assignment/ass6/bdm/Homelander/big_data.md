# Homelander - Assignment 6 

<a target="_blank" href="https://github.com/drshahizan/Python-big-data/blob/main/assignment/ass6/bdm/Homelander/Homelander_BDM_Assignment6.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: |
| Pang Chern Hong            |MCS231006      |
| Nian Cong              |MCS231007      |

**Five strategies to handle the big dataset**

1. Load Less Data
2. Use Chunking
3. Optimize Data Types
4. Sampling
5. Parallelize with Dask

**Processing time and Memory Usage:**
| Strategy | Time (in seconds) | Memory Usage (in Miga Byte) | Analysis|      
|----------|------|--------------|---------|
|Traditional(pandas)|22.1|732.4|Pandas use single core for data manipulation, it require more time for processing.|
|Load Less Data|25.27|709.5|If we only load certain data, eliminating some coulumns, definitely the memory usage will be dropped, but if we drop only few coulumns, the processing time will take longer.|
|Optimize Data Types|2.32|452|The time is only counted for the optimizing the data types, not including the loading of dataset, it significantly reduce the memory usage and save time in long run.|
|Sampling (percentage_sample)|0.98|75.5|Uses a percentage-based sample, which reduces memory usage and greatly improves processing time.|
|Parallelize with Dask|4.183|732.5|Utilizes Dask for parallel processing, resulting in a substantial reduction time but same memory usage.|
|Chunking|24.23|1385.9|We see a higher processing time and memory usage because we also perform calculation in chunking, anyway it definitely can save memory usage and processing time becase the dataset is separated and processed with higher speed.|

**Advantages and Disadvantages:**
1. Pandas: 

-Advantages: Very convenient and commonly used, can find many solutions in internet.

-Disadvantages: Highly time and memory usage consuming especially when dataset is large.

2. Load Less Data:

-Advantages: Save processing time and memory usage, and we able analyze the more important information.

-Disadvantages: Some underlying important data maybe not included in the analysis and causing information loss.

3. Optimize Data Types:

-Advantages: Greatly save memory usage and processing time in long run.

-Disadvantages: Some datatypes maybe went wrong and causing the further analysis not feasible, and if dataset is small this will add some additionaly processing time and add-up the risk.

4. Sampling:

-Advantages: Significantly save processing time and memory usage, the right technique can make the dataset posses certain representability.

-Disadvantages: Some important information maybe lost, especially some rare and important event happened and we failed to capture it.

5. Parallelize with Dask:

-Advantages: Process the dataset parallely and we able to function all the cores of our laptop or computer, and so we can save processing time in long run.

-Disadvantages: Because the cores are not really function that systematically, it will add-up some learning cost in long run.

6. Chunking:

-Advantages: Process the dataset in many separated pieces, then combined to form the results to reduce the memory usage.

-Disadvantages: Processing time will be higher, and we need to decide an appropriate chunking size before we process the data.

**Conclusion**

In Summary, in this assignment we found that there are various technique can be used when dealing with a large dataset that are larger than 1 GB in order to avoid cpu crash. Pandas is very useful but since it only utilize one of the cores, it is not fully exploring the capability of the CPU or GPU, in results of high processing time and also the memory usage. Besides that, if there are many unnecessary features in the dataset, we can eliminate them in order to reduce processing time and memory usage. If we want to keep them but at a lower computational cost, we can use sampling based on percentage and the selection is random so that we can select the data distributed in the dataset to make the sample representative of the dataset.We can also optimize the data types so that the data can be stored in a types that required lesser memory usage, and thus we also save processing time in long run and we are not compromised to eliminate any of the data. Last but not least, we can process the data through chunking, so that we separate the dataset and process it with higher efficient, then the processed data is combined to form the results in order to save the memory usage but it will inevitably increase the processing time. We always need to be smart to select the strategies and choose which aspects to compromize in order to achieve our goals.

