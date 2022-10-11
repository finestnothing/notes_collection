# data_lake_house
Created: 2022-09-29 17:20

- Specific data storage type made by [[databricks_moc|databricks]]
- Built from used defined [[delta_live_table]]s
- Combines [[data_lake]] and [[data_warehouse]] for speed, flexibility, and structure
- Usually set up in three layers
	- [[data_lake_house_bronze_layer]]
	- [[data_lake_house_silver_layer]]
	- [[data_lake_house_gold_layer]]
- Going between the layers uses a [[databricks_pipeline]] that uses [[delta_live_table]]s

[[benefits_of_data_lake_house]]
[[drawbacks_of_data_lake_house]]