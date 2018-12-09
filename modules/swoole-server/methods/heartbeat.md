### swoole_server->heartbeat

#### Prototype

```php
array swoole_server::heartbeat(bool $if_close_connection = true)
```

#### Illustration

Check status of all the connections of the server. Optionally close the idle and timeout connections.

서버의 모든 연결 상태를 확인하십시오. 선택적으로 유휴 및 시간 종료 연결을 닫으십시오.

#### Parameter

* `$if_close_connection`	the option which decides if close the connections which exceeds the time

*`$ if_close_connection` 시간을 초과하는 연결을 닫는지를 결정하는 옵션.

#### Return

the array of connections

연결 배열

#### Example
