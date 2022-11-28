# stream

The stream module provides a base API that makes it easy to build objects that implement the [Node.js stream interface](https://nodejs.org/api/stream.html).

> Summary is **stream handling in Node.js**.

> These package generally aren't used directly, but are instead accessed via the [fs](fs.md) and [net](net.md) modules.
## Popular Functions

- [stream.Readable](#streamreadable)
- [stream.Writable](#streamwritable)
- [stream.Duplex](#streamduplex)
- [stream.Transform](#streamtransform)
- [stream.PassThrough](#streampassthrough)

## stream.Readable

Creates a new Readable stream. This stream is readable, which means that data can be pulled from it using the stream's `read()` method.

```typescript
import stream from 'stream';

const readableStream = new stream.Readable({
    read() {
        this.push('Hello world!');
        this.push(null);
    },
});

readableStream.pipe(process.stdout);
```

## stream.Writable

Creates a new Writable stream. This stream is writable, which means that data can be pushed to it with the stream's `write()` method.

```typescript
import stream from 'stream';

const writableStream = new stream.Writable({
    write(chunk, encoding, callback) {
        console.log(chunk.toString());
        callback();
    },
});

writableStream.write('Hello world!');
```

## stream.Duplex

Creates a new Duplex stream. This stream is both readable and writable, which means that data can be pushed to it with the stream's `write()` method, and data can be pulled from it using the stream's `read()` method.

```typescript
import stream from 'stream';

const duplexStream = new stream.Duplex({
    write(chunk, encoding, callback) {
        console.log(chunk.toString());
        callback();
    },
    read() {
        this.push('Hello world!');
        this.push(null);
    },
});

duplexStream.on('data', (chunk) => {
    console.log(chunk.toString());
});

duplexStream.on('end', () => {
    console.log('End of stream');
});

duplexStream.write('Hi there!');
duplexStream.end();
```

## stream.Transform

Creates a new Transform stream. This stream is both readable and writable, which means that data can be pushed to it with the stream's `write()` method, and data can be pulled from it using the stream's `read()` method.
If you want to transform the data, you need to implement the `_transform()` method.

```typescript

import stream from 'stream';

const transformStream = new stream.Transform({
    transform(chunk, encoding, callback) {
        this.push(chunk.toString().toUpperCase());
        callback();
    },
});

transformStream.on('data', (chunk) => {
    console.log(chunk.toString());
});

transformStream.write('Hello world!');

transformStream.end();
```

## stream.PassThrough

Creates a new PassThrough stream. This stream is both readable and writable, which means that data can be pushed to it with the stream's `write()` method, and data can be pulled from it using the stream's `read()` method.
If you need a middleware stream that does nothing but passing the data, you can use this stream.

```typescript
import stream from 'stream';

const transformStream = new stream.Transform({
    transform(chunk, encoding, callback) {
        this.push(chunk.toString().toUpperCase());
        callback();
    },
});

transformStream.on('data', (chunk) => {
    console.log(chunk.toString());
});

// passthroughStream combined with transformStream
const passthroughStream = new stream.PassThrough();

passthroughStream.pipe(transformStream);

passthroughStream.write('hello');
passthroughStream.write('world');
passthroughStream.end();

```
