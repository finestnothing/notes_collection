up:: [[databricks_unity_catalog]], [[databricks_hive_metastore]]

# unity_catalog_vs_hive_metastore

Differences between Unity Catalog and Hive Metastore
- Account groups
	- Unity Catalog: Access control policies are applied to account group
	- Hive Metastore: Access control policies are applied to workspace_local groups
- Permissions - Use Catalog and Use Schema
	- Unity Catalog:
		- Use Catalog and Use Schema permissions are required on the catalog and schema for all operations on objects inside the catalog or schema
		- Even if a principal has privilege to access a table, they must have the USE CATALOG privilege on the parent catalog to access the schema
			- Needs USE SCHEMA on parent catalog to access objects within the schema
	- In hive metastore, granting USAGE access on the root catalog automatically grants USAGE on all databases, but USAGE on the root catalog is not needed
- Views
	- Unity Catalog
		- Owner of a view does not need to be an owner of the views referenced tables and views
		- Having the SELECT privilege is sufficient, along with USE SCHEMA on the views parents schema and USE CATALOG on the parent catalog
	- hive metastore
		- Views owner needs to be an owner of all referenced tables and views
- All Files/Anonymous Functions
	- Unity Catalog
		- No concept of ALL FILES or Anonymous Function permission
		- They can be used to circumvent access control restrictions
			- Could let unprivileged user run privileged code
