---
title: "Swoole"
weight: 8
sidebarTitle: "Swoole"
---

Swoole is a PHP extension that extends PHP core with a coroutine based asynchronous network application framework designed for building large scale concurrent systems.

Unlike PHP-FPM’s stateless operating, Swoole relies on establishing persistent connections with every user, sending and receiving data in real-time.

[Swoole](https://github.com/swoole/swoole-src) and [Open Swoole](https://openswoole.com/) are two forked libraries pursuing that goal.

{{< note >}}
Swoole requires PHP 7.3+.
{{< /note >}}

Check the documentation related to [Laravel Octane on Platform.sh](../../guides/laravel/deploy/octane.md).

{{% swoole %}}

## Use

Override the default web server with a [custom start command](./_index.md#alternate-start-commands).
Octane should listen on a TCP socket.

```yaml {location=".platform.app.yaml"}
web:
    upstream:
        socket_family: tcp
        protocol: http
    commands:
        start: php path/to/swoole/start/command --port=$PORT
    locations:
        "/":
            allow: false
            passthru: true
```