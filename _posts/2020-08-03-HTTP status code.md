---
layout: post
title: HTTP status code
subtitle:
date: 2020-07-28
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - http
---
## Classification of status codes
* 1** Information, the server receives the request and needs the requester to continue the operation
* 2** Success, the operation was successfully received and processed
* 3** Redirect, further action is required to complete the request
* 4** Client error, the request contains syntax errors or the request cannot be completed
* 5** Server error, the server encountered an error while processing the request

## 
* 100 continue. The client should continue its request
* 101 Switch protocol. The server switches the protocol according to the client's request. Can only switch to more advanced protocols, for example, switch to the new version of HTTP protocol
* 200 The request was successful. Generally used for GET and POST requests
* 201 has been created. Successfully requested and created a new resource
* 202 has been accepted. The request has been accepted, but has not been processed
* 203 Non-authorized information. The request was successful. But the returned meta information is not on the original server, but a copy
* 300 Multiple choices. The requested resource can include multiple locations, and accordingly a list of resource characteristics and addresses can be returned for user terminal (for example: browser) selection
* 301 Moved permanently. The requested resource has been permanently moved to the new URI, the returned information will include the new URI, and the browser will automatically be directed to the new URI. Any new requests in the future should use new URIs instead
* 400 The syntax of the client request is incorrect and the server cannot understand it
* 401 request requires user authentication
* 403 The server understands the request of the requesting client, but refuses to execute the request
* 404 The server could not find the resource (webpage) according to the client's request. With this code, the website designer can set a personalized page of "The resource you requested cannot be found"
* 405 The method in the client request is forbidden
* 416 The range requested by the client is invalid
* 500 server internal error, unable to complete the request
* 501 The server does not support the requested function and cannot complete the request
* 502 When the server working as a gateway or proxy tried to execute the request, an invalid response was received from the remote server
* 503 Due to overload or system maintenance, the server is temporarily unable to process the client's request. The length of the delay can be included in the server's Retry-After header information
* 504 The server acting as a gateway or proxy does not get the request from the remote server in time
* 505 The server does not support the requested HTTP protocol version and cannot be processed