---
layout:     post
title:      HTML beginner level note 1
subtitle:   cmder first using
date:       2020-07-01
author:     BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
    - HTML
    - tags
---

HTML is the abbreviation of Hyper Text Mark-up Language, which is created by Timothy John Berners-Lee, who is a British computer scientist.

When we start write HTML document, wo must write first tag, `<!DOTYPE html>`. Then we can add content in this tag.

In the tag, we also should add verify tags such `<html>` `<body>`,`<head>` etc.

Now, I introduce some Table chapter tags we often use:
* From `<h1>` to `<h6>`, that are content tags. we often use them as head tittle, because they are different size. `<h1></h1>` is largest size among them, and then with the number group, the size will be small. But actually, when we use them, we often use CSS to change their style.
* `<section>` defines a section in the document. Such as chapters, headers, footers, or other parts of the document.
* `<article>` specifies independent self-contained content. It often be contained by `<section></section>`
* `<main>` is a specially tag, that determine the document main content and it is Uniquely. Moreover, it must independent on some tags, like `<article>`,`<aside>` or `<header>` ect.
* `<aside>` defines content other than its content.

Additionally, some global attributes we also need to note, such as `class`,`style`,`contenteditable`,`title`,`tabindex`,`hiden` and `id` ect.

Some tags we often use I will mention as flow:
1. `<a>` defines hyperlinks, which are used to link from one page to another. The most important attribute of the `<a>` element is the href attribute, which indicates the target of the link.
2. `<strong>` and `<em>` all express emphasis, but `<em>` defines text as expert content. `<strong>` defines the text as the content of the author with a stronger tone.
3. `<code>` define a computer code text. The content in this tag will maintain a fixed distance.
4. `<pre>` can define pre-formatted text. The text enclosed in the `<pre>` element usually retains spaces and line breaks. The text will also be rendered as a monospaced font. A common application of the `<pre>` tag is to represent the source code of a computer.
5. `<ul>`,`<ol>` and `<il>` will present table. `<ul>` and `<ol>` are some level, but `<ul>` defines a unorder list, `<ol>` defines a order list. `<il>` can be used in ordered lists `<ol>` and unordered lists `<ul>`.