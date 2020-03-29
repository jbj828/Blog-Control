---
date: '2020/3/29 17:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Hashing - Quadratic Probing
---

Hashing - Quadratic Probing

<!-- more -->

QuadraticProbing.java
```
package com.chung;

import java.util.ArrayList;

public class QuadraticProbing {

     String[] hashTable;
     int noOfCellUsedInHashTable;

     QuadraticProbing(){
         hashTable = new String[13];
         noOfCellUsedInHashTable = 0;
     }

     // Hash Function to be used on keys
    public int simpleASCIIHashFunction(String x, int M){
         char ch[];
         ch = x.toCharArray();
         int sum, i;
         for(i = 0, sum = 0; i < ch.length; i++){
             sum += ch[i];
         }
         return sum % M;
    }

    // Returns load factor of Hash Table
    public double getLoadFactor(){
         double loadFactor = noOfCellUsedInHashTable * 1.0 / hashTable.length;
         return loadFactor;
    }

    // Insert Key in Hash Table
    public void insertKeyInHashTable(String value){
         double loadFactor = getLoadFactor();
         if(loadFactor >= 0.75){
             System.out.println("The hash table is full. Rehash the table");
             rehashing(value);
         } else {
             System.out.println("Inserting key in Hash Table");
             int index = simpleASCIIHashFunction(value, hashTable.length);
             int counter = 0;
             for(int i = index; i < index + hashTable.length; i++){
                 int newIndex = (index + (counter*counter)) % hashTable.length;
                 if(hashTable[newIndex] == null){
                     hashTable[newIndex] = value;
                     break;
                 } else {
                     System.out.println("Index is not blank");
                 }
                 counter++;
             }
         }
         noOfCellUsedInHashTable++;
    }


    // Create a new Hash Table and Rehashing
    public void rehashing(String newString){
        noOfCellUsedInHashTable = 0;
        ArrayList<String> data = new ArrayList<String>();
        for(String s : hashTable){
            if(s != null)
                data.add(s);
        }
        data.add(newString);
        hashTable = new String[hashTable.length *2];
        for(String s : data){
            insertKeyInHashTable(s);
        }
    }

    // Search for a given key in Hash Table
    public boolean searchKeyOnHashTable(String key){

         int index = simpleASCIIHashFunction(key, hashTable.length);
         for(int i = index; i < index + hashTable.length; i++){
             int newIndex = i % hashTable.length;
             if(hashTable[newIndex] != null && hashTable[newIndex].equals(key)){
                 System.out.println("Found the key!!");
                 return true;
             }
         }
         System.out.println("Cannot find the key");
         return false;
    }

    // Delete Key From Hash Table
    public void deleteKeyFromHashTable(String key){
         int index = simpleASCIIHashFunction(key, hashTable.length);

         for(int i = index; i < index + hashTable.length; i++){
             int newIndex = i % hashTable.length;
             if(hashTable[newIndex] != null && hashTable[newIndex].equals(key)){
                 hashTable[newIndex] = null;
                 System.out.println("Delete the key");
                 return;
             }
         }
         System.out.println("Cannot find the key");
    }

    // Display the hash table
    public void displayTheHashTable(){
         if(hashTable == null){
             System.out.println("HashTable is not exist");
         } else{
             for(int i = 0; i < hashTable.length; i++){
                 System.out.println(hashTable[i]);
             }
         }
    }

    // Delete Entire hash table
    public void deleteEntireHashTable(){
         hashTable = null;
        System.out.println("Hash Table is deleted");
    }
}
```