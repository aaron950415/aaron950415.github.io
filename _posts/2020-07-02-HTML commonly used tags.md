---
layout: post
title: HTML commonly used tags
subtitle:
date: 2020-07-02
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - HTML
  - Tags
---

## Foreword

Initially, I thought that `<a>` tag is very simple to use, just add tag and attribution like `<a herf="#">`. But when I learned deeply, I realized that it also can add other function. so, I prepare take some tags to in detail describe.

## `<a>`

`<a>` defines hyperlinks, which are used to link from one page to another.The most important attribute of the `<a>` element is the href attribute, which indicates the target of the link.

1.  The value of `href`, before I learned, I thing we just add website link or path in here that is enough. Now I discover we also can add some Pseudo-protocol, like `javascript:code;`, `mailto:e-mail` and `tel:phone number`.
    Moreover, it also can add `id`, which can redirect to id position in this page when people click link.

        ```html
        <a herf="javascript:alert('respond')"> javascript:code</a>
        <a herf="mailto: aaroon950415@qq.com"> mailto:e-mail</a>
        <a herf="tel:XXXXXXXXXX"> tel:phone number</a>
        <a herf="#XXXXX">ID</a>
        ```

2.  The value of `target`, this value can determine page open position in the browser.
    ```html
    <a herf="#" target="_bank"> open in new tab in the browser</a>
    <a herf="#" target="_bank"> open in original tag</a>
    <a herf="#" target="_parent"
      >open page in the parent frame (often use it with iframe tag)</a
    >
    <a herf="#" target="_top"
      >open page in the top frame (often use it with iframe tag)</a
    >
    ```
3.  The value of `tittle`, it will show the information about the link when mouse move on link.
    ```html
    <a herf="#" tittle="I wanna change"
      >the information will show "I wanna change"</a
    >
    ```

## `<img>`

`<img>` can get the picture from the source address and post it in the page.

1. The value of `src`, it is picture address.
   ```html
   <img src="XXXX" />
   ```
2. The value of `alt`, it will show information when the source address error.
   ```html
   <img src=" " alt="Error message" /> //Error message
   ```
3. The values of `width` and `height`, obviously, it is change the size of image. However, in order to achieve maintain normal ratio of pictures, we often change the one of them.
4. Event operation, `onload` and `onerror` .The onload event is executed immediately after the image is loaded.The onerror event is executed immediately after the image show error.

   ```html
   <img src=" " onerror="error()" onload="success()" />
   <script>
     function success() {
       alert("onload success");
     }

     function error() {
       alert("Error message");
     }
   </script>
   ```

## `<table>`

`<table>` defines an HTML table.

1. A simple HTML table consists of table elements and one or more `<tr>`, `<th>`, or `<td>` elements.
2. The `<tr>` element defines the table row, the `<th>` element defines the table header, and the `<td>` element defines the table cell.
   ```html
   <table>
     <tr>
       <td></td>
       <td></td>
     </tr>
     <tr>
       <td></td>
       <td></td>
     </tr>
   </table>
   ```
3. More complex HTML tables may also include `<thead>`, `<tfoot>`, and `<tbody>` elements.
   ```html
   <table>
     <thead>
       <tr>
         <td></td>
         <td></td>
       </tr>
     </thead>
     <tbody>
       <tr>
         <td></td>
         <td></td>
       </tr>
       <tr>
         <td></td>
         <td></td>
       </tr>
     </tbody>
   </table>
   ```
