### swoole_server->on 

#### Prototype

```php
bool swoole_server->on(string $event, mixed $callback)
```

#### Illustration

Register callback function for the event

이벤트에 대한 콜백 함수 등록

#### Parameter

* `$event` the string of event to be registered
* `$callback` the callable type variable

*`$ event` 등록 할 이벤트 문자열
*`$ callback`은 호출 가능한 타입 변수입니다.

> Check [the full list of events](/modules/swoole-server/callback-functions.md)

> [전체 이벤트 목록] (/ modules / swoole-server / callback-functions.md)을 확인하십시오.

> Check [the four types of callbacks](/modules/swoole-server/common-problems.md)

> [네 가지 유형의 콜백] (/ modules / swoole-server / common-problems.md)을 확인하십시오.

#### Return

the result if it has been registered successfully 

그것이 정상적으로 등록되었을 경우의 결과

#### Example

```php
<?php
$server = new swoole_server("127.0.0.1", 9501);
$server->on('connect', function ($server, $fd){
    echo "New connection established: #{$fd}.\n";
});
$server->on('receive', function ($server, $fd, $from_id, $data) {
    $server->send($fd, "Echo to #{$fd}: \n".$data);
    $server->close($fd);
});
$server->on('close', function ($server, $fd) {
    echo "Connection closed: #{$fd}.\n";
});
$server->start();
```
