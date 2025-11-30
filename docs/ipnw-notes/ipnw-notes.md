# Project Notes

## Place Record Setup

Each place is made of several components:

1. one row in the "ipnw_places.csv" table describing the place. Has a unique identifier in the "objectid" column.
2. one or more rows in the "ipnw_place_objects.csv" table describing primary sources related to the place (i.e. images, documents, or links). Each related object has the place's objectid in the "parentid" column.
3. one markdown file in the "_essays/" collection containing a longer narrative description of the significance. The markdown file has a filename based on the place's objectid.

## Places

objectid,title,location,state,subject,time,latitude,longitude,cataloger,display_template,essay,featured_image_id,image_small,image_thumb,image_alt_text

## Objects

objectid,parentid,title,date,creator,category,description,significance,source,subject,location,state,latitude,longitude,cataloger,original_link,type,format,display_template,filename,object_location,image_small,image_thumb

## Essays

Front matter like:

```
---
objectid: ipnw-001
title: Example Essay Title
---
```

### Convert DOCX to MD

Students submit essays in DOCX form in OneDrive. 

Clean up essays in DOCX, then use pandoc to convert to markdown:

`for f in *.docx; do pandoc -f docx -t gfm --wrap=none -o "${f%.docx}.md" "$f"; done`

