# Swoole WebSocket server

The following PHP codes shows how to write a simple WebSocket server. The WebSocket server sends the client a message when the WebSocket connection is established.

다음 PHP 코드는 간단한 WebSocket 서버를 작성하는 방법을 보여줍니다. WebSocket 서버는 WebSocket 연결이 설정되면 클라이언트에게 메시지를 전송합니다.

The `swoole_websocket_server` class inherits from the class `swoole_server`.

`swoole_websocket_server` 클래스는`swoole_server` 클래스를 상속받습니다.

## Example Code

```php
<?php
$server = new swoole_websocket_server("127.0.0.1", 9501);

$server->on('open', function (swoole_websocket_server $server, $request) {
    echo "server: handshake success with fd{$request->fd}\n";
});

$server->on('message', function (swoole_websocket_server $server, $frame) {
    echo "receive from {$frame->fd}:{$frame->data},opcode:{$frame->opcode},fin:{$frame->finish}\n";
    $server->push($frame->fd, "This message is from swoole websocket server.");
});

$server->on('close', function ($ser, $fd) {
    echo "client {$fd} closed\n";
});

$server->start();
```

## Table of Contents

* [Events And Callback Functions](/modules/swoole-websocket-server/events-callbacks.md)

* [Methods List](/modules/swoole-websocket-server/methods.md)

* [Predefined Contants](/modules/swoole-websocket-server/constants.md)

* [Common Problems](/modules/swoole-websocket-server/common-problems.md)

> If the swoole_websocket_server has been setted the callback function of event `request`, it can be used as Http server.

> swoole_websocket_server가 이벤트`request`의 콜백 함수로 설정되면 HTTP 서버로 사용할 수 있습니다.

> If the swoole_websocket_server hasn't been setted the callback function of event `request` and received http request, it would repond http 400 error.

> swoole_websocket_server가 이벤트`request`의 콜백 함수를 설정하지 않고 http 요청을 받으면 http 400 오류를 다시 보냅니다.