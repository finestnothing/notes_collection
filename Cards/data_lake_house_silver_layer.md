up:: [[data_lake_house_bronze_layer]]

# data_lake_house_silver_layer
Created: 2022-09-29 17:34

- Cleaned up version of data from [[data_lake_house_bronze_layer]] in a [[data_lake_house]]
- Not used directly for anything except the [[databricks_pipeline]] to the [[data_lake_house_gold_layer]]  from the [[data_lake_house_bronze_layer]]
- Usually has some standardization of variable names, even if just for ease of use
- Can be transformed, and calculated fields added
- Changes as new fields are added, which is not frequent
- Most of the processing and cleaning occurs when transferring data to this layer