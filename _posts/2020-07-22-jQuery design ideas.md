---
layout: post
title: jQuery design ideas
subtitle:
date: 2020-07-22
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - Algorithm
---
jQuery is currently the most widely used javascript library. Learning jQuery is necessary because it allows you to lay the foundation for learning more advanced libraries in the future, and it is indeed easy to make many complex effects.

## How jQuery gets elements 

The first step in using jQuery is often to put a selection expression into the constructor `jQuery()` (abbreviated as `$`), and then get the selected element.

```javascript
window.$ = window.jQuery = function(selector) {
  let elements;
  elements = document.querySelectorAll(selector);
  return elements
}
```

This is just for selecting the elements of the web page. If you want to operate on the array, you can change the statement and return the `elements`, and then perform some operations on it.

```javascript
window.$ = window.jQuery = function(selectorOrArrayOrTemplate) {
  let elements;
  if (typeof selectorOrArrayOrTemplate === "string") {
    if (selectorOrArrayOrTemplate[0] === "<") {
      elements = [createElement(selectorOrArrayOrTemplate)];   //this function we don't achieve in here, it will be complete next
    } else {
      elements = document.querySelectorAll(selectorOrArrayOrTemplate);
    }
  } else if (selectorOrArrayOrTemplate instanceof Array) {
    elements = selectorOrArrayOrTemplate;
  }
  const api = Object.create(jQuery.prototype)
  Object.assign(api, {
    elements: elements,
    oldApi: selectorOrArrayOrTemplate.oldApi
  })
  return api
}
  $('#myId') //Select the web element whose ID is myId
```

## What is the chain operation of jQuery

One of the main design ideas of jQuery is that after the web page element is finally selected, a series of operations can be performed on it, and all operations can be connected together and written in the form of a chain.

```javascript
$('#div').find('h3').eq(2).html('Hello');
```

This is because, in the jQuery constructor, every time it completes a step, it will return to its original element, so it can be operated continuously.

## How jQuery creates elements

There is a function for creating elements in jQuery. Through this function, we can create corresponding elements.

```javascript
function createElement(string) {
  const container = document.createElement("template");
  container.innerHTML = string.trim();
  return container.content.firstChild;
}
$('<div></div>')        //create a div
```

## How jQuery moves elements

If it is to move an element, there are two steps. The first step is to move the element to the target position, and the second step is to delete the element at the original position.

```javascript
.insertAfter()  //Outside the existing element, insert the element from behind

.insertBefore() //Outside the existing element, insert the element from the front

.appendTo() //Inside the existing element, insert the element from behind

.prependTo()  //Inside the existing element, insert the element from the front

.remove() //Delete element

.empty()   //Clear the content of the element (but do not delete the element)
```

## How jQuery modifies the attributes of elements

jQuery uses the overloaded design pattern to achieve different parameters and use different codes.

```javascript
.attr(name, value)  //Set attribute value
.attr(name)   //read attribute value

.text()
.text(string)   //No parameter is to get text, one parameter is to write text

.html()
.html(string)   //No parameter is to get html element, one parameter is to write html element
```