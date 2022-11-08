up:: [[databricks_moc]]
tags:: #databricks

# data_lake_house

- Specific data storage type made by [[databricks_moc|databricks]]
- Built from used defined [[delta_live_table]]s
- Combines the pros of [[data_lake]] and [[data_warehouse]] for speed, flexibility, and structure
- Usually set up in three layers
	- [[data_lake_house_bronze_layer]] - Raw
	- [[data_lake_house_silver_layer]] - Processed
	- [[data_lake_house_gold_layer]] - Specialized
- Going between the layers uses a [[databricks_pipeline]] that uses [[delta_live_table]]s
- Databricks is data native so all the data is in one place, no need to move it between servers

## See Also:

- [[benefits_of_data_lake_house]]
- [[drawbacks_of_data_lake_house]]
