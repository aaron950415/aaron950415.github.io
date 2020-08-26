---
layout: post
title: What is AJAX
subtitle:
date: 2020-08-07
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - AJAX
---

## Preface

AJAX stands for "Asynchronous Javascript And XML", which refers to a web development technology for creating interactive web applications. AJAX is a technology used to create fast and dynamic web pages. It allows developers to only obtain data from the server (not pictures, HTML documents and other resources), and the transmission of Internet resources has become unprecedentedly lightweight and pure, which stimulates the creativity of developers and makes a variety of Powerful web sites and Internet applications have sprung up like bamboo shoots after a rain, constantly bringing surprises.


## What is Ajax

Ajax is a web development technology that requests data asynchronously, which is very helpful for improving user experience and page performance. Simply put, without the need to refresh the page, Ajax loads the background data through asynchronous requests and presents it on the web page. Common application scenarios include form verification whether the login is successful, Baidu search drop-down box prompts, and express tracking number query, etc. The purpose of Ajax is to improve user experience and reduce the amount of network data transmission. At the same time, because the AJAX request obtains data instead of HTML documents, it also saves network bandwidth and makes Internet users' web surfing experience smoother

## Use of Ajax

1. Create Ajax core object XMLHttpRequest (remember to consider compatibility)

    ```javascript
    var xhr=null;  
        if (window.XMLHttpRequest){
            // compatible IE7+, Firefox, Chrome, Opera, Safari  
        xhr=new XMLHttpRequest();  
        } else{// compatible IE6, IE5 
            xhr=new ActiveXObject("Microsoft.XMLHTTP");  
        }
    ```
2. Send a request to the server\

    ```javascript
    xhr.open(method,url,async);
    end(string);
    //The string parameter is only used in the post request, otherwise no parameter is required.
    ```

3. Server response processing (distinguish between synchronous and asynchronous)

* responseText gets the response data in string form.

* responseXML obtains the response data in XML format.
    
    Synchronization
    ```javascript
    xhr.open("GET","info.txt",false);
    xhr.send();
    document.getElementById("myDiv").innerHTML=xhr.responseText; //Get the data and display it directly on the page
    ```
    Asynchronous processing
     ```javascript
    xhr.onreadystatechange=function(){ 
        if (xhr.readyState==4 &&xhr.status==200){ 
        document.getElementById("myDiv").innerHTML=xhr.responseText;  
        }
    } 
    ```
