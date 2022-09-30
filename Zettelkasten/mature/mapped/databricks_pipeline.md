# databricks_pipeline
Created: 2022-09-29 17:29

- Is the way that data moves through the three layers in a [[data_lake_house]] within databricks
- Runs the data through the [[delta_live_table]]s to move the data around
- For example
	- [[data_lake_house_bronze_layer]] \\/
	- bronze_silver_pipeline(delta_live_tables) \\/
	- silver_layer