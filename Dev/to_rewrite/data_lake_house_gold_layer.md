# data_lake_house_gold_layer
Created: 2022-09-29 17:36

- Top tier of a [[data_lake_house]]
- Fully cleaned and transformed data
- Used for reports and viewing directly
- Heavy aliasing is usually done to match specific uses
- Gets data from [[data_lake_house_silver_layer]] through a [[databricks_pipeline]]
- Changes frequently to meet the needs of the reports