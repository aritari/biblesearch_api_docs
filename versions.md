---
layout: default
title: Versions
---

# Versions

Versions are the specific editions of the Bible such as the New International Version (NIV) or King James Version (KJV).  Versions have many books.

## List

### GET /versions.xml

Returns a list of all available versions.

### Get /versions/#{version_id}/books.xml

Returns a list of all books for the specified version.

## List with Language

### GET /versions.xml?language=eng

Returns a list of all versions specified by the language parameter.  Use an [ISO 639-2][iso] abbreviation as the language parameter.
  
## Show
    
### GET /versions/1.xml

Returns a specific version with ID 1.

## Show with Books

### GET /versions/1.xml?include=books

You may pass an *include* query parameter with value *books* with your request to retrieve a list book resources belonging to each version (/versions.xml request) or the specified version (for the /versions/1.xml request).

[iso]: http://www.loc.gov/standards/iso639-2/php/code_list.php "ISO 639-2 language abbreviations"
