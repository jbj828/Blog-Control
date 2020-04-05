---
date: '2020/4/5 20:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: File Uploads with Multer
---

multer

<!-- more -->

### Multer

Multer is a library in the Express ecosystem that allows your Express application to easily support file uploads. It couldn't be easier.

After install the multer library, multer can then be configured to fit your specific needs. The example below shows off a basic configuration where `dest` ids set to `avatars`. This will store all uploaded files in a directory called `avatars`.

```
const multer = require('multer')

const upload = multer({
  dest : 'avatars'
})
```

Multer is then added as middleware for the specific endpoint that should allow for file uploads. The route below is expecting a single `avatar` field on the submitted form.

```
router.post('/users/me/avatar', upload.single('avatar'), (req,res)=>{
  res.send()
})
```