### onClose

The event `close` happens when the TCP connection between the client and the server is closed.

이벤트`close`는 클라이언트와 서버 간의 TCP 연결이 닫힐 때 발생합니다.

The worker process will call the callback function registered for the event `close`.

작업자 프로세스는 이벤트`close`에 등록 된 콜백 함수를 호출합니다.

#### Example

```php
function onClose(swoole_server $server, int $fd, int $reactorId);
```

- `$server` the swoole server object

- `$fd` the id number of client

- `$reactorId` the id number of reactor thread, when the `$reactorId` < 0, the connection is closed by server.

-`$ server`는 swoole 서버 객체입니다.

-`$ fd`는 클라이언트의 ID 번호입니다.

-`$ reactorId` 원자로 스레드의 ID 번호.`$ reactorId` <0 일 때, 서버에 의해 연결이 닫힙니다.
