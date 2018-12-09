# Swoole TCP/UDP client

Swoole client provide the wrapper of TCP/UDP sockets client side API. 

Swoole 클라이언트는 TCP / UDP 소켓 클라이언트 측 API의 래퍼를 제공합니다.

Compare with PHP *stream* functions, *swoole_client* is more advanced:

PHP * stream * 함수와 비교하여 * swoole_client *가 더욱 향상되었습니다.

* There is a bug in stream function, 
* fread has the limitation length of 8129, can't support big UDP packet
* swoole_client supports waitall, able to read all the data if the packet length is known.
* swoole_client supports UDP connect, there will be no UDP packets mixing up issues.
* swoole_client has better performance.
* swoole_client supports async non-blocking callback, along with sync blocking and select API.

* 스트림 기능에 버그가 있습니다.
* fread의 제한 길이는 8129이며, 큰 UDP 패킷을 지원할 수 없습니다.
* swoole_client는 패킷 길이가 알려진 경우 모든 데이터를 읽을 수있는 waitall을 지원합니다.
* swoole_client는 UDP 연결을 지원합니다. 문제가 혼합 된 UDP 패킷이 없습니다.
* swoole_client는 더 나은 성능을 제공합니다.
* swoole_client는 동기화 차단 및 선택 API와 함께 비동기 비 차단 콜백을 지원합니다.

## Table of Contents

* [Methods List](/modules/swoole-client/methods.md)

* [Callback functions](/modules/swoole-client/callback-functions.md)

* [Properties List](/modules/swoole-client/properties.md)

* [Predefined Constants](/modules/swoole-client/predefined-constants.md)

* [Configurations List](/modules/swoole-client/configuration.md)

* [Common Problems](/modules/swoole-client/common-problems.md)

## Examples

A simple sync TCP client:

간단한 동기화 TCP 클라이언트 :

```php
<?php
$client = new swoole_client(SWOOLE_SOCK_TCP);
if (!$client->connect('127.0.0.1', 9501, -1))
{
    exit("connect failed. Error: {$client->errCode}\n");
}
$client->send("hello world\n");
echo $client->recv();
$client->close();
```

A simple async TCP client:

간단한 비동기 TCP 클라이언트 :

```php
<?php
$client = new swoole_client(SWOOLE_SOCK_TCP, SWOOLE_SOCK_ASYNC);
$client->on("connect", function(swoole_client $cli) {
    $cli->send("GET / HTTP/1.1\r\n\r\n");
});
$client->on("receive", function(swoole_client $cli, $data){
    echo "Receive: $data";
    $cli->send(str_repeat('A', 100)."\n");
    sleep(1);
});
$client->on("error", function(swoole_client $cli){
    echo "error\n";
});
$client->on("close", function(swoole_client $cli){
    echo "Connection close\n";
});
$client->connect('127.0.0.1', 9501);

```

> Note, the async TCP client can not be used in PHP-FPM or Apache mode, only can be used in Swoole server.

> 비동기 TCP 클라이언트는 PHP-FPM 또는 Apache 모드에서는 사용할 수 없으며 Swoole 서버에서만 사용할 수 있습니다.
