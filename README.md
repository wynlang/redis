# redis — Official Wyn Package

Redis client for Wyn. Pure Wyn implementation using TCP sockets and RESP protocol. No C library dependency.

## Install

```bash
wyn pkg install github.com/wynlang/redis
```

## Usage

```wyn
var r = Redis_connect("localhost", 6379)
Redis_set(r, "name", "Alice")
var val = Redis_get(r, "name")     // "Alice"
Redis_del(r, "name")
Redis_incr(r, "counter")
Redis_expire(r, "key", 60)
Redis_ping(r)                       // "PONG"
Redis_close(r)
```

## API

| Function | Description |
|----------|-------------|
| `Redis_connect(host, port)` | Connect to Redis server |
| `Redis_set(conn, key, value)` | Set a key |
| `Redis_get(conn, key)` | Get a key |
| `Redis_del(conn, key)` | Delete a key |
| `Redis_incr(conn, key)` | Increment a key |
| `Redis_expire(conn, key, secs)` | Set expiry |
| `Redis_ping(conn)` | Ping server |
| `Redis_keys(conn, pattern)` | List keys |
| `Redis_close(conn)` | Close connection |

## Test

```bash
wyn run tests/test_redis.wyn
```

9 tests: RESP encoding/decoding + live tests if Redis is running.
