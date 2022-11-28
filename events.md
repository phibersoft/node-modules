# Events

The events module provides a way to handle events in Node.js.

> Summary is **event handling in Node.js**.
## Usage

```typescript
import {EventEmitter} from 'events';

const bus = new EventEmitter();

bus.on('event-name', (arg1, arg2) => {
    console.log(arg1, arg2);
});

bus.emit('event-name', 'Hello', 'World');
```

## EventEmitter

The EventEmitter class is the base class for all event emitters.

### EventEmitter::on(eventName, listener)

Adds the listener function to the end of the listeners array for the event named eventName.

```typescript
const bus = new EventEmitter();

bus.on('event-name', (arg1, arg2) => {
    console.log(arg1, arg2);
});

bus.emit('event-name', 'Hello', 'World');
```

### EventEmitter::once(eventName, listener)

Adds a one-time listener function for the event named eventName. The next time eventName is triggered, this listener is
removed and then invoked.

```typescript
const bus = new EventEmitter();

bus.once('event-name', (arg1, arg2) => {
    console.log(arg1, arg2);
});

bus.emit('event-name', 'Hello', 'World');
bus.emit('event-name', 'Hello', 'World'); // This will not be triggered
```

### EventEmitter::off(eventName, listener)

Removes the specified listener from the listener array for the event named eventName.

```typescript
const bus = new EventEmitter();

const listener = (arg1, arg2) => {
    console.log(arg1, arg2);
};

bus.on('event-name', listener);

bus.emit('event-name', 'Hello', 'World');

bus.off('event-name', listener);

bus.emit('event-name', 'Hello', 'World'); // This will not be triggered
```

### EventEmitter::emit(eventName, ...args)

Synchronously calls each of the listeners registered for the event named eventName, in the order they were registered,
passing the supplied arguments to each.

```typescript
const bus = new EventEmitter();

bus.on('event-name', (arg1, arg2) => {
    console.log(arg1, arg2);
});

bus.emit('event-name', 'Hello', 'World');
```

### EventEmitter::addListener(eventName, listener)

Alias for EventEmitter::on

### EventEmitter::removeListener(eventName, listener)

Alias for EventEmitter::off

### EventEmitter::removeAllListeners(eventName)

Removes all listeners, or those of the specified eventName.
