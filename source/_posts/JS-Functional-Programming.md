---
date: '2020/5/13 22:46:25'
tags:
  - Javascript
categories:
  - Javascript
thumbnail: ''
permalink: ''
title: Functional Programming on JS
---

Functional Programming on JS

<!-- more -->

```
// Fibonachi with Functional Programming
var fibo = (function () {
  var cache = { "0": 0, "1": 1 };

  var func = function (n) {
    if (typeof cache[n] === "number") {
      result = cache[n];
    } else {
      result = cache[n] = func(n - 1) + func(n - 2);
    }

    return result;
  };
  return func;
})();

console.log(fibo(10));

// Another way, defining cacher first
// and then put factorial or fibonacci
var cacher = function (cache, func) {
  var calculate = function (n) {
    if (typeof cache[n] === "number") {
      result = cache[n];
    } else {
      result = cache[n] = func(calculate, n);
    }
    return result;
  };
  return calculate;
};

var fact = cacher({ "0": 1 }, function (func, n) {
  return n * func(n - 1);
});

var fibo = cacher({ "0": 0, "1": 1 }, function (func, n) {
  return func(n - 1) + func(n - 2);
});

console.log(fact(10));
console.log(fibo(10));

// call method
function example() {
  console.log(Array.prototype.join.call(arguments));
}

example(1, "string", true); // "1,string,true"

// Currying
function calculate(a, b, c) {
  return a * b + c;
}

function curry(func) {
  var args = Array.prototype.slice.call(arguments, 1);

  return function () {
    return func.apply(null, args.concat(Array.prototype.slice.call(arguments)));
  };
}

var new_func1 = curry(calculate, 1);
```