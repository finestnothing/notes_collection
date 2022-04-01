# Collection of Notes in Obsidian
## Projects:
```dataview
TABLE WITHOUT ID
	file.link as Name,
	status as Status
from "Projects"
sort status asc
```

## Books:


## Recipes:
```dataview
TABLE WITHOUT ID
	file.link as Name,
	rating as Rating
FROM "Reviews/Recipes"
WHERE rating >= 7
SORT rating desc
```

## Restaurants:
```dataview
TABLE WITHOUT ID
	file.link as Name,
	rating as Rating
FROM "Reviews/Restaurants"
WHERE rating >= 7
SORT rating desc
```

## Templates:
```dataview
TABLE WITHOUT ID
	file.link as File
FROM "Templates"
```