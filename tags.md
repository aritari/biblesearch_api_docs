---
layout: default
title: Tags
---

# Tags

Tags are annotations you apply to selected Bible verses.  Tags belong to users.

## List

### GET /tags.xml

Returns all of your tags.

## List with verses

### GET /tags.xml?include=verses

You may pass an *include* query parameter with value *verses* with your request to retrieve the verse(s) your tags are assigned to.

## Show

*Please tag:* You may only access the tags you have created yourself.  If you attempt to access a tag belonging to someone else, you will receive a "404 Not Found" error.

### GET /tags/1.xml

Returns the tag identified by ID 1.  

## Show with verses

### GET /tags/1.xml?include=verses

You may pass an *include* query parameter with value *verses* with your request to retrieve the verse(s) your tag is assigned to.

## Create

### POST /tags.xml

Creates a tag resource for the verse(s) you pass to it in the body of your XML request.

## Update

### PUT /tags/1.xml

Updates the tag identified by ID 1 with content of the submitted XML.

## Delete

### DELETE /tags/1.xml

Deletes the tag identified by ID 1.

*Please tag:* The content-type header is not needed for DELETE requests, since you are not sending any XML to the ABS API.