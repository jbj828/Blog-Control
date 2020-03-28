---
date: '2020/3/28 23:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Hashing - Linear Probing
---

hashing - linear probing

<!-- more -->

LinearProbing.java
```
package com.chung;

import java.util.ArrayList;

public class LinearProbing {

    String[] hashTable;
    int noOfCellsUsedInHashTable;

    // Constructor
    LinearProbing(){
        hashTable = new String[13];
        noOfCellsUsedInHashTable = 0;
    }

    // Hash function to be used on keys
    public int simpleASCIIHashFunction(String x, int M){
        char ch[];
        ch = x.toCharArray();
        int i, sum;
        for(sum =0, i = 0; i < x.length(); i++){
            sum = sum + ch[i];
        }
        return sum % M;
    }

    // Returns LoadFactor of HashTable
    public double getLoadFactor(){
        double loadFactor = noOfCellsUsedInHashTable * 1.0 / hashTable.length;
        return loadFactor;
    }

    // Insert key in hash table
    public void insertKeyInHashTable(String value){
        double loadFactor= getLoadFactor();
        if(loadFactor >= 0.75){
            rehashKeys(value);
        } else {
            System.out.println("Inserting \"" + value + "\" in HashTable...");
            int index = simpleASCIIHashFunction(value, hashTable.length);
            for(int i = index; i < index+ hashTable.length; i++){
                int newIndex = i % hashTable.length;
                if(hashTable[newIndex] == null){
                    hashTable[newIndex] = value;
                    System.out.println("Successfully insert the value on the index " + newIndex);
                    break;
                } else{
                    System.out.println("Failed to insert the value on the index " + newIndex);
                }
            }
        }
        noOfCellsUsedInHashTable++;
    }

    // Create a new HashTable and Rehashing
    public void rehashKeys(String newStringToBeInserted){
        noOfCellsUsedInHashTable = 0;
        ArrayList<String> data = new ArrayList<String>();
        for(String s : hashTable){
            if(s != null){
                data.add(s);
            }
        }
        data.add(newStringToBeInserted);
        hashTable = new String[hashTable.length * 2];
        for(String s : data){
            insertKeyInHashTable(s);
        }
    }

    // Search for a given key in Hash Table
    public boolean searchKeyInHashTable(String key) {
        int index = simpleASCIIHashFunction(key, hashTable.length);

        for (int i = index; i < index + hashTable.length; i++) {
            int newIndex = i % hashTable.length;
            if (hashTable[newIndex] != null && hashTable[newIndex].equals(key)) {
                System.out.println("The key is found on the index of " + newIndex);
                return true;
            }
        }
        System.out.println("Not Found");
        return false;
    }

    // Delete Key from HashTable
    public void deleteKeyInHashTable(String key){
        int index = simpleASCIIHashFunction(key, hashTable.length);

        for(int i = index; i < index + hashTable.length; i++){
            int newIndex = i % hashTable.length;
            if(hashTable[newIndex] != null && hashTable[newIndex].equals(key)){
                hashTable[newIndex] = null;
                System.out.println("Delete the key you want");
                return;
            }
        }
        System.out.println("Failed to delete the key");
    }

    // Display the Hash Table
    public void displayHashTable(){
        if(hashTable == null){
            System.out.println("No hashTable");
            return;
        }
        for(int i = 0; i < hashTable.length; i++){
            System.out.println(hashTable[i] + "\n");
        }
    }

    // Deletes entire Hash table
    public void deleteEntireHashTable(){
        if(hashTable == null){
            System.out.println("No hash table!! Check again!!");
            return;
        }
        hashTable = null;
        System.out.println("Completely deleted!");
    }

}
```







