---
layout: default
title: Chapters
---

# Chapters
                    
Chapters are the sub-sections of a selected book.  Chapters belong to books and have many verses.

## List

### GET /chapters.xml

Returns a list of all chapters.

### GET /books/#{book_id}/chapters.xml

Returns a list of all chapters for the specified book resource.

## Show

### GET /chapters/1.xml

Returns the specific chapter with ID 1.

### GET /versions/1.xml?include=verses

You may pass an *include* query parameter with value *verses* with your request to retrieve a list of each verse belonging to the specified chapter.

