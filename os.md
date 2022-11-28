# os

The os module provides a number of operating-system-related utility methods.

> Summary is **operating system information in Node.js**.

## Popular Functions

- os.arch() - Returns the operating system CPU architecture.
- os.cpus() - Returns an array of objects containing information about each logical CPU core.
- os.endianness() - Returns the endianness of the CPU.
- os.freemem() - Returns the amount of free system memory in bytes.
- os.homedir() - Returns the home directory of the current user.
- os.hostname() - Returns the hostname of the operating system.
- os.loadavg() - Returns an array containing the 1, 5, and 15 minute load averages.
- os.networkInterfaces() - Returns an object containing network interfaces.
- os.platform() - Returns a string identifying the operating system platform.
- os.release() - Returns the operating system release.
- os.tmpdir() - Returns the operating system's default directory for temporary files.
- os.totalmem() - Returns the total amount of system memory in bytes.
- os.type() - Returns the operating system name.
- os.uptime() - Returns the system uptime in seconds.

## Usage

```typescript
import os from 'os';

console.log(os.arch()); // x64
console.log(os.cpus()); // Json object
console.log(os.endianness()); // LE
console.log(os.freemem()); // 123456789
console.log(os.homedir()); // /home/username
console.log(os.hostname()); // hostname
console.log(os.loadavg()); // [0.1, 0.2, 0.3]
console.log(os.networkInterfaces()); // Json object
console.log(os.platform()); // linux
console.log(os.release()); // 4.4.0-112-generic
console.log(os.tmpdir()); // /tmp
console.log(os.totalmem()); // 123456789
console.log(os.type()); // Linux

```

