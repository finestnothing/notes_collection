up:: [[pkm_meta]]
tags:: #pkm

# Dev Notes

This is where notes that have been developed from [[+about_inbox|inbox notes]] live before becoming [[atomic]] [[+about_cards|cards]].
This is where cards that have been rewritten into my own words but not yet made atomic will go. Formatting isn't important here either, just have to get the important info!
Avoid links here except to other Dev notes.

``` dataview
TABLE WITHOUT ID
 file.link as "Encounters and new notes",
 (date(today) - file.cday).day as "Days alive"

FROM "Dev" and (-#on/readme and -#on/pkm)

SORT file.cday asc

LIMIT 20
```
