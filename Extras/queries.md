up:: [[pkm_meta]]
tags:: #extras

# Queries

## All Pages with a Specific Tag, Ranked Desc

``` dataview
TABLE WITHOUT ID
 file.link as Efforts,
 rank as "Rank"

FROM #effort

SORT rank desc

```

## Unsorted Notes

``` dataview
TABLE WITHOUT ID
 file.link as "Encounters and new notes",
 (date(today) - file.cday).day as "Days alive"

FROM "+ Encounters" and -#on/readme 

SORT file.cday asc

LIMIT 20
```

## Notes in a Folder

``` dataview
TABLE WITHOUT ID
 file.link as "Newsletter",
 dates as "Date Published"

FROM "Spaces/My Newsletters"

SORT file.link desc

LIMIT 20
```

## Notes That Point to This File, but This File Doesn't Point Back (unrequited)

```dataview
LIST

FROM [[Concepts MOC]]
and !outgoing([[Concepts MOC]])
and -#map

SORT file.link asc
```
