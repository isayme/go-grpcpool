# Pool

[![GoDoc](https://godoc.org/github.com/isayme/go-grpcpool?status.svg)](https://godoc.org/github.com/isayme/go-grpcpool)
[![Go Report Card](https://goreportcard.com/badge/github.com/isayme/go-grpcpool?style=flat-square)](https://goreportcard.com/report/github.com/isayme/go-grpcpool)
[![LICENSE](https://img.shields.io/badge/licence-Apache%202.0-brightgreen.svg?style=flat-square)](https://github.com/isayme/go-grpcpool/blob/master/LICENSE)

Connection pool for Go's grpc client that supports connection reuse.

Pool provides additional features:

- `Connection reuse` supported by specific MaxConcurrentStreams param.
- `Failure reconnection` supported by grpc's keepalive.

# Getting started

## Install

Import package:

```
import (
    pool "github.com/isayme/go-grpcpool"
)
```

```
go get github.com/isayme/go-grpcpool
```

# Usage

```
p, err := pool.New("127.0.0.1:8080", pool.DefaultOptions)
if err != nil {
    log.Fatalf("failed to new pool: %v", err)
}
defer p.Close()

conn, err := p.Get()
if err != nil {
    log.Fatalf("failed to get conn: %v", err)
}
defer conn.Close()

// cc := conn.Value()
// client := pb.NewClient(conn.Value())
```

See the complete example: [https://github.com/isayme/go-grpcpool/tree/master/example](https://github.com/isayme/go-grpcpool/tree/master/example)

# Reference

- [https://github.com/fatih/pool](https://github.com/fatih/pool)
- [https://github.com/silenceper/pool](https://github.com/silenceper/pool)

# License

Pool is under the Apache 2.0 license. See the [LICENSE](https://github.com/isayme/go-grpcpool/blob/master/LICENSE) file for details.
