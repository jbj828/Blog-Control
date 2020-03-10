---
date: '2020/3/10 13:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Debugging Node.js
---

Debugging

<!-- more -->

### Console.log


<br>

### Node Debugger

  * NodeJS' built-in Debugger
  * console창에 `node --inspect-brk app.js` : window용 // Mac은 `node inspect app.js`
  * visit __*chrome://inspect*__ in the Chrome Browser
  * Click `inspect` to open up the developer tools.
  * Click `play` icon on the right side of the monitor.
  * You can add breakpoints into your application to stop it at a specific point in the code. 
      * `debugger`를 입력

  * chrome창에서 아무 것도 안뜨면 `configure` 에서 IP주소랑 포트 입력
