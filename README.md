# Socket.IO Chat App

A small realtime chat application built with Node.js, Express, Socket.IO, and
SQLite. This project is intended for learning how to create a realtime app
with Socket.IO.

## What you will learn

- Creating an HTTP server with Express
- Connecting browser clients to a Socket.IO server
- Sending and receiving realtime events
- Acknowledging messages and retrying failed sends
- Saving messages in SQLite
- Recovering messages after a temporary connection loss
- Using Socket.IO's cluster adapter with Node.js workers

## Requirements

- Node.js 18 or newer
- npm

## Getting started

1. Install the dependencies:

   ```bash
   npm install
   ```

2. Start the server:

   ```bash
   node index.js
   ```

3. Open [http://localhost:3000](http://localhost:3000) in one or more browser
   tabs.

4. Send messages from one tab and watch them appear in the other tabs.

The SQLite database is stored in `chat.db`. It is created automatically when
the server starts, and messages are stored in the `messages` table.

## How it works

1. `index.js` starts an Express HTTP server and attaches Socket.IO to it.
2. The browser loads the Socket.IO client and connects to the server.
3. When a user submits a message, the client emits a `chat message` event with
   a unique client offset.
4. The server stores the message in SQLite and broadcasts it to all connected
   clients.
5. The client acknowledges the event and keeps the latest server offset.
6. If a client reconnects, the server sends messages it may have missed.

The main files are:

- `index.js` - server, Socket.IO events, SQLite setup, and clustering
- `index.html` - browser chat interface and client-side Socket.IO code
- `chat.db` - local SQLite database
- `package.json` - project metadata and dependencies

## Ideas for further learning

- Add usernames and show who sent each message.
- Add message timestamps and format them in the browser.
- Add chat rooms or private conversations.
- Add typing indicators and online-user presence.
- Validate and limit message length on the server.
- Add authentication and protect private rooms.
- Add tests for Socket.IO events and database behavior.
- Replace the simple HTML page with a frontend framework.
- Use Redis with the Socket.IO adapter when running across multiple servers.
- Add pagination or message deletion for larger chat histories.

This is a learning project, so it does not yet include production features
such as authentication, authorization, input validation, or deployment
configuration.
