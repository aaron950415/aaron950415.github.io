---
layout: post
title: DOM events
subtitle:
date: 2020-07-22
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - DOM
---

The DOM level can be divided into four levels: DOM0 level, DOM1 level, DOM2 level and DOM3 level. *The DOM events are divided into three levels: DOM 0 level event processing, DOM 2 level event processing and DOM 3 level event processing.* Since there is no event related content in DOM 1 level, there is no DOM 1 level event.

## DOM event level

1. DOM 0 event

`el.onclick=function(){}`

```javascript
let btn = document.getElementById('btn');
btn.onclick = function(){
  alert(this.innerHTML);
}
```

When you want to bind multiple events of the same type to the same element/label (for example, bind 3 click events to the btn element above), it is not allowed. DOM0 event binding, binding methods to the event behavior of the element, these methods are all executed in the bubbling phase (or target phase) of the current element's event behavior.

2. DOM 2 event

`el.addEventListener(event-name, callback, useCapture)`

* event-name: event name, it can be a standard DOM event
* callback: callback function, when the event is triggered, the function will be injected with a parameter as the current event object event
* useCapture: The default is false, which means that the event handler is executed in the bubbling phase

```javascript
let btn = document.getElementById('btn');
btn.addEventListener("click", test, false);
function test(e){
	e = e || window.event;
  alert((e.target || e.srcElement).innerHTML);
  btn.removeEventListener("click", test);
}
```

3. DOM 3 event

More event types have been added to the DOM Level 2 event.

* UI events, triggered when the user interacts with elements on the page, such as `load`, `scroll`
* Focus events, triggered when an element gains or loses focus, such as `blur`, `focus`
* Mouse events, triggered when the user performs operations on the page through the mouse, such as: `dblclick`, `mouseup`
* Wheel event, triggered when the mouse wheel or similar device is used, such as `mousewheel`
* Text event, triggered when text is entered in the document, such as: `textInput`
* Keyboard event, triggered when the user performs an operation on the page through the keyboard, such as `keydown`, `keypress`
* Synthesis event, triggered when inputting characters for IME (input method editor), such as: `compositionstart`
* Change event, triggered when the underlying DOM structure changes, such as: `DOMsubtreeModified`
* At the same time, DOM3 level events also allow users to customize some events.

## Event stream

The DOM event model is divided into capture and bubbling. After an event occurs, it will propagate between the child element and the parent element. This spread is divided into three stages.

1. Capture phase: the phase where the event propagates from the window object from top to bottom to the target node;
2. Target stage: the stage where the real target node is processing the event;
3. Bubbling stage: the stage where the event propagates from the target node to the window object from bottom to top.

The capture is from top to bottom. The event first goes from the window object, then to the document, then the html tag, then the body tag, and then passes down layer by layer according to the normal html structure, and finally reaches the target element.

The process of event bubbling is just the reverse process of event capture.

As mentioned in the DOM 2 event, changing the third parameter in the addEventListener function can determine whether its operation is bubbling or capturing. Among them, some bubbling can be interrupted, and some bubbling can be interrupted by using the `e.stopropagation()` function. However, there are some exceptions. Search for scroll event in MDN to see whether the event can stop bubbling.

## Event delegation

Since the event will propagate up to the parent node during the bubbling phase, the listener function of the child node can be defined on the parent node, and the listener function of the parent node will uniformly handle the events of multiple child elements. This method is called event proxy.

Suppose there is a list with a large number of list items in the list, and we need to respond to an event when each list item is clicked

If you bind a function to each list item one by one, it will consume a lot of memory and consume a lot of performance in terms of efficiency. With the help of event proxy, we only need to bind a method to the parent container, so that no matter which descendant element is clicked, the click behavior of the container will be triggered according to the delivery mechanism of bubbling propagation, and then the corresponding method will be executed. According to the source of the event, we can know who clicked to accomplish different things.

In many cases, we need to dynamically add and delete list item elements through user operations. If you bind an event to each child element at the beginning, then when the list changes, you need to re-bind the event to the new element to be deleted soon. If you use the event proxy to unbind the event, it will save a lot of such trouble.





