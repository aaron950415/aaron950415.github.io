---
layout: post
title: JS data type and conversion
subtitle:
date: 2020-07-09
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
---
# Data type
There are seven types of data, four basic types, two empty types, and one object.
## Four basic types
  1. Number
  
      Number type, including integer value and floating point value, such as 21, 0.21, default value: 0
      ```JavaScript
      var age = 21;     //integer
      var Age = 21.3578 //floating
      ```
      It has 3 special values.
      Infinity, representing infinity, greater than any value

      -Infinity, stands for infinitesimal, less than any value

      NaN, Not a number, represents a non-number

      ```javascript
      alert(Infinity); //Infinity
      alert(-Infinity); //-Infinity
      alert(NaN); //NaN
      ```

  1. String
   
      String type can use any text in quotation marks, the syntax is double quotation mark "" and single quotation mark ''
      ```javascript
        var strMsg = 'I like u'; //Use single quotes to represent strings
        var strMsg2 = "sure";    //Use double quotes to represent strings
      ```
      The string is composed of several characters, the number of these characters is the length of the string. The length of the entire string can be obtained through the length property of the string.
      ```javascript
        var strMsg = 'I like u';
        console.log(strMsg.length)     //show length 8
      ```

  2. Boolean
   
      The Boolean type has two values: true and false, where true means true, and false means false. When the Boolean and numeric types are added, the value of true is 1, and the value of false is 0.
      ```javascript
      var flag = true;  
      var flag1 = false;
      console.log(flag + 1); //2
      console.log(flag1 + 1);//1
      ```
  3. symbol

      Data type "symbol" is a primitive data type. The nature of this type is that the value of this type can be used to create anonymous object properties. This data type is usually used as the key value of an object property-when you want it to be private. For example, symbols of type symbol exist in various built-in JavaScript objects. Similarly, custom classes can also create private members in this way.
      At present, we have basically abandoned the use of symbols, so I will not explain in depth.

## Empty types
### Undefined and Null
A variable that has not been assigned a value after declaration will have a default value of undefined.

A declared variable gives a null value, the value stored in it is empty.

Generally speaking, we are usually used to non-object null value is undefined, object null value is null
## Object
Everything in JavaScript is an object: strings, numbers, arrays, functions...
JavaScript provides multiple built-in objects, such as String, Date, Array, and so on. Objects are just special data types with attributes and methods.
* Boolean can be an object.
* The digital type can be an object.
* String can also be an object
* Date is an object
* Math and regular expressions are also objects
* Array is an object
* Even functions can be objects
* The object is just a special kind of data.
  
# Data type conversion
## Convert data types to string
### Method one:
1. Call the toString() method of the converted type
2. This method will not affect the original variable, it will return the converted result
### Method er: (implicit conversion)
Any value added to a string will be converted into a string, and the string will be combined

We can use this feature to convert an arbitrary data into String.  We only need to add a "" to any data type to convert it to String.

This is an implicit type conversion
  ```javascript
  var c=123;
  C = c + "";  //c='123'
  ```
