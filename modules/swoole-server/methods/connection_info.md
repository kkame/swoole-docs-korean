### swoole_server->connection_info

#### Prototype

```php
mixed swoole_server->connection_info(int $fd, int $from_id, bool $ignore_close = false)
```

#### Illustration

Get the connection info, alias of function *swoole_server->getClientInfo()*.

함수 * swoole_server-> getClientInfo () *의 별칭 인 연결 정보를 가져옵니다.

#### Parameter

* `$fd`	the id number of client
* `$from_id` this parameter is needed, the swoole server is type of UDP
* `$ignore_close` this method will return the information of connection even if the connection is closed

*`$ fd`는 클라이언트의 ID 번호입니다.
*`$ from_id '이 매개 변수가 필요합니다. 스풀 서버는 UDP 유형입니다
*`$ ignore_close`이 메소드는 연결이 닫혀 있어도 연결 정보를 반환합니다.

#### Return

the array of information of the `$fd` client 

if the `$fd` client dosen't exist, the result is false 

`$ fd` 클라이언트의 정보 배열

`$ fd` 클라이언트가 존재하지 않으면 결과는 false입니다

#### Example

```php
<?php
$fdinfo = $serv->connection_info($fd);
var_dump($fdinfo);
array(5) {
  ["from_id"]=>
  int(3)
  ["server_fd"]=>
  int(14)
  ["server_port"]=>
  int(9501)
  ["remote_port"]=>
  int(19889)
  ["remote_ip"]=>
  string(9) "127.0.0.1"
  ["connect_time"]=>
  int(1390212495)
  ["last_time"]=>
  int(1390212760)
}

$udp_client = $serv->connection_info($fd, $from_id);
var_dump($udp_client);
```
