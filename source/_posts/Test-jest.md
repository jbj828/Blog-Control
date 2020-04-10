---
date: '2020/4/8 12:30:25'
tags:
  - Test
categories:
  - Test
thumbnail: ''
permalink: ''
title: Jest Testing Framework
---

Jest Testing Framework

<!-- more -->

#### Setting up Jest

`npm i jest --save-dev`

Next, create a `test` script in `package.json`. The script itself is `jest`. This allows you to use `npm test` to run the Jest test suite.

```
"scripts": {
    "start": "node src/index.js",
    "dev": "env-cmd -f ./config/dev.env nodemon src/index.js",
    "test": "jest"
  },
```

Now, you'll need to create a test suite. This is a file in your project that ends with `.test.js`. The file extension allows Jest to find and run the test suites for your project.

#### Creating a Test Case

You can add a test case to a test suite using the `test` function. Jest provides various functions as global variables in your test suite files. `test` is one of them. The first argument to `test` is the name of your test case. The second argument to `test` is the test function itself.

If the test function throws an error, the test cast will fail. If the test function doesn't throw an error, the test case will pass.

```
test('Hello World', ()=>{

})

test('This should fail', ()=>{
  throw new Error("Failure!")
})
```

Ref : The Complete Node.js Dev Course by Andrew Mead