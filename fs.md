# fs

The fs module provides an API for interacting with the file system.

> Summary is **file system interaction in Node.js**.
## Popular Functions

- [fs.readFile](#fsreadfilefile-options-callback)
- [fs.writeFile](#fswritefilefile-data-options-callback)
- [fs.appendFile](#fsappendfilefile-data-options-callback)
- [fs.exists](#fsexistspath-callback)
- [fs.mkdir](#fsmkdirpath-options-callback)
- [fs.readdir](#fsreaddirpath-options-callback)
- [fs.unlink](#fsunlinkpath-callback)
- [fs.rmdir](#fsrmdirpath-callback)
- [fs.rename](#fsrenameoldpath-newpath-callback)

## What is fs.promises.* ?

The fs.promises API provides an alternative set of asynchronous file system methods that return Promise objects rather
than using callbacks. The methods are accessible via `fs.promises` or `require('fs').promises`.

## fs.readFile(file[, options], callback)

Reads the entire contents of a file.

```typescript
import fs from 'fs';

fs.readFile('file.txt', (err, data) => {
    if (err) throw err;
    console.log(data);
});

// or

fs.promises.readFile('file.txt')
    .then(data => console.log(data))
    .catch(err => console.error(err));
```

## fs.writeFile(file, data[, options], callback)

Writes data to a file, replacing the file if it already exists.

```typescript
import fs from 'fs';

fs.writeFile('file.txt', 'Hello Node.js', (err) => {
    if (err) throw err;
    console.log('The file has been saved!');
});
```

## fs.appendFile(file, data[, options], callback)

Appends data to a file, creating the file if it does not yet exist.

```typescript
import fs from 'fs';

fs.appendFile('file.txt', 'data to append', (err) => {
    if (err) throw err;
    console.log('The "data to append" was appended to file!');
});
```

## fs.exists(path, callback)

Tests a user's permissions for the file or directory specified by path.

```typescript
import fs from 'fs';

fs.exists('/etc/passwd', (exists) => {
    console.log(exists ? 'it\'s there' : 'no passwd!');
});
```

## fs.mkdir(path[, options], callback)

Creates a directory.

```typescript
import fs from 'fs';

fs.mkdir('/tmp/a/apple', {recursive: true}, (err) => {
    if (err) throw err;
});
```

## fs.readdir(path[, options], callback)

Reads the contents of a directory.

```typescript
import fs from 'fs';

fs.readdir('/tmp', (err, files) => {
    if (err) throw err;
    for (const file of files) {
        console.log(file);
    }
});
```

## fs.unlink(path, callback)

Deletes a file.

```typescript
import fs from 'fs';

fs.unlink('/tmp/hello', (err) => {
    if (err) throw err;
    console.log('successfully deleted /tmp/hello');
});
```

## fs.rmdir(path [, options], callback)

Deletes a directory.

```typescript
import fs from 'fs';

fs.rmdir('/tmp/a/apple', {recursive: true}, (err) => {
    if (err) throw err;
    console.log('successfully deleted /tmp/a/apple');
});
```

## fs.rename(oldPath, newPath, callback)

Renames a file or directory.

```typescript
import fs from 'fs';

fs.rename('/tmp/hello', '/tmp/world', (err) => {
    if (err) throw err;
    console.log('renamed complete');
});
```
