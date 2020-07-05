---
layout: post
title: A simple understanding of url
subtitle:
date: 2020-07-05
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - url
---

Today, I share my understand about url. That include:

1. What is url?
2. The composition of url
3. Absolute URLs vs relative URLs
4. What is IP?

## What is url?
URL stands for Uniform Resource Locator. A URL is nothing more than the address of a given unique resource on the Web. In theory, each valid URL points to a unique resource. Such resources can be an HTML page, a CSS document, an image, etc. In practice, there are some exceptions, the most common being a URL pointing to a resource that no longer exists or that has moved. As the resource represented by the URL and the URL itself are handled by the Web server, it is up to the owner of the web server to carefully manage that resource and its associated URL.

## The composition of url
The URL contains the protocol, domain name or IP, port number, path, query parameters, and anchor point. Some of them are mandatory, while others are optional. Let's use the following URL to view the most important part:

`https://www.xiedaimala.com:80/path/to/myfile.html?key1=value1&key2=value2#common`

First part is protocol, `https`. The URL indicates the protocol that the browser must use. A protocol is a setting method used to exchange or transmit data on a computer network. Usually for websites, it is HTTP protocol or its secure version HTTPS. Sometimes you maybe see other protocol, like `ftp:`,it's normally, despite we selden use it to hand file transfers, because it's very old protocol.

Second part is DNS or Domain Name System, `www.xiedaimala.com`. It indicates which web server is being requested. In addition, the IP address can also be used directly, but because it is not convenient, it is not often used on the Web.

Third part is port, `:80`. It indicates the technical "gate" for accessing resources on the Web server. If the web server uses the standard port of the HTTP protocol (80 for HTTP and 443 for HTTPS) to grant access to its resources, it is usually omitted. Otherwise, it is mandatory.

Forth part is path, `/path/to/myfile.html`. It is the path of the resource on the web server. In the early days of the Web, such paths represented physical file locations on the Web server. Today, it is mainly an abstraction handled by a Web server, without any physical reality.

Fifth part is parameters, `?key1=value1&key2=value2`. It is an additional parameter provided to the web server. These parameters are a list of key/value pairs separated by ampersands. Before returning the resource, the Web server can use these parameters to do some additional work. Every web server has its own rules about parameters, and the only reliable way to know whether a particular web server is processing parameters is to ask the web server owner.

Last part is anchor, `#common`. The anchor represents a kind of "bookmark" within the resource and provides instructions to the browser to display the content at the "marked" point. For example, on an HTML document, the browser will scroll to the position where the anchor is defined. On a video or audio document, the browser will try to go to the time indicated by the anchor. (Notice, the part after # is also called the fragment identifier and is never sent to the server with the request.)
## Absolute URLs vs relative URLs
What we saw above is called an absolute URL, but there is also something called a relative URL. Let's examine what that distinction means in more detail.

The required parts of a URL depend to a great extent on the context in which the URL is used. In your browser's address bar, a URL doesn't have any context, so you must provide a full (or absolute) URL, like the ones we saw above. You don't need to include the protocol (the browser uses HTTP by default) or the port (which is only required when the targeted Web server is using some unusual port), but all the other parts of the URL are necessary.

When a URL is used within a document, such as in an HTML page,  things are a bit different. Because the browser already has the document's own URL, it can use this information to fill in the missing parts of any URL available inside that document. We can differentiate between an absolute URL and a relative URL by looking only at the path part of the URL. If the path part of the URL starts with the "/" character, the browser will fetch that resource from the top root of the server, without reference to the context given by the current document.

## What is IP?
Each machine on the network has a unique identifier. Just like you want to send a letter in an email, a computer uses a unique identifier to send data to a specific computer on the network. Most networks today, including all computers on the Internet, use the TCP/IP protocol as a standard for how to communicate on the network. In the TCP/IP protocol, the unique identifier of a computer is called its IP address.

There are two standards for IP addresses: IP version 4 (IPv4) and IP version 6 (IPv6). All computers with IP addresses have an IPv4 address, and many computers have begun to use the new IPv6 address system.