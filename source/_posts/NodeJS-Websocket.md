---
date: '2020/4/20 23:30:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: WebSocket
---

WebSocket

<!-- more -->

### The WebSocket Protocol

  - WebSockets allow for full-duplex communication.
  - WebSocket is a seperate protocol from HTTP
  - Persistent connection between client and server.

```
npm i socket.io
```

Socket.io can be used on its own or with Express. Since the chat application will be serving up client-sied assets, both Express and Socket.io will get set up. 

```
const path = require('path')
const http = require('http')
const express = require('express')
const socketio = require('socket.io')

// Create the Express application
const app = express()

// Create the HTTP server using the Express app
const server = http.createServer(app)

// Connect socket.io to the HTTP server
const io = socketio(server)

const port = process.env.PORT || 3000
const publicDirectoryPath = path.join(__dirname, '../public')
app.use(express.static(publicDirectoryPath))

// Listen for new connections to Socket.io
io.on('connection', () => {
 console.log('New WebSocket connection')
})

server.listen(port, () => {
 console.log(`Server is up on port ${port}!`)
```

The server above uses `io.on` which is provided by Socket.io. `on` allows the server to listen for an event and respond to it. In the example above, the server listens for `connection` which allows it to run some code when a client connects to the WebSocket server.

**Socket.io on the Client**

Socket.io is also used on the client to connect to the server. Socket.io automatically serves up `/socket.io/socket.io.js` which contains the client-side code. The script tags below load in the client-side library followed by a custom Javascript file.

```
<script src="/socket.io/socket.io.js"></script>
<script src="/js/chat.js"></script>
```

Your client-side JavaScript can then connect to the Socket.io server by calling `io`. `io` is provided by the client-side Socket.io library. Calling this function will set up the connection, and it'll cause the server's `connection` event handler to run.

```
io()
```