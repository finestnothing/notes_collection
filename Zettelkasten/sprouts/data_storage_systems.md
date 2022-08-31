# data_storage_systems
Created: 2022-08-31 12:12
#zettel/pending 

## Data Warehouses
- [[data_storage_systems#^db3388|Reference 1]]
- Designed and made for data that isn't changing often
	- New data isn't being added or changed, only adding to existing
- Great for running multiple queries on them since they are not designed to change
- Often used for reporting, too rigid for a lot of other work

## Data Lake
- [[data_storage_systems#^db3388|Reference 1]]
- Accepts any format or kind of data, all lumped together like a bucket
- Can accept structured data, but doesn't keep the data in itself structured
- Used for ai/ml since any format of data will work without much configuration other then initializing the lake

## Data lake house
- [[data_storage_systems#^db3388|Reference 1]], [[data_storage_systems#^575f58|Reference 3]]
- Specific to databricks
- Flexible but also standardized
- Indexed for quick access
- Reliable due to using ACID to ensure data isn't lost and changes are tracked
	- Created new seedling for ACID [[202208311348]]
- Follows GDPR and HIPAA guidelines by default in databricks
- Open source formats
- Supports real time data acquisition and processing
- Addresses main challenges in data industry
	- Large volumes of data
	- Varying data types and formats
	- Data streaming
	- Tracking changes to data and formatting

## Delta Lakes and Delta Live Tables
- [[data_storage_systems#^43f217|Reference 2]]
- Databricks delta lakes
	- Storage format specific to databricks data lakehouses
- Delta Live Tables
	- Is how the data is setup in the lakehouse itself
		- Gives structure to it
	- Defines any transformations, fields, aliases, etc in layers
	- When pipeline is being built, it uses the delta live tables to setup all of the data for access
- Data Pipelines in data lake house
	- Should follow three-tiered approach
		- Bronze Layer - raw data directly mirrored from source, no transformations occur
		- Silver layer - clean data from bronze layer (trim spaces, transform basic fields, aliasing, etc)
		- Fold layer - reporting-ready layer. Changes often as different needs arise for different reports

## Databricks SQL
-[[data_storage_systems#^dd9faa|Reference 4]]
- Built natively into databricks, not pure sql but close
- Has dashboard compliance built in, including scheduling queries to populate dashboards
- Dashboards
	- textboxes
	- Widgets to show data
	- Annotate with markdown
- Connect external BI tools
	- Able to access the databases in databricks using external tools

## References
1. [[202208151619]] ^db3388
2. [[202208151627]] ^43f217
3. [[202208300931]] ^575f58
4. [[202208301002]] ^dd9faa