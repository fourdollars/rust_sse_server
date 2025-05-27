# A dummy Rust SSE server

## Server

```bash
$ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.06s
     Running `target/debug/rust_sse_server`
Starting SSE server at http://127.0.0.1:8080/events
$ cargo run 0.0.0.0 8765
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.06s
     Running `target/debug/rust_sse_server 0.0.0.0 8765`
Starting SSE server at http://0.0.0.0:8765/events
```

## Client

```bash
$ time curl -v http://127.0.0.1:8765/events
*   Trying 127.0.0.1:8765...
* Connected to 127.0.0.1 (127.0.0.1) port 8765
> GET /events HTTP/1.1
> Host: 127.0.0.1:8765
> User-Agent: curl/8.5.0
> Accept: */*
>
< HTTP/1.1 200 OK
< transfer-encoding: chunked
< content-type: text/event-stream
< cache-control: no-cache
< date: Tue, 27 May 2025 10:13:13 GMT
<
id: 1
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 1", "timestamp": "0"}

id: 2
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 2", "timestamp": "1001"}

id: 3
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 3", "timestamp": "2002"}

data: Just a simple data message at 2002

id: 4
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 4", "timestamp": "3003"}

id: 5
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 5", "timestamp": "4005"}

id: 6
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 6", "timestamp": "5007"}

data: Just a simple data message at 5007

id: 7
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 7", "timestamp": "6008"}

id: 8
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 8", "timestamp": "7009"}

id: 9
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 9", "timestamp": "8010"}

data: Just a simple data message at 8010

id: 10
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 10", "timestamp": "9012"}

id: 11
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 11", "timestamp": "10013"}

id: 12
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 12", "timestamp": "11015"}

data: Just a simple data message at 11015

id: 13
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 13", "timestamp": "12016"}

id: 14
event: update
retry: 2000
data: {"message": "Hello from Rust! Event 14", "timestamp": "13017"}

id: 15
event: notification
retry: 2000
data: {"message": "Hello from Rust! Event 15", "timestamp": "14019"}

data: Just a simple data message at 14019

* Connection #0 to host 127.0.0.1 left intact

real    0m15.032s
user    0m0.001s
sys     0m0.011s
```

## References

* https://html.spec.whatwg.org/multipage/server-sent-events.html

## License

MIT
