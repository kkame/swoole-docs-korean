# Swoole TCP/UDP client

## Methods 

### swoole_client->on

#### Prototype

```php
int swoole_client::on(string $event, mixed $callback)
```

#### Illustration

> Only can be used in async mode.

> 비동기 모드에서만 사용할 수 있습니다.

Set the callback functions for the events:

이벤트에 대한 콜백 함수를 설정합니다.

* connect
* receive
* close
* error 
* BufferFull
* BufferEmpty

* 연결
* 수신
* 닫기
* 오류
* BufferFull
* BufferEmpty

> connect/close events will be emitted immediately when UDP client is created or closed.

> 연결 / 종료 이벤트는 UDP 클라이언트가 생성되거나 닫힐 때 즉시 방출됩니다.

#### Parameter

* `$event`	  the event to be registered with callback function
* `$callback` the callback function

*`$ event`는 콜백 함수로 등록 할 이벤트입니다.
*`$ callback` 콜백 함수

#### Return


#### Example

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
