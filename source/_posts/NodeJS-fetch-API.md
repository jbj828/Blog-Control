---
date: '2020/3/12 23:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Browser HTTP Requests with Fetch
---

fetch API

<!-- more -->

This chapter shows you how to make HTTP AJAX requests from the browser.
<br>

### The Fetch API

Web APIs provide you with a way to make HTTP requests from JavaScript in the browser. This is done using the `fetch` function. `fetch` expects to be called with the URL as the first argument. It sends off the HTTP request and gives you back the response.

The `fetch` call below is used to fetch the weather for Boston. An if statement is then used to either print the forecast or the error message.

```
fetch('http://localhost:3000/weather?address=Boston').then((response) => {
 response.json().then((data) => {
 if (data.error) {
 console.log(data.error)
 } else {
 console.log(data.location)
 console.log(data.forecast)
 }
 })
}) 
```

<br>

*reference : Udemy 'The Complete Node.js Developer course' by Andrew Mead*
