up:: [[pkm_meta]]
tags:: #on/pkm 

# Inbox Notes
This folder serves as the "inbox" to the PKM. All notes destined for the [[+about_cards|cards folder]] start their life here.
The purpose is to contain the raw data, usually notes from some source or an idea. 
While they're in the inbox, the ideas cools off a bit. 
If I come back to the note or idea in the future and it no longer seems useful then it can easily be discarded!
The notes are meant for future me anyway, so it helps to revisit them after an adequate time delay so "future me" is the one that revisits it.

Avoid links except to other notes here!

``` dataview
TABLE WITHOUT ID
 file.link as "Encounters and new notes",
 (date(today) - file.cday).day as "Days alive"

FROM "Inbox" and (-#on/readme and -#on/pkm)

SORT file.cday asc

LIMIT 20
```

#to/do - Sort through old_notes, integrate with new PKM