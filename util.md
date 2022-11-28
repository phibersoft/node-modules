# Util

The Util module provides access to some utility functions.

> Summary is **extend developer's functionality**.

## Popular Functions

- [Util::promisify](#promisify)
- [Util::callbackify](#callbackify)
- [Util::inspect](#inspect)
- [Util::format](#format)
- [Util::debuglog](#debuglog)
- [Util::deprecate](#deprecate)
- [Util::isDeepStrictEqual](#isDeepStrictEqual)

## Util::promisify(original)

Convert a function that takes a callback to a function that returns a promise.

```typescript
const myFunc = (callback: (err: Error | null, ...args: any[]) => void) => {
callback(null, ['Hello', 'World']);
};

const myFuncPromise = Util.promisify(myFunc);

myFuncPromise().then((result) => {
    console.log(result); // ['Hello', 'World']
});
```

## Util::callbackify(original)

Convert a promise-based function to callback function.

```typescript
const myFunc = () => {
    return new Promise((resolve, reject) => {
        resolve(['Hello', 'World']);
    });
};

const myFuncCallback = Util.callbackify(myFunc);

myFuncCallback((err, result) => {
    console.log(result); // ['Hello', 'World']
});
```

## Util::inspect(object, [options])

Returns a string representation of object that is intended for debugging.

```typescript
const obj = {
    foo: 'bar',
    baz: 42,
    nested: {a: 1, b: 2},
    arr: [1, 2, 3],
    fn: () => 'Hello',
    date: new Date(),
    reg: /foo/g
};
console.log(util.inspect(obj, {
    showHidden: true,
    depth: 2,
    colors: true,
}));

/*
    Output is colorized and formatted for readability:
    { foo: 'bar',
      baz: 42,
      nested: { a: 1, b: 2 },
      arr: [ 1, 2, 3, [length]: 3 ],
      fn: [Function: fn] { [length]: 0, [name]: 'fn' },
      date: 2018-07-30T15:12:00.000Z,
      reg: /foo/g { [lastIndex]: 0 }, 
    }
*/

```

## Util::format(format, ...args)

Returns a formatted string using the first argument as a format string. Similar to `printf` in C.

```typescript
const text = 'Congratulate %s on their %dth birthday! Also: %j';
const name = 'Sara';
const age = 32;
const data = {foo: 'bar', baz: 42};

const output = util.format(text, name, age, data);

console.log(output);
// Output: Congratulate Sara on their 32th birthday! Also: {"foo":"bar","baz":42}
/*
    %s - String
    %d - Number
    %j - JSON
    %% - Literal percent sign
*/
```

## Util::debuglog(section)

Returns a function that writes to stderr with the prefix `section: ` if the `NODE_DEBUG` environment variable is set to
a space-separated list of values that includes `section`.

```typescript
const debuglog = util.debuglog('foo');
debuglog('hello from foo [%d]', 123);
// Output: NODE_DEBUG=foo node my-app.js
// Output: FOO 123: hello from foo [123]
```

## Util::deprecate(fn, message)

Returns a function that prints a deprecation message to stderr the first time it is invoked, then invokes `fn` with the
supplied arguments.

```typescript
const myFunc = () => {
    console.log('Hello World');
};

const myFuncDeprecated = Util.deprecate(myFunc, 'myFunc is deprecated. Please use myFunc2 instead.');

myFuncDeprecated();
// Output: (node:1234) [DEP0001] DeprecationWarning: myFunc is deprecated. Please use myFunc2 instead.
// Output: Hello World
```

## Util::isDeepStrictEqual(val1, val2)

Returns true if the two values are deeply equal, false otherwise.

```typescript
const obj1 = {a: 1, b: 2};
const obj2 = {a: 1, b: 2};
const obj3 = {a: 1, b: 2, c: 3};

console.log(util.isDeepStrictEqual(obj1, obj2)); // true
console.log(util.isDeepStrictEqual(obj1, obj3)); // false
```
