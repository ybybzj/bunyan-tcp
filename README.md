# bunyan-tcp2
A fork of [bunyan-tcp](https://github.com/zenmoto/bunyan-tcp) with backoff reconnection support.

## reconnect usage:

```{javascript}
var tcpStream = bunyanTcp.createBunyanStream({
  server: 'my.logging.server',
  port: 1234,
  backoffStrategy: {
    name: 'fibonacci'(default)|'exponential',
    initialDelay: 300(default),
    maxDelay: 10000(default)
  }|[BackoffStrategy instance],
  retryNum: 10(default)
});

var log = bunyan.createLogger({
    name: 'log',
    streams: [
        {
          level: 'info',
          stream: tcpStream,
          type: 'raw',
          closeOnExit: true
        }
    ]
});
```


