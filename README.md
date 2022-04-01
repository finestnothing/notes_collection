# Alecs Notes
Made in [https://obsidian.md/](https://obsidian.md/). Links to other files should still work without it.

## Projects:
```dataview
TABLE WITHOUT ID
	file.link as Name,
	status as Status
from "Projects"
sort status asc
```

## Books:
Current: [ready_player_one](Reviews/Books/ready_player_one.md)
Favorite: [ready_player_one](Reviews/Books/ready_player_one.md)
```dataview
TABLE WITHOUT ID
	file.link as Name,
	genre as Genre,
	rating as Rating
FROM "Reviews/Books"
WHERE rating >= 6
SORT rating desc
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