---
layout: post
title: 纯js借助Formspree发送邮件
subtitle:
date: 2020-12-07
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JS
---

1. 现在[官网](https://formspree.io/)注册一个账号，并且验证邮箱（如果不验证，将无法使用）
2. 创建新的表单里面填上表单名，项目名以及发送到的邮箱。
3. 配置html 

    * 官方有给出模板（把代码复制到自己地代码里）
    
        ```html
        <form action="https://formspree.io/f/mjvpawqr" method="POST">
        <input type="text" name="name">
        <input type="email" name="_replyto">
        <input type="submit" value="Send">
        </form>
        ```
    
    * 配置邮箱收到信息的html模板

        ```html
            <form
        action="https://formspree.io/f/mjvpawqr"
        method="POST"
        >
        <label>
            Your email:
            <input type="text" name="_replyto">
        </label>
        <label>
            Your message:
            <textarea name="message"></textarea>
        </label>

        <!-- your other form fields go here -->

        <button type="submit">Send</button>
        </form>
        ```
    * 每个账号都有特定的form's endpoint
    * input / textarea 标签都需要设定相应的 name 属性。收到的邮件信息为name属性值和对应的表单信息。
4. 成功发送