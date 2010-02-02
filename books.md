---
layout: default
title: Books
---

# Books

These are the books of the Bible belonging to the requested version.  Books belong to versions and have many chapters.

## List

### Get /books.xml

Returns a list of all books for all versions.

### Get /books.xml?bookgroup=#{abbreviation}

Returns a list of only those books identified by the group abbreviation of a <a href="bookgroups.html">book group</a>.

### Get /books.xml?testament=#{abbreviation}

Returns a list of only those books identified by the Testament abbreviation.  Valid abbreviations include NT (New Testament), OT (Old Testament) and DEUT (Deuterocanonical).

## Show

### GET /books/1.xml

Returns the specified book resource with ID=1.

### GET /books/1.xml?include=version

You may pass an *include* query parameter with value *version* with your request, to enclose your book resource in its parent version resource.

### GET /books/1.xml?include=bookgroup

You may pass an *include* query parameter with value *bookgroup* with your request, to enclose your book resource in its applicable book group resource.


