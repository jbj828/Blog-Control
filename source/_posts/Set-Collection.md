---
title: Set Collection
date: 2020/1/6 13:46:25
tags: [java, masterclass]
categories: [Java, Masterclass]
thumbnail: ''
permalink: ''
---

Set의 특징
  1. 객체(데이터) 중복 저장 불가능
  2. 저장 순서 보장 X(리스트를 인덱스로 관리 안함)

데이터를 검색하기 위해서는 iterator() 메서드로 Iterator(반복자)를 생성하고 데이터를 가져와야 한다.


Collection c 가 있다고 하자.
같은 element의 다른 Collection을 만들고 똑같은 인자를 제거하기 위해선 어떻게 해야할까?
{% codeblock lang:java %}
Collection<Type> noDups = new HashSet<Type>(c);
{% endcodeblock %}

*Collection class의 메서드
    retainAll() : 저장 된 객체 중 주어진 컬렉션과 공통된 것만 남기고 나머지 삭제

*Array 메서드
    Arrays.asList()
        : 배열을 리스트로 반환
        이 메서드를 사용하여 배열을 캐스팅하여 컬렉션 관련 유틸들을 이용할 수 있다.
        하지만 fixd-size-list를 반환하기 때문에 추가, 삭제 불가능
해결방법: 새로운 리스트를 만듦
{% codeblock lang:java %}
List<String> list = new ArrayList(Arrays.asList(array));
{% endcodeblock %}

Set Collection 연습(출처 : Udemy Programming masterclass for software developers)
{% codeblock lang:java %}
package com.chung.setCollection;

import java.util.Arrays;
import java.util.HashSet;
import java.util.Set;

public class Main {

    public static void main(String[] args) {
        Set<Integer> squares = new HashSet<>();
        Set<Integer> cubes = new HashSet<>();

        for (int i = 1; i <= 100; i++) {
            squares.add(i * i);
            cubes.add(i * i * i);
        }

        System.out.println(squares.size() + ", " + cubes.size()); //100, 100
        Set<Integer> union = new HashSet<>(squares);
        union.addAll(cubes);
        System.out.println(union.size());  //196

        Set<Integer> intersection = new HashSet<>(squares);
        intersection.retainAll(cubes);
        System.out.println(intersection.size()); // 4

        for (int i : intersection) {
            System.out.println(i + " is the square of " + Math.sqrt(i) + ", and the cube of " + Math.cbrt(i));
        }
        //4096 is the square of 64.0, and the cube of 16.0
        //1 is the square of 1.0, and the cube of 1.0
        //64 is the square of 8.0, and the cube of 4.0
        //729 is the square of 27.0, and the cube of 9.0

        Set<String> words = new HashSet<>();
        String sentence = "one day in the year of the box";
        String[] arrayWords = sentence.split(" ");
        words.addAll(Arrays.asList(arrayWords));

        for (String s : words) {
            System.out.println(s);
        }
        //the
        //in
        //year
        //one
        //of
        //box
        //day

        Set<String> nature = new HashSet<>();
        Set<String> divine = new HashSet<>();

        String[] natureWords = {"all", "nature", "is", "but", "art", "unknown", "to", "thee"};
        nature.addAll(Arrays.asList(natureWords));
        String[] divineWords = {"to", "err", "is", "human", "to", "forgive", "divine"};
        divine.addAll(Arrays.asList(divineWords));

        System.out.println("nature - divine");
        Set<String> diff1 = new HashSet<>(nature);
        diff1.retainAll(divine);
        printSet(diff1); //is to

        System.out.println("divine - nature");
        Set<String> diff2 = new HashSet<>(divine);
        diff2.retainAll(nature);
        printSet(diff2); //is to

        Set<String> unionTest = new HashSet<>(nature);
        unionTest.addAll(divine);
        Set<String> intersectionTest = new HashSet<>(nature);
        intersectionTest.retainAll(divine);

        System.out.println("Symmetric Difference");
        unionTest.removeAll(intersectionTest);
        printSet(unionTest);
        //all
        //but
        //art
        //thee
        //err
        //nature
        //forgive
        //divine
        //human
        //unknown
        if (nature.containsAll(divine)) {
            System.out.println("divine is a subset of nature");
        }

        if (nature.containsAll(intersectionTest)) {
            System.out.println("intersection is subset of nature");
        }

        if (divine.containsAll(intersectionTest)) {
            System.out.println("intersection is subset of divine");
        }

    }

    private static void printSet(Set<String> set) {
        System.out.println("\t");
        for (String s : set) {
            System.out.println(s + " ");
        }
        System.out.println();
    }

}
{% endcodeblock %}




<!-- excerpt -->
<!-- toc -->