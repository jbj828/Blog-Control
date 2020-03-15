---
date: '2020/3/12 14:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: The Query String
---

Query String

<!-- more -->

#### The Query String

The query string is a portion of the URL that allows you to provide additional information to the server. 

```
app.get('/weather', (req, res) => {
    console.log(req.query)
    if (!req.query.address) {
        return res.send({
            error: "You must provide an address."
        })
    }
    res.send({
        forcast: 'forcast',
        location: 'location',
        address: req.query.address
    })
})
```

