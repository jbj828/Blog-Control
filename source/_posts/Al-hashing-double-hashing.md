---
date: '2020/3/29 21:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Hashing - Double Probing
---

hashing - double probing

<!-- more -->

DoubleProbing.java
```
package com.chung;

import java.util.ArrayList;

public class DoubleHashing {
    String[] hashTable;
    int noOfCellsUsedInHashTable;

    DoubleHashing(){
        hashTable = new String[13];
        noOfCellsUsedInHashTable = 0;
    }

    // hash function to be used on keys
    public int simpleASCIIHashFunction(String x, int M){
        char[] ch;
        ch = x.toCharArray();
        int i, sum;
        for(i = 0, sum = 0; i < x.length(); i++){
            sum += ch[i];
        }
        System.out.println("Index from Hash Function : " + sum%M);
        return sum % M;
    }

    // 2nd Hash Function
    int secondHashFunction(String x, int M){
        char[] ch;
        ch = x.toCharArray();
        int i, sum;
        for(i = 0, sum = 0; i < x.length(); i++){
            sum += ch[i];
        }
        while(sum > 13){
            sum = addAllTheDigitsTogether(sum);
        }
        return sum % M;
    }

    private int addAllTheDigitsTogether(int sum){
        int value = 0;
        while(sum > 0){
            value = sum % 10;
            sum = sum / 10;
        }
        return value;
    }

    // get Load Factor
    public double getLoadFactor(){
        double loadFactor = noOfCellsUsedInHashTable * 1.0 / hashTable.length;
        return loadFactor;
    }


    // Insert key in Hash Table
    public void insertKeyInHashTable(String value){
        double loadFactor = getLoadFactor();
        if(loadFactor >= 0.75){
            System.out.println("Load Factor of this hash table is over 0.75. We need to rehash!! ");
            rehashKeys(value);
        } else {
            int firstHashResult = simpleASCIIHashFunction(value, hashTable.length);
            int secondHashResult = secondHashFunction(value, hashTable.length);

            for(int i = 0; i < hashTable.length; i++){
                int index = (firstHashResult + (i * secondHashResult)) % hashTable.length;
                if(hashTable[index] == null){
                    hashTable[index] = value;
                    System.out.println("Succeed in inserting value on the hash table");
                    break;
                }
                System.out.println("Cannot insert the value on the index of " + index);
            }
        }
        noOfCellsUsedInHashTable++;
    }

    // Creates a new hash table and rehashing
    public void rehashKeys(String newString){
        noOfCellsUsedInHashTable = 0;
        ArrayList<String> data = new ArrayList<String>();
        for(String s : hashTable){
            if(s != null){
                data.add(s);
            }
        }
        data.add(newString);
        hashTable = new String[hashTable.length * 2];
        for(String s : data){
            insertKeyInHashTable(s);
        }
    }

    // Search for a given key in hash table
    public boolean searchKeyInHashTable(String value){
        int index = simpleASCIIHashFunction(value, hashTable.length);
            for(int i = index; i < index + hashTable.length; i++){
                int newIndex = i % hashTable.length;
                if(hashTable[newIndex] == value){
                    System.out.println("Found the value!!");
                    return true;
                }
            }
        System.out.println("Cannot find the value");
        return false;
    }

    // Delete Key from Hash Table
    public void deleteKeyFromHashTable(String value){
        int index = simpleASCIIHashFunction(value, hashTable.length);

        for(int i = index; i < index + hashTable.length; i++){
            int newIndex = i % hashTable.length;
            if(hashTable[newIndex] != null && hashTable[newIndex].equals(value)){
                hashTable[newIndex] = null;
                System.out.println("Delete the value on the hash table");
                return;
            }
        }
        System.out.println("No value on the hash Table");
    }

    // Display the hash table
    public void displayTheHashTable(){
        if(hashTable == null){
            System.out.println("Hash Table is not exist");
            return;
        }
        for(int i = 0; i < hashTable.length; i++){
            System.out.println(hashTable[i]);
        }
    }

    // Delete entire hash table
    public void deleteEntireHashTable(){
        hashTable = null;
        System.out.println("Delete the hash table");
    }
}
```