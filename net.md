# net

The net module provides you with an asynchronous network wrapper. It contains functions for creating both servers and clients (called streams).

> Summary is **network interaction in Node.js**.

> There are popular frameworks built on top of the net module, such as [Socket.IO](https://socket.io/).
## Popular Functions

- [net.createServer](#netcreateserveroptions-connectionlistener)
- [net.connect](#netconnectoptions-connectionlistener)
- [net.Socket](#netsocket)
- [net.Server](#netserver)
- [net.isIP](#netisipinput)

## net.createServer([options][, connectionListener])

Creates a new TCP server.

```typescript
import net from 'net';

const server = net.createServer((socket) => {
    socket.write('Echo server\r\n');
    socket.pipe(socket);
});

server.listen(1337, () => {
    console.log('Server running at http://localhost:1337/');
});
```

## net.connect(options[, connectionListener])

Makes a connection to a server and returns the connection.

```typescript
import net from 'net';

const client = net.connect({ port: 1337 }, () => {
    console.log('Connected to server!');
    client.write('Hello, server! Love, Client.');
});

client.on('data', (data) => {
    console.log(data.toString());
    client.end();
});

client.on('end', () => {
    console.log('Disconnected from server');
});
```

## net.Socket

This class is an abstraction of a TCP or local socket. net.Socket instances implement a duplex Stream interface. They can be created by the user and used as a client (with connect()) or they can be created by Node.js and passed to the user through the 'connection' event of a server.

```typescript
import net from 'net';

const socket = new net.Socket();

socket.connect(1337, () => {
    console.log('Connected to server!');
    socket.write('Hello, server! Love, Client.');
});

socket.on('data', (data) => {
    console.log(data.toString());
    socket.end();
});

socket.on('end', () => {
    console.log('Disconnected from server');
});
```

## net.Server

This class is used to create a TCP or local server.

```typescript
import net from 'net';

const server = net.createServer((socket) => {
    socket.write('Echo server\r\n');
    socket.pipe(socket);
});

server.listen(1337, () => {
    console.log('Server running at http://localhost:1337/');
});
```

## net.isIP(input)

Check the string is a valid IP address.
```typescript
import net from 'net';

const ipV4 = '124.23.15.83';
const ipV6 = '2001:0db8:85a3:0000:0000:8a2e:0370:7334';

console.log(net.isIP(ipV4)); // 4
console.log(net.isIP(ipV6)); // 6

console.log(net.isIPv4(ipV4)); // true
console.log(net.isIPv6(ipV6)); // true
```
