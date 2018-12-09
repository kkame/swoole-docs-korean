### swoole_server->sendwait

#### Prototype

```php
bool swoole_server->sendwait(int $fd, string $send_data)
```
#### Illustration

Send data to the remote socket in the blocking way.

블로킹 방식으로 원격 소켓에 데이터를 보냅니다.

> Only available in SWOOLE_BASE mode.

> SWOOLE_BASE 모드에서만 사용할 수 있습니다.

#### Parameter

* `$fd`	the id number of client
* `$send_data` the data to send

*`$ fd`는 클라이언트의 ID 번호입니다.
*`$ send_data`는 보낼 데이터입니다.

#### Return

the result of sending data

데이터를 전송 한 결과

#### Example
