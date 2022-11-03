up:: [[databricks_workspaces]]

# databricks_sql

- Modified version of standard [[sql]] inside [[databricks_moc|databricks]]
- Useful for [[data_engineering]] and [[data_science]]
- Has easy to make [[databricks_dashboard]]s based on queries
- Can also connect external [[business_intelligence]] tools
- Utilizes [[photon]] to speed up queries
- Queries run directly on the [[data_lake_house]], don't need to connect to any external tools
- Automating workflows
	- Can setup notifications if values fall out of certain ranges to make sure criteria are met
	- Auto schedule query refreshes (Keeping dashboard up to date, using in a notification, etc)
	- When a visualization is saved on a saved query, it always will pop up when the query is opened
- Also doesn't have to use a [[sql_table]] as the source, they can also use [[self_describing_data_sources]] - [[databricks_sql_query_files]]

## See Also:
- [[sql_endpoints]]
- [[databricks_unity_catalog]]