---
alias: ["000"]
---

# Home
Your launchpad and home base. That's here. That's home.

This is the starting point for accessing any idea of the PKM efficiently.
Searching or selecting a specific file works too, but this is better for first access.

## Atlas
The [[+about_atlas|atlas]] is full of [[map_of_content|maps of content]] so you don't need to try to hunt down a specific file to get started.
They're all right here waiting for you.

## Diving In

>[!INFO]
>This is a dataview query
>The results only show up if the files are downloaded locally, queries like this don't work in obsidian publish.
``` dataview
TABLE WITHOUT ID
	file.link as "Map of Content",
	length(file.outlinks) as "Outgoing Links",
	length(file.inlinks) as "Incoming Links"

FROM "Atlas"
and -#on/pkm
and -[[pkm_meta]]

sort length(file.outlinks) desc, length(file.inlinks) desc
```

## Understanding this PKM
It can be daunting to jump right in to this repository of knowledge - and even more so maintaining it as it gets large.
Here are some helpful links for understand what the heck is going on across the PKM, and my own maintenance guidelines.
Everything here is made in [[obsidian]] with [[markdown]] files

- Overview of how this all works
	- [[+about_atlas]]
	- [[+about_spaces]]
	- [[+about_inbox]]
	- [[+about_dev]]
	- [[+about_cards]]
	- [[+about_calendar]]
	- [[+about_sources]]
- Maintenance and Building Resources
	- [[+about_extras]]
	- [[pkm_meta]]

## PKM Meta Access

``` dataview
TABLE WITHOUT ID
	file.link as "Map of Content",
	length(file.outlinks) as "Outgoing Links",
	length(file.inlinks) as "Incoming Links"

FROM outgoing([[pkm_meta]])

sort length(file.outlinks) desc, length(file.inlinks) desc
```