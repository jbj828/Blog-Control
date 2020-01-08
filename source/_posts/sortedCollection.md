---
date: '2020/1/7 20:46:25'
tags:
  - java, masterclass
categories:
  - Java, Masterclass, challenge
thumbnail: ''
permalink: ''
title: Basket Challenge
---



### Main.java
{% codeblock lang:java %}
package com.chung;

public class Main {

    private static StockList stockList = new StockList();

    public static void main(String[] args) {
        StockItem temp = new StockItem("bread", 0.86, 10);
        stockList.addStock(temp);

        temp = new StockItem("Orange", 0.23, 2);
        stockList.addStock(temp);

        temp = new StockItem("coffee", 0.1, 3);
        stockList.addStock(temp);

        temp = new StockItem("chair", 62.0, 10);
        stockList.addStock(temp);

        temp = new StockItem("cup", 0.50, 200);
        stockList.addStock(temp);

        temp = new StockItem("door", 72.95, 4);
        stockList.addStock(temp);

        temp = new StockItem("juice", 2.50, 36);
        stockList.addStock(temp);

        temp = new StockItem("phone", 96.99, 35);
        stockList.addStock(temp);

        temp = new StockItem("towel", 2.40, 80);
        stockList.addStock(temp);

        temp = new StockItem("vase", 8.76, 40);
        stockList.addStock(temp);

        System.out.println(stockList);

        for (String s : stockList.Items().keySet()) {
            System.out.println(s);
        }

        Basket javitsBasket = new Basket("Javit");
        sellItem(javitsBasket, "bread", 1);
        System.out.println(javitsBasket);



    }

    public static int sellItem(Basket basket, String item, int quantity) {
        StockItem stockItem = stockList.get(item);
        if (stockItem == null) {
            System.out.println("We don't sell " + item);
            return 0;
        }
        if (stockList.sellStock(item, quantity) != 0) {
            basket.addToBasket(stockItem, quantity);
            return quantity;
        }
        return 0;
    }
}
{% endcodeblock %}

#### Result

Stock List
door : price 72.95. There are 4 in stock. Value of times : 291.80
bread : price 0.86. There are 10 in stock. Value of times : 8.60
phone : price 96.99. There are 35 in stock. Value of times : 3394.65
towel : price 2.4. There are 80 in stock. Value of times : 192.00
chair : price 62.0. There are 10 in stock. Value of times : 620.00
coffee : price 0.1. There are 3 in stock. Value of times : 0.30
vase : price 8.76. There are 40 in stock. Value of times : 350.40
juice : price 2.5. There are 36 in stock. Value of times : 90.00
Orange : price 0.23. There are 2 in stock. Value of times : 0.46
cup : price 0.5. There are 200 in stock. Value of times : 100.00
Total stock value 5048.209999999999
door
bread
phone
towel
chair
coffee
vase
juice
Orange
cup

Shopping basket Javit contains 1 item
bread : price 0.86. 1 purchased
Total cost 0.86


### StockItem.java
{% codeblock lang:java %}
package com.chung;

public class StockItem implements Comparable<StockItem> {

    private final String name;
    private double price;
    private int quantityStock;

    public StockItem(String name, double price) {
        this.name = name;
        this.price = price;
        this.quantityStock = 0;
    }

    public StockItem(String name, double price, int quantityStock) {
        this.name = name;
        this.price = price;
        this.quantityStock = quantityStock;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }

    public int getQuantityStock() {
        return quantityStock;
    }

    public void setPrice(double price) {
        if (price > 0.0) {
            this.price = price;
        }
    }

    public void adjustStock(int quantity) {
        int newQuantity = this.quantityStock + quantity;
        if (newQuantity >= 0) {
            this.quantityStock = newQuantity;
        }
    }

    @Override
    public boolean equals(Object obj) {
        System.out.println("Entering StockItem.equals");
        if (obj == this) {
            return true;
        }
        if ((obj == null) || (obj.getClass() != this.getClass())) {
            return false;
        }
        String objName = ((StockItem) obj).getName();
        return this.name.equals(objName);
    }

    @Override
    public int hashCode() {
        return this.name.hashCode() + 31;
    }

    @Override
    public int compareTo(StockItem o) {
        if(this == o){
            return 0;
        }
        if(o != null){
            return this.name.compareTo(o.getName());
        }

        throw new NullPointerException();
    }

    @Override
    public String toString() {
        return this.name + " : price " + this.price;
    }
}

{% endcodeblock %}


### StockList.java
{% codeblock lang:java %}
package com.chung;

import java.util.Collections;
import java.util.HashMap;
import java.util.Map;

public class StockList {

    private final Map<String, StockItem> list;

    public StockList() {
        this.list = new HashMap<>();
    }

    public int addStock(StockItem item){
        if(item != null) {
            StockItem inStock = list.getOrDefault(item.getName(), item);

            if(inStock != item){
                item.adjustStock(inStock.getQuantityStock());
            }

            list.put(item.getName(), item);
            return item.getQuantityStock();
        }
        return 0;
    }

    public int sellStock(String item, int quantity){
        StockItem inStock = list.getOrDefault(item, null);

        if((inStock != null) && (inStock.getQuantityStock() >= quantity) && (quantity > 0)){
            inStock.adjustStock(-quantity);
            return quantity;
        }
        return 0;
    }

    public StockItem get(String key){
        return list.get(key);
    }

    public Map<String, StockItem> Items(){
        return Collections.unmodifiableMap(list);
    }

    @Override
    public String toString() {
        String s = "\nStock List\n";
        double totalCost = 0.0;
        for(Map.Entry<String, StockItem> item: list.entrySet()){
            StockItem stockItem = item.getValue();

            double itemValue = stockItem.getPrice() * stockItem.getQuantityStock();

            s = s + stockItem + ". There are " + stockItem.getQuantityStock() + " in stock. Value of times : ";
            s = s + String.format("%.2f", itemValue) + "\n";
            totalCost += itemValue;
        }

        return s + "Total stock value " + totalCost;
    }
}
{% endcodeblock %}

### Basket.java
{% codeblock lang:java %}
package com.chung;

import java.util.Collections;
import java.util.HashMap;
import java.util.Map;

public class Basket {
    private final String name;
    private final Map<StockItem, Integer> list;

    public Basket(String name) {
        this.name = name;
        this.list = new HashMap<>();
    }

    public int addToBasket(StockItem item, int quantity) {
        if ((item != null) && (quantity > 0)) {
            int inBasket = list.getOrDefault(item, 0);
            list.put(item, inBasket + quantity);
            return inBasket;
        }
        return 0;
    }

    public Map<StockItem, Integer> Items() {
        return Collections.unmodifiableMap(list);
    }

    @Override
    public String toString() {
        String s = "\nShopping basket " + name + " contains " + list.size() + ((list.size() == 1) ? " item" : " items") + "\n";
        double totalCost = 0.0;
        for (Map.Entry<StockItem, Integer> item : list.entrySet()) {
            s = s + item.getKey() + ". " + item.getValue() + " purchased\n";
            totalCost += item.getKey().getPrice() * item.getValue();
        }
        return s + "Total cost " + totalCost;
    }
}
{% endcodeblock %}

(출처 : Udemy Programming masterclass for software developers)

<!-- excerpt -->
<!-- toc -->