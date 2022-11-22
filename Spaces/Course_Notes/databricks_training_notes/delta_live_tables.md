# Data Streaming

	
- Streaming live tables are a great way to begin the streaming process
- Databricks auto loader
	- Built in databricks tool for data streaming
	- Can connect to other data sources to update Streaming Live Tables
	- Still need to look into this more on best cases to use
	- Optimized incremental data loading and streaming

# Python and SQL DLT's

## Basic DLT's

```
import dlt
@dlt.table
def order_bronze():
	return({spark dataframe query})
```

```
create or refresh live table order_bronze
tblproperties (
	'pipelines.autoOptimize.zOrderCols' = 'case_id'
) as (
	{sql query}
)
```

This is the basic syntax for creating a delta live table

## Adding Properties to DLT's

```
@dlt.table(
comment = "Append only orders with valid timestamp",
	table_properties = {"quality": "silver"}
)
```

```
create or refresh live table {table name}
comment "Append only orders with valid timestamp"
```

## Streaming DLT's

```
import dlt
import pyspark.sql.functions as f

@dlt.table
def orders_bronze():
	return(
		spark.readStream
		.format("cloudFiles")
		.option("cloudFiles.format", "json")
		.option("cloudFiles.inferColumnTypes", "true")
		.load(f"{source}/orders")
		.select(
			f.current_timestamp().alias("processing_time"),
				f.input_file_name().alias("source_file"),
				"*"
		  )
)
```

```
create or refresh streaming live table customers_bronze
comment "Raw data from customers CDC feed"
as select current_timestamp() processing_time, input_file_name() source_file, *
from cloud_files("${source}/customers", "json")
```

Both of these utilize Databricks auto loader

## Quality Enforcement in DLT's

```
@dlt.table
@dlt.expect_or_fail("valid_id", "customer_id is not null")
@dlt.expect_or_drop("valid_operation", "operation is not null")
@dlt.expect("valid_name", "name is not null or operation = 'DELETE'")
@dlt.expect(
	"valid_address",
		"""
	  (
		address is not null
		  and city is not null
		  and state is not null
		  and zip_code is not null
	  ) or operation = "DELETE"
	  """
)
```

```
  create streaming live table customers_bronze_clean
  (
	constraint valid_id expect (customer_id is not null) on violation fail update,
	constraint valid_operation expect (operation is not null) on violation drop row,
	constraint valid_name expect (name is not null or operation = "DELETE"),
	constraint valid_address expect(
		(
		address is not null
		and city is not null
		and state is not null
		and zip_code is not null
	  ) or operation = "DELETE"
	),
	constraint valid_email expect(
		rlike(email, '^([a-zA-Z0-9_\\-\\.]+)@([a-zA-Z0-9_\\-\\.]+).([a-zA-Z0-9_\\-\\.]+)')
	  or operation = "DELETE"
	) on violation drop row
  )
  as select *
  from stream(live.customers_bronze)
```

Both of these implement the same constraint checking
This is useful for only getting good data

### Constraints

- `fail update`
	- Transaction fails, does not get updated
	- Transaction fails if `customer_id` is null
- `drop row`
	- Drop any records matching the condition
	- Drops any rows where `operation` is null
	- Drops any rows where `email` does not fit the regex pattern of _@._.*
- No `on violation` statement
	- The issue is logged, but the data still gets updated

## Using `Apply Changes Into` for Incremental Loads

```
dlt.create_target_table(
	name = "customers_silver"
)

dlt.apply_changes(
	target = "customers_silver",
	source = "customers_bronze_clean",
	keys = ["customer_id"],
	sequence_by = f.col("timestamp"),
	apply_as_deletes = f.expr("operation = 'Delete'")
	except_column_list = ["operation", "source_file", "_rescued_data"]
)
```

```
create or refresh streaming live table customers_silver

apply changes into live.customers_silver
	from stream(live.customers_bronze_clean)
	keys (customer_id)
	apply as delete when operation = "DELETE"
	SEQUENCE by timestamp
	columns * except (operation, source_file, _recursed_data)
```

- Both code blocks create a new streaming live table called customers_silver
- They then apply changes into the table
	- Databricks keeps track of every change
	- First "apply_changes" will load all of the data in
	- After the first load, only changes will be moved
		- Any updates, additions, and deletions
		- Does not move all of the data over again
- We also specify that we use customer_id as the primary key
	- Primary key is necessary, multiple can be used

# Delta Live Views

		
- Live views in python and databricks follow the same format as tables
	- Only difference is "view" instead of "table
		- `@dlt.view`
		- `create or refresh live view`
- Views do NOT persist on the disk, they rely on their source tables to continue existing
- Views are not accessible outside of the pipeline and do not persist in the metastore

# Python DLT's

- DLT's can be defined in SQL or Python
- At work, we currently use SQL
	- I tried a python DLT on 20221118 but it refused to work

## Code Blocks

```
import dlt
```

- This may require you to run `pip install dlt` before using
- DLT is a decorator for python

# Streaming Versus Live DLT's

	
- Live tables
	- Basically a persistent view in a data lakehouse format
		- It actually stores and caches the data that is a part of it
			- A view doesn't cache anything, each time you call the view it goes to it's sources
	- If on a triggered pipeline, the data only updates whenever the pipeline is triggered
		- Usually a manual run, but it can be scheduled too
		- This is a tradeoff
			- It is a lower cost and processing time since it runs once and shuts down
			- The data is only as updated as the last pipeline runtime
- Streaming Live Tables
	- It is also persistent
	- The main difference between this and Live tables is that this one stream ingests data
		- Any changes that occur in the source data/table/files/etc is the only thing that gets updated rather than pulling in the entire source each time
		- It updates incrementally so append-only is best, but it can still handle updates and deletes
	- Can have real-time data since it triggers the data update whenever it detects that the source updated
		- This works well for chaining together streaming live tables and views
- Sources
	- DE 4.1.1 Orders Pipeline (python) archive/inbox
	- DE 4.1.1 - Orders Pipeline archive/inbox
	- DE 4.1.2 Customers Pipeline archive/inbox
	- DE 4.1.2 - Customers Pipeline archive/inbox
