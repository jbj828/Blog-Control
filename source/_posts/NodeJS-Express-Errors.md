---
date: '2020/4/5 22:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Handling Express Errors
---

Handling Express Errors


<!-- more -->

We'll customize the errors that multer provides. This will give you complete control of what sort of response the client gets when their upload is rejected.

### Handling Express Errors

You can handle errors from middleware function by providing a function to Express. As shown below, a new function is passed as the final argument to `router.post`. This function accepts `error, req, res, next`. This call signature lets Express know the function is designed to handle errors.

The function itself sends back a JSON response with the error message from multer.

```
router.post('/users/me/avatar', upload.single('avatar'), (req,res) => {
  res.send()
}, (error, req, res, next) => {
  res.status(400).send({ error : error.message })
})
```
