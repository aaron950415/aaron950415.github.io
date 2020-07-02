---
layout: post
title: How to delete Github file and document in remote repository
subtitle:
date: 2020-07-02
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - Github
  - Repository
---

### Quickly delete 

Firstly, people must clone your remote repository to the local repository.

I use my repository as example.I had created a test1 document and a test1.txt file in the Github

![](/img/item/item3-1.jpg)
You can clone with HTTPS or SSh, but I recommend use SSH, it is convenient. And entry the document. The code of clone is

`git clone git@github.com:xxx/xxx.git`
![](/img/item/item3-2.jpg)

Secondly, you choose your files or documents which you want to delete to execute the following command:

```
git rm -r test1 
git rm test.txt 
```
![](/img/item/item3-3.jpg)
Both execute successfully. If you meet any question, you can try these command:
```
git rm -rf test1 
git rm -f test.txt 
```
Thirdly, commit modify. The command is

`git commit -m "Delete"`
![](/img/item/item3-4.jpg)

Finally, Submit the changes to the xxx branch of the remote repository:
`git push origin xxx`
![](/img/item/item3-5.jpg)

Result, my repository has cleared file and document.
![](/img/item/item3-6.jpg)
