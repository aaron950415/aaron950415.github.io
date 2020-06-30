---
layout:     post
title:      Git Learning
subtitle:   cmder first using
date:       2020-07-01
author:     BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
    - git command
    - cmder
---


On the way to learning Git, some necessary tools are indispensable. cmder is a software that integrates cmd and comes with git bush instructions.

* First download and install the software on the official website.
* Second, for cmder configuration, select the type of instruction to run in the settings (for our learning, the choice should be {bush::bush})
* The third is to configure Git in six steps, fill in and remove the brackets arbitrarily:
    ```
    git config --global user.name (your name)
    git config --global user.email (e-mail)
    git config --global push.default simple
    git config --global core.quotepath false
    git config --global core.editor "code --wait"
    git config --global core.autocrlf input
    ```
* Fourth, after the above configuration, the configuration is successful.
  
Verification: Entering code will automatically run vscode (installed before cmder)
* Question 1: If it fails to open, please determine whether it is in the path of the user environment
X:\XXXXX\Microsoft VS Code\bin, if not, please add it.

* Question 2: Permission denied appears, this is because cmder has insufficient permissions. The solution is to click the cmder property-compatibility-to run this program as an administrator. This will solve the problem successfully.
