# Path

The path module provides utilities for working with file and directory paths.

> Summary is **file and directory paths**.

## Popular Functions

- basename: Returns the last portion of a path
- dirname: Returns the directory name of a path
- extname: Returns the extension of the path
- join: Joins all given path segments together
- normalize: Normalizes a path
- parse: Returns an object from a path string
- relative: Returns the relative path from from to to based on the current working directory
- resolve: Resolves a sequence of paths or path segments into an absolute path

> Path functions related to Operating System.
## Usage

```typescript
import {basename, dirname, extname, join, normalize, parse, relative, resolve} from 'path';

const path = '/foo/bar/baz/asdf/quux.html';

console.log(basename(path)); // quux.html
console.log(dirname(path)); // /foo/bar/baz/asdf
console.log(extname(path)); // .html
console.log(join('/foo', 'bar', 'baz/asdf', 'quux', '..')); // /foo/bar/baz/asdf
console.log(normalize('/foo/bar//baz/asdf/quux/..')); // /foo/bar/baz/asdf
console.log(parse(path)); // {root: "/", dir: "/foo/bar/baz/asdf", base: "quux.html", ext: ".html", name: "quux"}
console.log(relative('/data/orandea/test/aaa', '/data/orandea/impl/bbb')); // ../../impl/bbb
console.log(resolve('/foo/bar', './baz')); // C:\foo\bar\baz (on Windows)
```

