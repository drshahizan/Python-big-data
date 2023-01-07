<h1>Data Table as an alternative to Pandas</h1>

![DataTable](https://datatable.readthedocs.io/en/latest/_static/py_datatable_logo.png)

Python package datatable was inspired from its counterpart R package data.table. It was developped with the aim to analyse BigData efficiently. Following is about datatable package.(Taken from datatable github page)

The set of features that we want to implement with datatable is at least the following:

- Column-oriented data storage.

- Native-C implementation for all datatypes, including strings. Packages such as pandas and numpy already do that for numeric columns, but not for strings.

- Support for date-time and categorical types. Object type is also supported, but promotion into object discouraged.

- All types should support null values, with as little overhead as possible.

- Data should be stored on disk in the same format as in memory. This will allow us to memory-map data on disk and work on out-of-memory datasets transparently.

- Work with memory-mapped datasets to avoid loading into memory more data than necessary for each particular operation.

- Fast data reading from CSV and other formats.

- Multi-threaded data processing: time-consuming operations should attempt to utilize all cores for maximum efficiency.

- Efficient algorithms for sorting/grouping/joining.

- Expressive query syntax (similar to data.table).

- LLVM-based lazy computation for complex queries (code generated, compiled and executed on-the-fly).
LLVM-based user-defined functions.

- Minimal amount of data copying, copy-on-write semantics for shared data.

- Use "rowindex" views in filtering/sorting/grouping/joining operators to avoid unnecessary data copying.

- Interoperability with pandas / numpy / pure python: the users should have the ability to convert to another data-processing framework with ease.

- Restrictions: Python 3.5+, 64-bit systems only.

<hr>

<h1>Installation</h1>
`!pip install datatable`
