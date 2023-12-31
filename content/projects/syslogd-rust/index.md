---
title: "Syslogd server in Rust"
description: "A simple syslogd server written in Rust."
date: 2022-12-24
draft: false
tags: ["rust", "syslog", "server"]
langs: "English"
showTableOfContents: true
---

# Introduction

[This](https://github.com/fede-26/syslogd-rust) is a simple server for syslog.

It supports incoming connection via udp (514) or tcp (601) _without tls_.

It listens on all interfaces but can't use both protocols at the same time (you should run 2 servers).

# Build

```bash
cargo build --release
```

If you don't want or can't build the executable, you can download it in the release tab.

# Run

If builded with cargo:
```bash
sudo target/release/syslogd-rust --help
```

If downloaded:
```bash
sudo syslogd-rust --help
```

## Log to file

If you want to log to a file you can redirect the output or use a command like `tee`:

```bash
sudo syslogd-rust | tee -a log.txt
```

# Send a log message

In linux you can use the `logger` command:

```bash
logger -is -n 127.0.0.1 this message is sent with udp
```

```bash
logger -is --tcp -n 127.0.0.1 this message is sent with tcp
```

# "The Flow"

Depending on the flag used, the port is bound and the process waits for connections.
For udp it defines the socket (with the bind of the port) and enters an infinite loop in which every incoming connection is accepted.
After which the transmitted content is passed to the `print_message()` function, which takes care of parsing and printing the payload.

For tcp instead a listener is created, which is an infinite iterator.
A for loop loops through all incoming connections.
Each connection is then accepted and read to extract its payload.
As before it is passed to `print_message()`.

`print_message()` uses [syslog_loose](https://crates.io/crates/syslog_loose) for parsing and then has a series of conditional prints (only print if the value is present).

Using the `--raw` flag you can see the original payload.

[Clap](https://crates.io/crates/clap) is used for parsing command line arguments.

I don't know why yet, but using tcp appends a `\n` to the end.
This doesn't happen with udp.
To make the outputs equal I trim the last character if it's a `\n` or `\r`.

All the connections should stop after sending a single packet (both udp and tcp), because the tcp listener, in its current implementation (done by me) can't handle multiple reads on the same stream.
This theoretically shouldn't be a problem.

# External links

- [rfc5424](https://datatracker.ietf.org/doc/html/rfc5424)
- [abnf syntax of syslog](https://datatracker.ietf.org/doc/html/rfc5424#section-6)
- [Wikipedia: syslog](https://en.wikipedia.org/wiki/Syslog)
- Stack overflow