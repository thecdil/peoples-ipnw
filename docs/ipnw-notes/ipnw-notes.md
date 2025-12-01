# Project Notes

## Place Record Setup

Each place is made of several components:

1. one row in the "ipnw-atlas.csv" table describing the place. Has a unique identifier in the "objectid" column. It does NOT have a "parentid".
2. one or more rows in the "ipnw-atlas.csv" table describing primary sources related to the place (i.e. images, documents, or links). Each related object has the place's objectid in the "parentid" column.
3. one markdown file in the "_essays/" collection containing a longer narrative description of the significance. The markdown file has a filename based on the place's objectid.

## Places and Objects Table

To follow standard CB conventions, the places and objects records are combined into a single CSV. 
Some of the columns are only used by specific types of records. 

The "place" records are the parents for all objects, following the compound object conventions of CB.

objectid,parentid,title,time_period,date,creator,category,description,significance,source,subject,location,state,latitude,longitude,cataloger,original_link,type,format,display_template,filename,object_location,image_small,image_thumb,image_alt_text,featured_image_id,essay_file

The records are submitted by students in two forms. 
The form data is wrangled into the final CSV used in the website.

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

# Issues

- problematic rights, like NewBank
- inconsistent sources
- source links
- essay citations
- add color

