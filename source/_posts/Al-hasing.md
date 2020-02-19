---
date: '2020/2/18 23:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Hashing
---

Hashing

<!-- more -->


<br>

__What is Hashing__

  * Hashing is a method of sorting and indexing data. The idea behind hasing is to allow large amounts of data to be indexed using keys commonly created by formulas.
  * 해시함수란 데이터의 효율적 관리를 목적으로 임의의 데이터를 고정된 길이의 데이터로 매핑하는 함수이다. 매핑 전 원래 데이터의 값을 키(key), 매핑 후 데이터의 값을 해시값(hash value), 매핑하는 과정 자체를 해싱(hashing) 이라고 한다.


__Why we need Hashing__

  * Time efficient
{% asset_img "hasing1.png" 400 200 "hashing time complexity" %}

<br>

__Terminologies__

  * Hash Function : A hash function is any function that can be used to map data of arbitrary size to data of fixed size.
  * Key : Input data given by user
  * Hash Value : The values returned by a hash function are called hash values, hash codes, digests, or simply hashes.
  * Hash Tables : It is a data structure which implements an associative array abstract data type, a structure that can map keys to values.
  * Collision : A collision occurs when two different key to a hash function produce the same output called hash values.
  
  {% asset_img "hashing2.png" 600 500 "hashing structure" %}

<br>

__Characteristics of good Hash function__

  * It distributes hash values uniformly across the hash table.
  * The hash function uses all the input data.


<br>

#### Collision Resolution Techniques
{% asset_img "hashing3.png" 400 300 "hashing structure" %}

<br>

  * Direct Chaining 
      * Implements the buckets as linked lists. Colliding elements are stored in these lists.
       {% asset_img "hashing4.png" 400 300 "Direct Chaining" %}
       <br>
  * Open Addressing
      * Colliding elements are stored in other vacant buckets. During storage and lookup, there are found through so called "probing"
    <br>

    * Linear Probing :
      * Linear probing is a strategy for resolving collisions by replacing the new key into the closest following empty cell.
      {% asset_img "hashing5.png" 400 300 "Linear Probing" %}
      <br>

    * Quadratic Probing : 
      * Qudratic probing operates by taking the original hash index and adding successive values of an arbitrary quadratic polynomial until an open slot is found.
      {% asset_img "hashing6.png" 400 300 "Quadratic Probing" %}
      <br>
    * Double Hashing :
      * Interval between probes is computed by another hash function.
        {% asset_img "hashing7.png" 400 300 "Double Hashing" %}
      
<br>

__What happens when Hash Table is full?__

  * Direct Chaining 
      * This situation will never arise.

  * Open Addressing
      * Need to create 2x size of current table and redo Hashing for existing keys.
    {% asset_img "hashing8.png" 400 300 "resizeHashTable" %}

<br>

__Pros & Cons of Collision Resolution Technique__

  * Direct Chaining
      * No fear of exhausting Hash Table buckets.
      * Fear of big Linked Lists(can effect performance big time).

  * Open Addressing
      * Easy implementation
      * Fear of exhasuting Hash Table buckets.

1. If input size is known then always use "Open Addressing", else can use any of the two.

2. If Deletion is very high, then we should always go for 'Direct Chaining'. Because when we delet a lot on 'Open Addressing', there's gonna have lots of Hole and it will make problem. We can do "restruction", but it's not that efficient way.

<br>


__Practical Use of Hashing__

  * Password Verification
  * File System : File path is mapped to physical location on disk.

<br>

__Pros & Cons of Hashing__

  * Pros
      * On an average Insertion/Deletion/Search operation takes O(1) time.
  
  * Cons
      * In the worst case Insertion/Deletion/Search might take O(n) time(when hash function is not good enough)



<br>
출처 : "Data Structures & Algorithms" by DS GUY

