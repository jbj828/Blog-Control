---
date: '2020/3/9 13:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: JSON
---


study JSON

<!-- more -->

__JSON__ :  Javascript 객체 문법을 따르는 문자 기반의 데이터 포맷


JavaScript Object Notation (JSON)은 Javascript 객체 문법으로 구조화된 데이터를 표현하기 위한 문자 기반의 표준 포맷이다. 웹 어플리케이션에서 데이터를 전송할 때 일반적으로 사용한다(서버에서 클라이언트로 데이터를 전송하여 표현하려거나 반대의 경우).

```
const fs = require('fs');

// const book = {
//     title: 'Ego is the enemy',
//     author: 'Ryan Holiday'
// }

// const bookJSON = JSON.stringify(book)
// fs.writeFileSync('1-json.json', bookJSON);

// const parsedData = JSON.parse(bookJSON);
// console.log(parsedData.author);

// const dataBuffer = fs.readFileSync('1-json.json');
// const dataJSON = dataBuffer.toString();
// const data = JSON.parse(dataJSON);
// console.log(data.title);


const dataBuffer = fs.readFileSync('1-json.json');
const data = JSON.parse(dataBuffer);
data.name = 'Jay'
data.age = '26'
const newData = JSON.stringify(data);
fs.writeFileSync('1-json.json', newData);
```

