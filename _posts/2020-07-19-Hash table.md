---
layout: post
title: Hash table
subtitle:
date: 2020-07-19
author: BY Aaron
header-img: img/tag-bg.jpg
catalog: true
tags:
  - JavaScript
  - Algorithm
---
A hash table is a data structure that directly accesses the memory storage location based on keywords. Through the hash table, a certain correspondence relationship is established between the storage location of the data element and the keyword of the data element, and the function of establishing this correspondence relationship Hash function.

In fact, the object of JS can be regarded as a truncated hash table.

## Hash table structure
The characteristics of arrays are: easy to address, difficult to insert and delete; and the characteristics of linked lists are: difficult to address, easy to insert and delete, Hash table combines the characteristics of the two, to make a kind of easy addressing, easy to insert and delete data structure.

## The working principle of hash table:

The first step is to get the specific hash value according to the given key and hash algorithm, which is the corresponding array subscript.

In the second step, the pointer stored in the subscript is obtained according to the array subscript. If the pointer is empty, there is no such key-value pair, otherwise the chained array is obtained based on the pointer.

Traverse this chained array, take out the Key and compare with the given Key respectively, if you find a Key equal to the given key, that is, there is the `<Key,Value>` key-value pair to be found in this hash table, then you can This key-value pair performs related operations; if it cannot be found, it means there is no such key-value pair.

## Hash function construction method
1. Direct addressing method

    The method is to take a linear function value of the keyword as a hash address. It can be simply expressed as:
    ```
    Hash(K)=aK mod C
    ```

    The advantage is that there is no conflict, but the disadvantage is that the space complexity may be very high, which is suitable for the case of fewer elements;

2. In addition to the remainder method

    It uses the remainder of the data element key divided by a constant as the hash address. This method is simple to calculate and has a wide range of applications. It is the most frequently used hash function, which can be expressed as:
    ```
    Hash(K)=K mod C
    ```

    The key to this method is the selection of a constant. The general requirement is to be close to or equal to the length of the hash table itself. Theoretical studies have shown that the constant is best when a prime number is used.

3. Digital analysis method

    This method is to use some even-valued digital bits in the data element keywords as the hash address, so as to avoid conflicts as much as possible, but this method is only suitable for the case where all keywords are known. Not suitable for designing a more general hash table.
## Hash collision
When constructing a hash table, there is such a problem. For two different keywords, the same hash address is obtained when calculating the hash address through our hash function. We call this phenomenon a hash collision

### Solution
1. Open addressing method

    It is a method of obtaining a new free memory unit address through a certain hash function with the hash address where the hash conflict occurs as an argument. The hash conflict function of the open addressing method is usually a group.

2. Linked list method

    When there is no conflict, the data element is directly stored; when the conflict occurs, the conflicting data element is additionally stored in the singly linked list.