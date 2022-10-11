# delta_live_table
Created: 2022-09-29 17:26

- User defined functions define how the data is setup in the [[data_lake_house]]
	- Is how the structure of the data is defined
	- Results are the [[data_lake_house_silver_layer]] and [[data_lake_house_gold_layer]]s
- Defines any transformations, fields, and aliases for each layer
- While working on them nothing changes, but then changes are deployed when the [[databricks_pipeline]] is started up