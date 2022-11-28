# node-modules

This package contains the some popular modules that are built-in to Node.js for newbies to learn from.

## Modules

- [util](/util.md): Utilities for inspecting and formatting objects
- [events](/events.md): Event emitter
- [path](/path.md): Path utilities
- [fs](/fs.md): File system utilities
- [http](/http.md): HTTP server and client
- [net](/net.md): TCP and UDP networking
- [os](/os.md): Operating system utilities
- [crypto](/crypto.md): Cryptographic utilities
- [stream](/stream.md): Stream utilities
- [child_process](/child_process.md): Child process utilities
- [cluster](/cluster.md): Cluster utilities
- [readline](/readline.md): Readline utilities

> Note: In this modules, only popular usage of each module is included. For more information, please refer to the
> official documentation.

> Note 2: Also there are more modules that are built-in to Node.js (like zlib for compression), but they are not
> included in this package. We will just discuss most popular modules.

## Contributing

Feel free to open an issue or pull request if you find any errors or have any suggestions.

## Suggestions

- Learn very well (**events, path, fs, stream**) before you move to other modules. These modules almost used in every
  Node.js project.
  For other modules, you can learn them as you need.
- Advanced Topics for General:
    - ESModules vs CommonJS
    - Node.js Event Loop
    - Node.js Worker Threads
- If you interested in REST API, here are some advanced topics:
    - What is the difference between **Monolilith** and **Microservices**?
    - What is the difference between **REST** and **GraphQL**?
    - What is the difference between **JWT** and **OAuth**?
- If you interested in **Socket**, here are some advanced topics:
    - What is the difference between **Socket.io** and **WebSocket**?
    - What is the difference between **TCP** and **UDP**?
    - What is the difference between **HTTP** and **HTTPS**?
- If you interested in command-line applications
    - What is the difference between **CLI** and **GUI**?
    - What is the difference between **Bash** and **PowerShell**?
    - Check [PKG](https://npmjs.com/package/pkg) for creating standalone executables
    - Check [Inquirer](https://npmjs.com/package/inquirer) for creating interactive command-line applications
- If you interested in operating system, my personal suggestion is don't use NodeJS, try low-level compiled languages
  like C, C++, Rust, Go, etc. NodeJS is not suitable for operating system development. You can use it but you will have
  to deal with some performance issues.

> Main suggestion is don't listen NodeJS fans, they will tell you NodeJS is the best on every topic. Research every
> benchmarks. Also don't listen any other language fans, they will tell you their language is the best on every topic.
> Choose the best language for your project.
