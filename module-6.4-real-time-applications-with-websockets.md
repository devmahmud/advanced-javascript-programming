#### 6.4. Real-time Applications with WebSockets

WebSockets are a communication protocol that allows for full-duplex, bidirectional communication between a client and a server. They are especially useful for building real-time applications such as chat apps, online games, and collaborative tools. In this submodule, we'll delve into WebSockets and how to use them for real-time communication.

##### Introduction to WebSockets

WebSockets provide a persistent connection between a client and a server. Unlike HTTP, which follows a request-response model, WebSockets enable ongoing, low-latency communication in both directions. Here's a high-level overview of how WebSockets work:

1. **WebSocket Handshake:** The client and server perform a handshake to establish a WebSocket connection.

2. **Bi-Directional Communication:** Once the connection is established, both the client and server can send and receive messages at any time without the overhead of HTTP requests.

**Example (Server-Side Using Node.js and `ws` Library):**

```javascript
const WebSocket = require('ws');
const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', (ws) => {
  console.log('Client connected');

  ws.on('message', (message) => {
    console.log(`Received: ${message}`);
    // Send a response
    ws.send(`You said: ${message}`);
  });
});
```

In this example, we create a WebSocket server using the `ws` library in Node.js, listen for incoming connections, and handle messages from clients.

**Example (Client-Side Using JavaScript):**

```javascript
const socket = new WebSocket('ws://example.com:8080');

socket.addEventListener('open', (event) => {
  socket.send('Hello, WebSocket!');
});

socket.addEventListener('message', (event) => {
  console.log(`Received: ${event.data}`);
});
```

On the client side, we create a WebSocket connection, send a message when the connection is open, and handle incoming messages.

##### Real-Time Applications

WebSockets are widely used for real-time applications. Here are a few examples of where they shine:

- **Chat Applications:** WebSockets enable instant message delivery between users.

- **Live Notifications:** Real-time updates for notifications, likes, and comments.

- **Online Gaming:** Multiplayer games that require low-latency communication.

- **Collaboration Tools:** Real-time document editing and collaboration.

#### Benefits

- WebSockets provide a persistent, low-latency communication channel for real-time applications.
- They enable interactive and engaging user experiences in web applications.

Understanding and utilizing WebSockets is crucial for building real-time applications that require instant data updates and interactive user experiences.
