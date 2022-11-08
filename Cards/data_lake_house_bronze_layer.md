up:: [[data_lake_house]]

# data_lake_house_bronze_layer

Created: 2022-09-29 17:32

- Layer that holds the raw ingested data
- Usually just a mirror of the data
- No transformations occur between data source and the bronze layer
- Connects to [[data_lake_house_silver_layer]] through a [[databricks_pipeline]]
- Defined by [[delta_live_table]]s
