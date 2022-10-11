up:: [[pkm_meta]]
tags:: #extras

# Queries

## All pages with a specific tag, ranked desc
``` dataview
TABLE WITHOUT ID
 file.link as Efforts,
 rank as "Rank"

FROM #effort

SORT rank desc

```

## Unsorted notes
``` dataview
TABLE WITHOUT ID
 file.link as "Encounters and new notes",
 (date(today) - file.cday).day as "Days alive"

FROM "+ Encounters" and -#on/readme 

SORT file.cday asc

LIMIT 20
```

## Notes in a folder

``` dataview
TABLE WITHOUT ID
 file.link as "Newsletter",
 dates as "Date Published"

FROM "Spaces/My Newsletters"

SORT file.link desc

LIMIT 20
```

## Notes that point to this file, but this file doesn't point back (unrequited)
```dataview
LIST

FROM [[Concepts MOC]]
and !outgoing([[Concepts MOC]])
and -#map

SORT file.link asc
```