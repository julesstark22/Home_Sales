# Home_Sales

This code demonstrates the use of PySpark to perform various operations on a dataset containing home sales information. Below is a step-by-step explanation of the code and its functionality:

Import the necessary packages and initialize Spark:

The findspark package is imported and initialized to locate the Spark installation.
The pyspark.sql package is imported to work with Spark SQL.
The time package is imported to measure the runtime of certain operations.
Create a SparkSession:

A SparkSession is created using SparkSession.builder with the application name set to "SparkSQL".
The getOrCreate() method ensures that an existing SparkSession is used or a new one is created.
Read data from an AWS S3 bucket into a DataFrame:

The URL of the CSV file containing home sales data is assigned to the url variable.
The file is added to Spark using spark.sparkContext.addFile(url).
The CSV file is then read into a DataFrame using spark.read.csv with options for header and schema inference.
Create a temporary view of the DataFrame:

The DataFrame is registered as a temporary view named "my_table" using createOrReplaceTempView().
The view allows executing SQL queries on the DataFrame.
Perform a test operation on the temporary view:

A SQL query is executed on the temporary view using spark.sql() to select all records.
The result is printed using .show().
Calculate the average price for a four-bedroom house sold in each year:

A SQL query is executed on the temporary view to calculate the average price for four-bedroom houses.
The result is rounded to two decimal places and ordered by the year.
The result is printed using .show().
Calculate the average price of homes built in each year with 3 bedrooms and 3 bathrooms:

A SQL query is executed on the temporary view to calculate the average price of homes with specific criteria.
The result is rounded to two decimal places and ordered by the year.
The result is printed using .show().
Calculate the average price of homes built in each year with 3 bedrooms, 3 bathrooms, 2 floors, and at least 2000 square feet:

A SQL query is executed on the temporary view to calculate the average price of homes with specific criteria.
The result is rounded to two decimal places and ordered by the year.
The result is printed using .show().
Measure the runtime for a query filtering homes with a price greater than or equal to $350,000:

The start time is recorded using time.time().
A SQL query is executed on the temporary view to calculate the average price of homes with a specific price condition.
The result is printed using .show().
The elapsed time is calculated and printed using time.time() - start_time.
Cache the temporary table "my_table":

The temporary table is cached in memory using spark.catalog.cacheTable().
Check if the table is cached:

The cached status of the table is checked using spark.catalog.isCached().
Run a query on the cached data:

The start time is recorded using time.time().
A SQL query is executed on the cached DataFrame to filter homes with a specific price condition.
The result is printed using .show().
The elapsed time is calculated and printed using time.time() - start_time.
Partition the formatted Parquet home sales data by the "date_built" field:

The output path for the partitioned Parquet data is specified.
The DataFrame is written in Parquet format with partitioning based on the "date_built" field.
Read the formatted Parquet data:

The path to the formatted Parquet data is specified.
The Parquet data is read into a DataFrame using spark.read.parquet().
Create a temporary table for the Parquet data:

The Parquet DataFrame is registered as a temporary view named "parquet_table" using createOrReplaceTempView().
Run a query on the Parquet data to filter homes with a specific price condition:

The start time is recorded using time.time().
A SQL query is executed on the Parquet DataFrame to filter homes with a specific price condition.
The result is printed using .show().
The elapsed time is calculated and stored in the parquet_runtime variable.
Print the runtime comparison between the cached and Parquet versions:

The runtime for the Parquet query is printed using parquet_runtime.
The runtime for the cached query is not available (missing code).
Uncache the temporary table "my_table":

The temporary table is uncached from memory using spark.catalog.uncacheTable().
Check if the temporary table is no longer cached:

The cached status of the table is checked using spark.catalog.isCached().
The result is printed indicating whether the table is still cached or not.
Please make sure to update the paths and filenames as necessary before running the code.
