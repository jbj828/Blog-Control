---
date: '2020/3/12 23:46:25'
tags:
  - ES6
categories:
  - ES6
thumbnail: ''
permalink: ''
title: Default Function Parameters
---

es6

<!-- more -->

### Default Function Parameters

ES6 provides a new syntax to set default values for function arguments.

Function parameters are `undefined` unless an argument value is provided when the function is called. ES6 now allows function parameters to be configured with a custom default value.

```
const greeter = (name = 'user', age) => {
 console.log('Hello ' + name)
}
greeter('Andrew') // Will print: Hello Andrew
greeter() // Will print: Hello user
```

This syntax can also be used to provide default values when using ES6 destructuring. The `transaction` function below shows this off by providing a default value for `stock`

```
const transaction = (type, { label, stock = 0 } = {}) => {
 console.log(type, label, stock)
}
transaction('order')
```


*reference : Udemy 'The Complete Node.js Developer course' by Andrew Mead