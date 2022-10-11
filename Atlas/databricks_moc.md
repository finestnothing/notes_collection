up:: [[README]]
tags:: #on/technology #map

# Databricks Map of Content
This map of content contains notes related to databricks

``` dataview
TABLE WITHOUT ID
 file.link as "Databricks Data Engineer Learning Path",
 file.cday as "Creation Date"

FROM "Spaces/databricks_training/data_engineer_path" and (-#on/readme and -#on/pkm)

SORT file.cday desc

LIMIT 20
```