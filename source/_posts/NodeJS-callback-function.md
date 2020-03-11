---
date: '2020/3/11 13:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Callback Function
---

callback function on nodejs

<!-- more -->

### The Callback Function

A callback function is a function that's passed as an argument to another function.

Callback functions are at the core of asynchronous development. When you perform an asynchronous operation, you will provide Node with a callback function. Node will then call the callback when the async operation is complete. This is how you get access to the results of the async operation, whether it's an HTTP request for JSON data or a query to a database for a user's profile.

```
const add = (a, b, callback) => {
    setTimeout(() => {
        callback(a + b)
    }, 2000)
}

add(1, 4, (sum) => {
    console.log(sum) // Should print: 5
})
```



