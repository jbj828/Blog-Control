---
date: '2020/3/17 20:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Async/Await
---

async/await

<!-- more -->


These provide an improved syntax for working with promises. You’ll be able to write complex asynchronous code that looks like normal synchronous code. This makes it much easier to write and maintain asynchronous code.

```
const add = (a, b) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (a < 0 || b < 0) {
                return reject('Numbers must be non-negative')
            }
            resolve(a + b);
        }, 2000)
    })
}

const doWork = async () => {
    const sum = await add(1, 99)
    const sum2 = await add(sum, 50)
    const sum3 = await add(sum2, -10)
    return sum3
}

doWork().then((result) => {
    console.log('result', result)
}).catch((e) => {
    console.log('e', e)
})
```


