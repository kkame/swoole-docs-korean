# Swoole TCP/UDP client

## Methods 

### swoole_client::__construct 

#### Prototype

```php
swoole_client->__construct(int $sock_type, int $is_sync = SWOOLE_SOCK_SYNC, string $key);
```

#### Illustration

Create Swoole sync or async TCP/UDP client, with or without SSL.

SSL의 유무에 관계없이 Swoole 동기화 또는 비동기 TCP / UDP 클라이언트를 만듭니다.

#### Parameter

* `$sock_type`	the type of socket
* `$is_sync`    set the client to be synchronous or asynchronous 
* `$key`        the key used for long connection, the default key is IP:PORT. the connection which has the same key will be reused

*`$ sock_type` 소켓의 타입
*`$ is_sync`는 클라이언트를 동기 또는 비동기로 설정합니다.
*`$ key`는 긴 연결에 사용되는 키이고, 기본 키는 IP : PORT입니다. 같은 열쇠를 가지는 접속이 재사용됩니다.

#### Return

the swoole_client object

swoole_client 객체


#### Example

Create persistent TCP connection in php-fpm or apache php:

php-fpm 또는 apache php에서 영구 TCP 연결을 만듭니다.

```php
<?php
$cli = new swoole_client(SWOOLE_TCP | SWOOLE_KEEP);
```
