up:: [[+info_databricks_training]]
tags:: #on/technology #learning #databricks 
link:: [Data Engineer Learning Plan](https://customer-academy.databricks.com/learn/lp/10/data-engineer-learning-plan)

# Databricks Data Engineer Learning Path
This space is for all notes relating to the Data Engineer Learning path on databricks.
The notes will eventually be moved to [[+about_dev|dev]], but I wanted a central place for the [[+about_inbox|inbox notes]]

``` dataview
TABLE WITHOUT ID
 file.link as "Databricks Data Engineer Learning Path",
 file.cday as "Creation Date"

FROM "note_reorg/Spaces/databricks_training/data_engineer_path"
and -#on/readme 
and -#on/pkm

where !contains(file.name, "+info")

SORT file.cday desc

LIMIT 20
```