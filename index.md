---
layout: default
title: Introduction
---

# ABS BibleSearch API Documentation

## Introduction

The ABS BS API is available via XML requests served over HTTP using [RESTful resources][rest].  Accessing Bible passages via API is a read-only process; you may access this content via HTTP GET requests.  To interact with user-specific features like accounts, tags, and notes, you may read and write to the API using all four HTTP verbs (GET/POST/PUT/DELETE).  

Because the ABS BS API is accessible via HTTP, you may use a regular browser to view all GET requests for the API.  We recommend using Firefox for this, since it will happily render XML in the browser.  For many URLs in the ABS BS application, you may simply append .xml to the URL to retrieve the corresponding API response for that URL.  For example, /versions/niv/books becomes /versions/niv/books.xml to retrieve the XML version.

You may also retrieve JSON responses from the ABS BS application by appending .json to the request URL.  For example, /versions/niv/books becomes /versions/niv/books.json to retrieve the JSON version.

## Authentication

All requests to the ABS API are authenticated via an existing ABS user account -- you do not need a special API user account to access the API.  All users have full read access to all Bible passages.  For user-specific content such as account information, tags, and notes, users have full read and write access, but only to their own content.

API Authentication is done via an authentication token, which you'll find on your [account settings page][settings] in the ABS BS application.  Every request must include your API key.  If necessary for your development environment, you may pass a dummy password along with your request.

Here is an example of how to use [Curl][3] to access our API.  (The dummy password "X" is being passed with this request.)                      

    curl -u YOUR_API_KEY:X http://@ABS_URL/versions/1.xml
    
*Remember to keep your authentication token private.*  Anything you can do via the website you can do via the API, so protect your API token as you would protect your username and password for the website.  If you ever want to change your API token, simply change your account password via the [account settings page][settings], and your API token will be changed as well.

TODO: Developers will also be able to grant access to signed-up users via OAuth.  This way users can use a third-party app built on the API to access their own account information while keeping that information private.

## Reading (HTTP GET requests)

There are two categories of actions used to read data from the ABS API: list and show.  List actions return a collection of records (such as all versions of the Bibles ABS provides) and may sometimes be filtered by certain criteria described in this documentation.  Each resource typically offers a single show action to return data about that individual resource (a particular book of a particular Bible version, for example).  

You may access all list and show actions via GET requests.  These are easily performed via either the browser or via command line:

Browser (load this URL in FireFox):

     http://#{your API token}:@ABS_URL/versions/1.xml

Command line (using [curl][curl]):

    curl -u #{your API token}:X http://@ABS_URL/versions/1.xml
    
If the read request is successful, the XML response will include the status code "200 OK."

*Please note:* Bible passages are only available via read requests.  Right access is not available for Bible passages.

## Writing (HTTP POST and PUT requests)  

You may use the ABS API to create and update content that you, yourself, have created.  This includes account information, tags, and notes.  To perform these write requests, you will need to send an XML request to the ABS API along with the relevant HTTP verb for your action.  Because of these requirements, it is not easy to interact with the ABS API using your browser to send these write requests.  Instead, we recommend you use a command line tool like [curl][curl] to play around with this portion of the ABS API interface.

To create new resources via the ABS API, send the resource encoded as XML or JSON.  **Be sure to also send the correct Content-type header with your request.**  This will be either "Content-type: application/xml" for XML requests or "Content-type: application/javascript" for JSON requests.  Data should be sent to the ABS API as the raw POST or PUT body.                            

Examples:

To create a new tag via the ABS API, do this:

    curl -u #{your API token}:X -H 'Content-Type: application/xml' \
    -d '<tag><name>love</name></tag>' http://@ABS_URL/tags
    
Successful creations respond with the status code "201 Created."  The response will also include the URL of the resource in the location header and the complete resource, formatted as XML.  It's helpful to use the returned resources attributes (especially the id attribute) to interact with the resource in subsequent requests.

You may update resources you have created by performing an HTTP PUT request.  The resource attributes you pass with the request (as XML) will replace the attributes on file for that resource.

A sample update request:

    curl -u #{your API token}:X -X PUT -H 'Content-Type: application/xml' \
    -d '<tag><name>love</name></tag>' http://@ABS_URL/tags/1.xml

Successful update requests return the response code "200 OK."

## Deleting (HTTP DELETE requests)

You may delete content you, yourself, have created by sending an HTTP DELETE request:

    curl -u #{your API TOKEN}:X -X DELETE http://@ABS_URL/tags/5.xml
    
*Please note:* The content-type header is not needed for DELETE requests, since you are not sending any XML to the ABS API.  

Successful update requests return the response code "200 OK."

## Response codes

Successful requests will return HTTP response codes in the 200s, either "201 Created" for actions where you have created content via the ABS API, or "200 OK" for all other queries, updates, or deletions.  For example, a request for a nonexistent resource would return:

    HTTP/1.1 404 The record could not be found
    Date: Thu, 16 Mar 2006 17:41:40 GMT
    ...

## API conventions           

Throughout this documentation, the following conventions are in use:

* #{text}: Indicates that this text should be replaced by your own data.
* ...: Indicates that a portion of the response has been omitted for brevity and clarity's sake.

[rest]: http://en.wikipedia.org/wiki/Representational_State_Transfer "REST"
[settings]: 
[curl]: http://curl.haxx.se/