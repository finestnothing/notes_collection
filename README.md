# Collection of Notes in Obsidian
## Books:
```dataview
TABLE WITHOUT ID
	file.link as Name,
	rating as Rating
from "Reviews/Books"
where rating >= 7
sort rating desc

```

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