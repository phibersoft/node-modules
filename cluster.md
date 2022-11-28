# cluster

The `cluster` module allows you to easily create child processes that all share server ports.

> Summary is **multi-process in NodeJS**.

## Popular Functions

- cluster.fork() - Forks a new worker process.
- cluster.setupMaster() - Setup the master process.
- cluster.schedulingPolicy - The scheduling policy for the cluster.
- cluster.settings - The settings for the cluster.
- cluster.worker - The worker object for the current process.
- cluster.workers - The worker objects for all workers.
- cluster.disconnect() - Disconnects the worker from the cluster.
- cluster.isMaster - Whether the current process is the master process.
- cluster.isWorker - Whether the current process is a worker process.


## Usage

```typescript
import cluster from 'cluster';

if (cluster.isMaster) {
    // Fork workers.
    for (let i = 0; i < numCPUs; i++) {
        cluster.fork();
    }

    cluster.on('exit', (worker, code, signal) => {
        console.log(`worker ${worker.process.pid} died`);
    });
} else {
    // Workers can share any TCP connection
    // In this case it is an HTTP server
    http.createServer((req, res) => {
        res.writeHead(200);
        res.end('hello world');
    }).listen(8000);
}
```

### PM2
Are you looking for a production-ready process manager for Node.js? Check out [PM2](https://pm2.keymetrics.io/).

