---
date: '2020/4/9 18:30:25'
tags:
  - Test
categories:
  - Test
thumbnail: ''
permalink: ''
title: Jest - Testing an Express Application
---

Jest - Testing an Express Application

<!-- more -->

We will set up the Express API to be easily testable. This involves settings up a test environment as well as configuring Jest to work with Node.

### Creating a Test Environment

Creating the test environment requires `test.env` to be added to the `config` directory. The contents will be identical to `dev.env`, with the exception of the MongoDB connection string. The test environment should use a separate database such as `task-manager-api-test`. This will prevent the test cases from messing with development data.

With the environment in place, update the `test` script to load the enviroment file in. That would be `env-cmd ./config/test.env jest --watch`.

### Configuring Jest

By default, Jest is expecting to run in the browser. You can use Jest with Node, but you'll need to configure Jest to enable support. Jest can be configured by adding a `jest` property in `pacakage.json`. The configuration below sets `testEnvironment` to `node` to ensure that Jest runs correctly in Node.js.

```
{
  "jest": {
      "testEnvironment": "node"
  }
}
```

Next, we'll add tests for the Express API. Each test case will focus on testing a specific endpoint, making assertions about the response from the server.

### Testing with Supertest

Supertest allows you to easily test Express apps.

```
npm i supertest --save-dev
```

Now, supertest can be used to test an endpoint. The test case below tests that new users can sign up for accounts. All the account data provided is valid, so a new account should be created.

Step one is to pass the express `app` to `request`. Next, supertest methods can be chained together to fit the needs of your tests. `post` is used to make an HTTP POST request to `/users`. `send` is used to send the correct JSON data to the server. `expect` is used to assert that the response status code is correct. In this case, a successful signup should result in a 201 status code.

```
const request = require('supertest')
const app = require('../src/app')

test('Should signup a new user', async () => {
    await request(app).post('/users').send({
        name: "Jay",
        email: "jay@exaple.com",
        password: 'MyPass777!'
    }).expect(201)
})
```








Ref : The Complete Node.js Dev Course by Andrew Mead