### onOpen

The event `open` happens when the websocket server and client has created the connection and finished the handshake. And the callback function registered for event `open` will be called.

'open'이벤트는 websocket 서버와 클라이언트가 연결을 생성하고 핸드 셰이크를 마쳤을 때 발생합니다. 그리고 이벤트`open`에 등록 된 콜백 함수가 호출됩니다.

#### Example

```php
function onOpen(swoole_websocket_server $svr, swoole_http_request $req)
```

- `$req` the object of http request, it contains the information of client

-`$ req`는 HTTP 요청의 객체이며 클라이언트의 정보를 담고 있습니다.

> In the callback function for event `open`, you can push message to client and close the connection.

> 이벤트`open`에 대한 콜백 함수에서 메시지를 클라이언트에 푸시하고 연결을 닫을 수 있습니다.

> The callback function for event `open` is optional.

> 이벤트`open`에 대한 콜백 함수는 선택 사항입니다.
