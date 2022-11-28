# readline

The `readline` module provides an interface for reading data from a Readable stream (such as `process.stdin`) one line at a time.

> Summary is **managing the input and output of a terminal**.
## Popular Functions

- [readline.createInterface](#readlinecreateinterfaceoptions)
- [readline.cursorTo](#readlinecursortostreamx-y)
- [readline.clearLine](#readlineclearlinestream-dir)
- [readline.clearScreenDown](#readlineclearscreendownstream)
- [readline.moveCursor](#readlinemovecursorstreamdx-dy)

## Main Usage

```typescript
import readline from 'readline';

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
});

rl.question('What is your name? ', (name) => {
    console.log(`Hello ${name}!`);
    rl.close();
});
```

## readline.createInterface(options)

Creates a new `readline.Interface` instance.

```typescript
import readline from 'readline';

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
});
```

## readline.cursorTo(stream, x, y)

Moves the cursor to the specified position.

```typescript
import readline from 'readline';

readline.cursorTo(process.stdout, 0, 0);
```

## readline.clearLine(stream, dir)

Clears the current line of the given `WriteStream` in a specified direction.

```typescript
import readline from 'readline';

readline.clearLine(process.stdout, 0);
```

## readline.clearScreenDown(stream)

Clears the given `WriteStream` from the current position of the cursor down.

```typescript
import readline from 'readline';

readline.clearScreenDown(process.stdout);
```

## readline.moveCursor(stream, dx, dy)

Moves the cursor relative to its current position.

```typescript
import readline from 'readline';

readline.moveCursor(process.stdout, 0, 1);
```
