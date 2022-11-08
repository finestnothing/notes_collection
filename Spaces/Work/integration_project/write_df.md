# write_df

- Purpose: Create a csv from the data
- Inputs: data
- Outputs: csv file
- Questions: Where to write it? Workspaces doesn't support non-notebook files.
	- Have to write to dbfs table first
	- Copy it to S3
	- Is it possible to write directly to S3 possibly? Databricks has weird file-write stuff
