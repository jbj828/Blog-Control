---
date: '2020/4/18 23:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test - Code Signal Intro 3
---

Coding Test - Code Signal Intro 3

<!-- more -->

### Add Border

```
function addBorder(picture) {
    var width = picture[0].length + 2

    return [
        '*'.repeat(width),
        ...picture.map(line => `*${line}*`),
        '*'.repeat(width)
    ]
}
```

### Are Similar

```
function areSimilar(a,b){
    const aDiff = a.filter((v,i) => v != b[i])
    const bDiff = b.filter((v,i) => v != a[i])
    return aDiff.length == 0 || aDiff.length == 2 && aDiff.join('') == bDiff.reverse().join('')
}
```

