---
date: '2020/2/16 15:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Trie
---

trie

<!-- more -->

__What is Trie?__

  * It is a search tree, which is typically used to store/search strings in space/time efficient way.
  * In it, any node can store non repetitive multiple characters.
  * Also, every node stores 'link' of next character of the string.
  * Also, every node keeps a track of 'end of String'

<br>

__Why learn Trie?__

  * Used to solve many standard problems in efficient ways
      * Spelling checker
      * Auto Complete string
      * Etc..

<br>

__Creating a Trie__

```
Trie()
  create a blank node
```

<br>

__Inserting a String in Trie__

  * Case#1 - Trie is blank(air)
  * Case#2 - New String's prefix is common with another String's Prefix(aio)
  * Case#3 - New String's prefix is already present as complete String(airk)
  * Case#4 - String to be inserted is already present in Trie

<br>

__Searching a String in Trie__ 

ex)abc

  * Case#1 - String does not exist in Trie(ex) xyz)
  * Case#2 - String exists in Trie(ex) abc)
  * Case#3 - Current String is a prefix of another String. But this string does not exist in Trie.(ex) ab)

<br>

__Deleting a String from Trie__

  * Case#1 - Some other word's prefix is same as Prefix of this word(BCDE, BCKG)
  * Case#2 - This word is a prefix of some other word(BCDE,BCDEF)
  * Case#3 - Some other word is a prefix of this word(BCDE,BC)
  * Case#4 - No one is dependent on this word(k)

<Br>

__Trie-Practical use__

  * Auto Complete
  * Spell Checkers


출처 : "Data Structures & Algorithms" by DS GUY

