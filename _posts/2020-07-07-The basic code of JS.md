---
layout: post
title: The basic code of JS
subtitle:
date: 2020-07-07
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
---
Today, I has learned JavaScript basic code. Systematic learning can indeed achieve a deeper understanding.

Now, I write some things about that.

1. Expressions and statements
2. Identifier rules
3. Judge sentences
   * if else 
   * switch

4. Loop statement
   * while
   * for
   * break and continue
  
5. Label

## Expressions and statements
In the JavaScript, expression and statement are different. Expression will get a value, function or function return value. For example:
* get a value
  ```javascript
  111+111 //value is 3
  ```
* get a function
  ```javascript
  console.log // value is itself
  ```
  ![](/img/item/item5-1.jpg)
* get a function return value
  ```javascript
  add(1,2); // value is function return value
  function add(x,y){
    return x+y
  }
  ```
Statement is similar to background,a statement performs an action. If and loop statement are belong to this.
```javascript
var a;                //set a global variable
function add(){
  var x,y;            //set a local variable
}
if(){}
  else{}
```
**Important notices** :

  There are case sensitive, `var a` and `var A`, `object` and `Object`, `function` and `Function` are different.

  **Moreover**, most of the spaces and carriage returns have no effect on the sentence.
  ```javascript
  var a=1;
  console.log(a);             //value is 1
  var a     =       2;    
  console.log(a);             //value is 2   
  var a
  =
  3;                      
  console.log(a);             //value is 3   
```
  ![](/img/item/item5-2.jpg)
However, you cannot add a carriage return after the function return value, because when there is no expression or statement after the return, it will automatically add a carriage return to end.
  ```javascript
  var a=1;
  function test1(a){
    b=a;
    return b
  }
  function test2(a){
    c=a;
    return
     c
  }
  console.log(test1(a)); //value is 1 
  console.log(test2(a)); //value is undefined
```
 ![](/img/item/item5-3.jpg)
## Identifier rules
Commonly used identifiers can be Unicode letters, $ or _ (underscore).
* Usually the characters at the beginning should be the ones mentioned above
* Numbers cannot start
* Variable names are also identifiers
```javascript


var _12 = 11; /*Correct Wording*/
var $2 = 44;
var cc2 = 3;
var _______ = 6; 


var 23_;      /*Incorrect Wording*/
var 3$;
```
It is recommended that the underline should not exceed 2, although it is correct, it is not convenient to remember. $, this symbol is used in Jquery and has similarities.

## Judge sentences
I will not say the specific usage of if and switch statements, I believe everyone is very clear. I will talk about what they need to pay attention to.
### If else
* In the if statements, if { } just contain one statement, it can ignore { }, but I don't recommend, because it will make statements confuse, such as 
`if(b === 3) a=1;else a=2;`
 ![](/img/item/item5-4.jpg)
* I recommend original writing.
  ```javascript
  if(Expressions){
    statements
  }else if(Expressions){
    statements
  }else{
    statements
  }
  ```
### Switch
Switch can be said to be an upgraded version of if. But it is not recommended. It basically has to be used with break.
  ```javascript
  switch(expression){
      case constant-expression  :
        statements;
        break; 
      case constant-expression  :
        statements;
        break; 
      default :
        statements;
  }
  ```
  Notices,if you forget add `break` in the end of every case, the statement will continue run. For example:
  ```javascript
  switch(1){
      case 1  :
        console.log("active");
      case 2  :
        console.log("active"); 
      case 3  :
        console.log("active");
        break; 
      default :
        console.log("finish");
  }
  ```
   ![](/img/item/item5-5.jpg)
## Loop statement
### While
Its execution sequence is to judge whether the expression is true, skip directly if it is not true, execute the loop body for true, and then judge the expression.
```javascript
while(expression){
  statements;
}
```
### for
Its execution order is to execute statement 1 first, then judge whether expression 2 is true, and end the statement if it is not true. If true, execute statement 3, execute statement 4 after the end, and then determine whether expression 2 is true.
```javascript
for(statement 1;expression 2;statement 4){
  statement 3;
}
```
It should be noted that statement 4 is executed after statement 3 ends.
```javascript
for(var i=0;i<5;i++){
  console.log(i);     //result is 0,1,2,3,4
}
console.log(i);       //result is 5
```
   ![](/img/item/item5-6.jpg)
### Break and continue
Break and continue both use in loop statements, but break can jump out switch statement as I said before.
The function of break is to end the most recent cycle. (Note the most recent one). continue is to end the current loop and enter the next loop. (Also the closest)
```javascript
for(var i=0;i<5;i++){
  break;
  console.log("i =" + i);     //no display
}
console.log("i =" + i);       //result is 0
for(var k=0;k<5;k++){
  continue;
  console.log("k =" + k);     //no display
}
console.log("k =" + k);       //result is 5
```
   ![](/img/item/item5-7.jpg)
## Label
The syntax of label is rarely used, and it is very similar to the composition of object. The effect is to add an identifiable identifier in front of the statement. It is equivalent to storing a statement in a variable, similar to the function name of the function.

Label statements are generally used with break and continue or code blocks.
```javascript
foo: {
    console.log('entry');
    break foo;
    console.log('break');
}
console.log('print');
```
   ![](/img/item/item5-8.jpg)
