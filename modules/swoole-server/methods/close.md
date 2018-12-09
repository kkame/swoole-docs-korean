### swoole_server->close

#### Prototype

```php
bool swoole_server->close(int $fd, bool $reset = false)
```

#### Illustration

Close the connection to the remote TCP socket and emit *Close* event.

원격 TCP 소켓에 대한 연결을 닫고 * Close * 이벤트를 내 보냅니다.

#### Parameter

* `$fd`	the id of connection between the server and the client
* `$reset` if close the connection forcibly and loose the data of this connection

*`$ fd`는 서버와 클라이언트 간의 연결 ID입니다.
연결을 강제로 닫고이 연결의 데이터를 풀면``$ reset`

#### Return

the result of close the connection

연결을 닫은 결과

#### Example
