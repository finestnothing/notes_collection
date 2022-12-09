up:: [[databricks_workspaces]]

# databricks_machine_learning

Created: 20221101 17:35
Modified: 20221101 17:35

Haven't used this one too much, so it'll get flushed out later
More info will get added to this when I work on the ML training

Can be an end to end system for ML
- Prep data
- Build Model
- Deploy and Monitor
- Use delta lake and apache spark
- Batch scoring
- Cloud training

Addresses common issues in ML
- Quality issues
	- Data built in, won't get corrupted or lost trying to move it around
- Compute resources - too much or not enough resources for training
	- Auto scaling for resources
	- Can also manually specify resources
- Need input data sets for training and testing
	- Feature score registry to save the data
- Develop models - Can be costly and time consuming to develop
	- Databricks AutoML builds a series of models and logs their runtimes and effectiveness
- Hard to evaluate and govern new ML settings
	- Access control lists and Unity Catalog work together to restrict access
- Once they're built, need to be integrated
	- Store and manage models
	- Standard model deployment and staging
	- Streaming serving tools

what's in the workspace?
- Databricks ML Runtime
	- Has [[tensorflow]], [[scikit_learn]], [[keras]], etc
	- Create environments for running models
- Repos
	- Sync projects and existing projects
	- CI/CD workflows
- Workflows
	- Automate running jobs

## See Also

- [[databricks_ml_flow]]
- [[databricks_auto_ml]]
- [[databricks_feature_store 1]]
