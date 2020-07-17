---
layout: post
title: Four simple algorithms
subtitle:
date: 2020-07-18
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - Algorithm
---
1. Select sort
   ```javascript
   let arr=[];
   for(let i=0; i<10;i++){
     arr[i] = Math.round(Math.random()*100);
   }            //create array

   let min=(numbers)=>{
     if(numbers.length > 2){
       return min([numbers[0],min(numbers.slice(1))]);
     }else {
       return numbers[0]>numbers[1] ? numbers[1] : numbers[0]
       }    
   };           //find min value

   let sort=(numbers)=>{
     let passing=[];
     let save=[];
     for(let j=0; j<arr.length;j++){
       passing[j]=arr[j];
     }
     for(let k=0;k<numbers.length;k++){
       save[k]=min(passing);
       passing.splice(passing.indexOf(save[k]),1);
     }
     return save;
   }
   ```
2. Quickly sort
   ```javascript
    let arr=[];
    for(let i=0; i<10;i++){
    arr[i] = Math.round(Math.random()*100);
    }            //create array

    let quickSort=(arr)=>{
    if(arr.length <= 1) {return arr};
    let index = Math.floor(arr.length/2);
    let mid = arr.splice(index,1)[0];
    let left = [];
    let right = [];
    for(let i=0;i<arr.length;i++){
        arr[i]<mid ? left.push(arr[i]) : right.push(arr[i])
    }
    return quickSort(left).concat(mid,quickSort(right))
    }
    quickSort(arr);
    console.log(quickSort(arr));
    ```
3. Merge sort
    ```javascript
    let arr=[];
    for(let i=0; i<10;i++){
    arr[i] = Math.round(Math.random()*100);
    }       //create array

    let mergeSort=(arr)=>{
    let k = arr.length;
    if(k === 1) {return arr};
    let left = arr.slice(0,Math.floor(k/2));
    let right = arr.slice(Math.floor(k/2));
    return merge(mergeSort(left),mergeSort(right))
    }
    let merge=(a,b)=>{
    if(a.length===0) return b;
    if(b.length===0) return a;
    return a[a.length-1]>b[0] ? [b[0]].concat(merge(a, b.slice(1))) :
    [a[0]].concat(merge(a.slice(1), b))
    }

    mergeSort(arr);
    console.log(mergeSort(arr));
    ```
4. Count sort
    ```javascript
    let arr=[];
    for(let i=0; i<10;i++){
    arr[i] = Math.round(Math.random()*100);
    }       //create array

    let countSort = arr =>{
        let hashTable = {}, max = 0, result = []
        for(let i=0; i<arr.length; i++){ 
            if(!(arr[i] in hashTable)){
            hashTable[arr[i]] = 1
            }else{
            hashTable[arr[i]] += 1
            }
            if(arr[i] > max) {max = arr[i]}
        }
        for(let j=0; j<=max; j++){ 
            if(j in hashTable){
            for(let i = 0; i<hashTable[j]; i++){
                result.push(j)
            }
            }
        }
        return result
    }
    console.log(countSort(arr))
    ```