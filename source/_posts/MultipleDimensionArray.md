---
date: '2020/1/29 15:46:25'
tags:
  - Algorithm
categories:
  - Alogrithm
thumbnail: ''
permalink: ''
title: Two Dimension Array
---

* Declaring, instanciating, initializing a 2D Array

<!-- more -->

  * Declare               ------------------------- O(1)
    * dataType[][] arr
    * ex: int[][] arr

  * Instanciation of Array -------------------------O(1)
    * arrayRefVar = new datatype[row][col];
    * ex: arr = new int[2][3];

  * Initialization        --------------------------O(mn)
    * a[0][0]=10;
    * a[0][1]=20;
    * a[0][2]=30;
    * a[1][0]=40;
      .....


  * Declaring, instanciating, initializing -----------O(1)
    * int[][] arr = {{1,2,3},{4,5,6}};  


* When to Use/Avoid Array
  * When to use
      * When there is a need to store multiple similar type of data
      * When random access is regular affair(접근할 때 바로 인덱스 넣으면 접근가능하기에 time complexity가 O(1)이다)

  * When to avoid
      * Data to be stored are non-homogenous(데이터 종류가 같지 않을 경우)
      * When number of data to be stored is not known in advance.