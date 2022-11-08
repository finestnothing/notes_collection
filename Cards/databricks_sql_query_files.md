up:: [[databricks_sql]], [[spark]]

# databricks_sql_query_files

Created: 20221101 17:54
Modified: 20221101 17:54

- [[#Self Describing Formats|Self Describing Formats]]
	- [[#Self Describing Formats#Querying from JSON|Querying from JSON]]
	- [[#Self Describing Formats#Creating Views|Creating Views]]
	- [[#Self Describing Formats#Creating CTEs|Creating CTEs]]
	- [[#Self Describing Formats#Text Files|Text Files]]
	- [[#Self Describing Formats#Raw Bytes and Metadata|Raw Bytes and Metadata]]
- [[#Other File Formats|Other File Formats]]
	- [[#Other File Formats#Problem|Problem]]
	- [[#Other File Formats#Solution|Solution]]
- [[#SQL Databases as data source|SQL Databases as data source]]

## Self Describing Formats

### Querying From JSON

```sql
-- SQL cmd block
SELECT * FROM json.'${path_to_json.json}'
```

- Gets all data from a json file
- SQL command block
- If this command is ran to a directory instead of specific .json file and all files in the directory have the same schema and format, all files will be combined into one output
	- Like how parquet files are written and read

### Creating Views

```sql
-- SQL cmd block
CREATE OR REPLACE TEMP VIEW tmp AS (
	SELECT * FROM json.'${path_to_json.json}'
)

SELECT * FROM tmp
```

- Can create views
- TEMP only gets created for the current spark session
	- Only for notebook, job, etc

### Creating CTEs

```sql
-- SQL cmd block
WITH cte_tmp AS (
	SELECT * FROM json.'${path_to_json.json}'
)
SELECT * FROM cte_tmp
```

- CTE Tables can be defined as well, work similar to views but are more human readable and short-lived
- Only last for the current cell execution, not accessible from other cells

### Text Files

```sql
-- SQL cmd block
SELECT * FROM text.'${path_to_txt.txt}'
```

- When it specifies a text file, each line becomes a row
- Only returns a single column called Value, grabbed directly from the file
- Great for when data sources are prone to corruption
	- Allows custom text parsing to extract values

### Raw Bytes and Metadata

```sql
-- SQL cmd block
SELECT * FROM binaryFile.'${path_to_dir}'
```

- Extracts metadata about a file
- Creates the following fields
	- path
	- modificationTime
	- length
	- content

## Other File Formats

### Problem

```sql
-- SQL cmd block
SELECT * FROM csv.'${path_to_csv.csv}'
```

- This does not work well
- It will grab the header row as a row itself rather than the field names
- Doesn't support non-comma delineated files
- Can truncate overly long entries

### Solution

```sql
CREATE TABLE tmp (col_name1 col_type1,...)
USING data_source
OPTIONS(key1 = val1, key2 = val2, ...)
LOCATION = path
```

- Basic commands to extract data from an external data source

```sql
-- SQL cmd block
CREATE TABLE IF NOT EXISTS tmp_csv
	(order_id LONG, ...)
USING CSV
OPTIONS(
	header = "true",
	delimiter = "|"
)
LOCATION "${DA.paths.tmp_csv}"
```

- Creates a table from csv with | as delimiter, reads a header, and specifies data types
- No data is actually moved yet, it won't be read until we try to read the data
- Note: make sure column order never changes when reading from these, or field name and types will need to be manually changed

```sql
-- SQL cmd block
DESCRIBE EXTENDED tmp_csv
```

- Will show all metadata for the table

```sql
-- SQL cmd block
REFRESH TABLE tmp_csv
```

- Spark may query an older cached version of data when accessing external data, which is why it's best to use DLT's when possible
	- This happens since spark tries to speed up repeated queries rather than refetching every time
- Running the command above will refresh the data and get the newest version of it

## SQL Databases as Data Source

```sql
CREATE TABLE {table_name}
USING JDBC
OPTIONS(
	url = "{url}:{port}",
	dbtable = "{database}.{table}",
	user = "{user_name}",
	password = "{user_password}"
)
```

- This defines access to a SQL database
- We can now query the table like it's local
- There are two ways to access these
	- Cache the entire source file to databricks
	- Push the query to the SQL database and only get the result of the query back
