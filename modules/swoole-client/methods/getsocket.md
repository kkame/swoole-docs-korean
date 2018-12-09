# Swoole TCP/UDP client

## Methods 

### swoole_client->getSocket

#### Prototype

```php
resource swoole_client->getSocket()
```

#### Illustration

Get the TCP socket of the connection.

연결의 TCP 소켓을 가져옵니다.

> This method needs the support of extension sockets. You should compile swoole with `--enable-sockets`.

>이 방법은 확장 소켓을 지원해야합니다. `--enable-sockets`으로 swoole을 컴파일해야합니다.

#### Parameter

void

#### Return

A resource which holds the handle of socket 

#### Example

```php
<?php
$socket = $client->getSocket();
if (!socket_set_option($socket, SOL_SOCKET, SO_REUSEADDR, 1)) {
    echo 'Unable to set option on socket: '. socket_strerror(socket_last_error()) . PHP_EOL;
}
```
