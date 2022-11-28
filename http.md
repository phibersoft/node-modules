# http

The http module provides HTTP server and client functionality.

> Summary is **HTTP server and client in Node.js**.

> There are popular frameworks built on top of the http module, such as [Express](https://expressjs.com/).

## Popular Functions

- [http.createServer](#httpcreateserveroptions-requestlistener)
- [http.request](#httprequestoptions-callback)
- [http.get](#httpgetoptions-callback)
- [http.STATUS_CODES](#httpstatus_codes)
- [http.METHODS](#httpmethods)

## http.createServer([options][, requestListener])

Creates a new HTTP server.

```typescript
import http from 'http';

const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello World!');
});

server.listen(3000, () => {
    console.log('Server running at http://localhost:3000/');
});
```

## http.request(options[, callback])

Makes a request to a server and returns the response.

```typescript
import http from 'http';

const options = {
    hostname: 'www.google.com',
    port: 80,
    path: '/',
    method: 'GET'
};

const req = http.request(options, (res) => {
    console.log(`STATUS: ${res.statusCode}`);
    console.log(`HEADERS: ${JSON.stringify(res.headers)}`);
    res.setEncoding('utf8');
    res.on('data', (chunk) => {
        console.log(`BODY: ${chunk}`);
    });
    res.on('end', () => {
        console.log('No more data in response.');
    });
});

req.on('error', (e) => {
    console.error(`problem with request: ${e.message}`);
});

req.end();
```

## http.get(options[, callback])

> Or you can use http.post(), http.put(), http.delete(), etc.

Makes a GET request to a server and returns the response.

```typescript
import http from 'http';

http.get('http://www.google.com/index.html', (res) => {
    const { statusCode } = res;
    const contentType = res.headers['content-type'];

    let error;
    if (statusCode !== 200) {
        error = new Error('Request Failed.\n' +
            `Status Code: ${statusCode}`);
    } else if (!/^text\/html/.test(contentType)) {
        error = new Error('Invalid content-type.\n' +
            `Expected text/html but received ${contentType}`);
    }
    if (error) {
        console.error(error.message);
        // Consume response data to free up memory
        res.resume();
        return;
    }

    res.setEncoding('utf8');
    let rawData = '';
    res.on('data', (chunk) => { rawData += chunk; });
    res.on('end', () => {
        try {
            console.log(rawData);
        } catch (e) {
            console.error(e.message);
        }
    });
}).on('error', (e) => {
    console.error(`Got error: ${e.message}`);
});
```

## http.STATUS_CODES

A map of numeric HTTP status codes to their corresponding messages.

```typescript
import http from 'http';

console.log(http.STATUS_CODES[200]); // OK
console.log(http.STATUS_CODES[404]); // Not Found
```

## http.METHODS

An array of the HTTP methods that are supported by the parser.

```typescript

import http from 'http';

console.log(http.METHODS); // [ 'ACL', 'BIND', 'CHECKOUT', 'CONNECT', 'COPY', 'DELETE', 'GET', 'HEAD', 'LINK', 'LOCK', 'M-SEARCH', 'MERGE', 'MKACTIVITY', 'MKCALENDAR', 'MKCOL', 'MOVE', 'NOTIFY', 'OPTIONS', 'PATCH', 'POST', 'PROPFIND', 'PROPPATCH', 'PURGE', 'PUT', 'REBIND', 'REPORT', 'SEARCH', 'SOURCE', 'SUBSCRIBE', 'TRACE', 'UNBIND', 'UNLINK', 'UNLOCK', 'UNSUBSCRIBE' ]
```

