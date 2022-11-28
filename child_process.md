# child_process

The child_process module provides the ability to spawn child processes in a manner. This is primarily used to
spawn `npm` commands.
> Summary is **cmd in NodeJS**.

## Popular Functions

- [child_process.exec](#child_processexeccommand-options-callback)
- [child_process.execFile](#child_processexecfilefile-args-options-callback)
- [child_process.fork](#child_processforkmodulepath-args-options)
- [child_process.spawn](#child_processspawncommand-args-options)

## child_process.exec(command[, options][, callback])

The `child_process.exec()` method runs a command in a shell and buffers the output.

```typescript
import child_process from 'child_process';

child_process.exec('npm install', (error, stdout, stderr) => {
    if (error) {
        console.error(`exec error: ${error}`);
        return;
    }
    console.log(`stdout: ${stdout}`);
    console.error(`stderr: ${stderr}`);
});

// Install all dependencies
```

## child_process.execFile(file[, args][, options][, callback])

The `child_process.execFile()` method is similar to `child_process.exec()` except that it does not spawn a shell by
default. Rather, the specified executable file is spawned directly as a new process making it slightly leaner
than `child_process.exec()`. It takes the same arguments as `child_process.exec()`.

```typescript

import child_process from 'child_process';

child_process.execFile('npm', ['install'], (error, stdout, stderr) => {
    if (error) {
        console.error(`exec error: ${error}`);
        return;
    }
    console.log(`stdout: ${stdout}`);
    console.error(`stderr: ${stderr}`);
});

// Install all dependencies
```

## child_process.fork(modulePath[, args][, options])

The `child_process.fork()` method is a special case of the `child_process.spawn()` method used specifically to spawn new
Node processes. Like `child_process.spawn()`, a `ChildProcess` object is returned. The returned `ChildProcess` will have
an additional communication channel built-in that allows messages to be passed back and forth between the parent and
child.

```typescript

import child_process from 'child_process';

const child = child_process.fork('child.js');

child.on('message', (message) => {
    console.log('Message from child', message);
});

child.send({hello: 'world'});

// Message from child { foo: 'bar', baz: null }
```

## child_process.spawn(command[, args][, options])

The `child_process.spawn()` method spawns a new process using the given command, with command line arguments in args. If
omitted, args defaults to an empty array. If args is not an array, the behavior is undefined.

```typescript

import child_process from 'child_process';

const child = child_process.spawn('npm', ['install']);

child.stdout.on('data', (data) => {
    console.log(`stdout: ${data}`);
});

child.stderr.on('data', (data) => {
    console.error(`stderr: ${data}`);
});

child.on('close', (code) => {
    console.log(`child process exited with code ${code}`);
});

// Install all dependencies
```

