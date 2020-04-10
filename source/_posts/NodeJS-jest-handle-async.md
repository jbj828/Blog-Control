---
date: '2020/4/9 12:30:25'
tags:
  - Test
categories:
  - Test
thumbnail: ''
permalink: ''
title: Jest - Testing Asychronous Code
---

Jest - Testing Asychronous Code

<!-- more -->


### Testing Asychronous Code

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
```

The callback function for the first test case accepts a `done` parameter. This lets Jest know that the test function contains asynchronous code. Jest won't determine if the test passed or failed until `done` is called. In the example below, `then` is called to run some code after the numbers are added. This is where the assertion is added and it's where `done` is called.

```
test('Should add two numbers', (done)=>{
  add(2,3).then((sum)=>{
    expect(sum).toBe(5)
    done()
  })
})
```

Using `async/await` is also possible.

```
test('Should add two numbers async/await', async()=>{
  const sum = await add(2,3)
  expect(sum).toBe(5)
})
```

Ref : The Complete Node.js Dev Course by Andrew Mead