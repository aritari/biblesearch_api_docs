---
layout: default
title: Users
---

# Users

You may access your user account (and associated resources) via the ABS API.  Users have many tags and notes.

## List

_No list actions are available for the User resource.  You may only access show actions for your own user account._

## Show

### GET /user.xml

Returns your user resource. 

## Show with notes and tags

### GET /user.xml?include=notes,tags

You may pass an *include* query parameter with value *notes* or *tags* or *notes,tags*  with your request to retrieve a list of your own notes, tags, or both notes and tags, respectively.

## Create

_No create action is available for the User resource.  (Users must be created by signing up to ABS BS application via the website.)_

TODO: Is this correct?  Should users only be able to sign up via web?

## Update

### PUT /user.xml

Update your user account with content of the submitted XML.

## Delete

_No delete action is available for the User resource.  (Users must be deleted by canceling your account via the  ABS BS website.)_

TODO: Is this correct?  Should users only be able to unsubscribe via the website?
