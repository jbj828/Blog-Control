---
date: '2020/4/21 20:30:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Socket.io Events
---

Socket.io Events

<!-- more -->

Events allow you to transfer data from the client to the server or from the server to the client.

### Working with Events

There are two sides to every event, the sender and the receiver. If the server is the sender, then the client is the receiver.

Events can be sent from the sender using `emit`. Events can be received by the receiver using `on`. The example below shows how this pattern can be used to create a simple counter application. The following snippet contains the client-side Javascript code.

```
const socket = io()

// Listen for "countUpdated"
socket.on('countUpdated', (count) => {
  console.log('The count has been updated!', count)
})

document.querySelector('#increment').addEventListener('click', ()=>{
  // Emit 'increment'
  socket.emit('increment')
})
```

The client-side code uses `on` to listen for the `countUpdated` event. A message will be logged with the current count when that event is received. The client-side code also uses `emit` to send the `increment` event. This occurs when a button on the screen is clicked. 

The server-side code for this example is below

```
let count = 0

io.on('connection', (socket)=>{
  console.log('New WebSocket connection')

  socket.emit('countUpdated', count)

  socket.on('increment', ()=>{
    count++
    io.emit('countUpdated', count)
  })
})
```

The server above is responsible for emitting `countUpdated` and listening for `increment`. New users get the current count right after they connect to the server. If a client sends `increment` to the server, the count is incremented and all connected clients are notified of the change.

On the client, `socket.emit` emits an event to the server. On the server, both `socket.emit` and `io.emit` can be used. `socket.emit` sends an event to that specific client, while `io.emit` sends an event to all connected clients.






Ref : The Complete Node.js Dev Course by Andrew Mead