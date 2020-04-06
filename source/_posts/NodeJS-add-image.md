---
date: '2020/4/6 12:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Adding Images to the User Profile & Serving up Files
---

Adding Images to the User Profile & Serving up Files

<!-- more -->

## Adding Images to the User Profile

A new field needs to be added to the user model to store the avatar image data. The snippet below adds `avatar` on the user with the type of `Buffer`. The `Buffer` type should be used when storing binary data, which is exactly the type of data that multer provides.

```
const userSchema = new mongoose.Schema({
  avatar : {
    type : Buffer
  }
})
```

The avatar upload route will be able to change the user profile data, so the route should be put behind authentication. The handler function grabs the binary data and stores it on the `avatar` field. Finally, the changes are saved.

```
router.post('/users/me/avatar', auth, uploda.single('upload'), async (req, res) => {
  req.user.avatar = req.file.buffer
  await req.user.save()
  res.send()
}, (error, req, res, next) => {
  res.status(400).send({ error : error.message})
})
```

<br>

## Serving up Files

This is how we serve up user profile images. These images will be served as if they were static assets for the application.

Serving up the user avatars will require two pieces of data from the server. The first is the image data, and the second is the `Content-Type` header. The image data is stored on the user profile. The header should be set equal to `image/png` which lets the client know they're getting a PNG image back.

The route below fetches the image data and sets the `Content-Type` header for the response. The URL could be visited to view the profile picture.

```
router.get('/users/:id/avatar', async (req, res) =>{
  try {
      const user = await User.findById(req.params.id)

      if(!user || !user.avatar){
        throw new Error()
      }

      res.set('Content-Type', 'image/jpg')
      res.send(user.avatar)
  } catch(e){
      res.status(404).send()
  }
})
```


출처 : NodeJS course on Udemy by Andrew Mead
