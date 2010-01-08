---
layout: default
title: Notes
---

# Notes

Notes are annotations you apply to selected Bible verses.  Notes belong to users.

## List

### GET /notes.xml

Returns all of your notes.

## List with verses

### GET /notes.xml?include=verses

You may pass an *include* query parameter with value *verses* with your request to retrieve the verse(s) your notes are assigned to.

## Show

*Please note:* You may only access the notes you have created yourself.  If you attempt to access a note belonging to someone else, you will receive a "404 Not Found" error.

### GET /notes/1.xml

Returns the note identified by ID 1.  

## Show with verses

### GET /notes/1.xml?include=verses

You may pass an *include* query parameter with value *verses* with your request to retrieve the verse(s) your note is assigned to.

## Create

### POST /notes.xml

Creates a note resource for the verse(s) you pass to it in the body of your XML request.

## Update

### PUT /notes/1.xml

Updates the note identified by ID 1 with content of the submitted XML.

## Delete

### DELETE /notes/1.xml

Deletes the note identified by ID 1.

*Please note:* The content-type header is not needed for DELETE requests, since you are not sending any XML to the ABS API.