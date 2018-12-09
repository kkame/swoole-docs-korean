### onMessage

The event `message` happens when the swoole websocket server receives the data frame from the client.

`message` 이벤트는 swoole websocket 서버가 클라이언트로부터 데이터 프레임을 받으면 발생합니다.

#### Example

```php
function onMessage(swoole_server $server, swoole_websocket_frame $frame)
```

- `$frame` the object of class `swoole_websocket_frame`. It contains the infomation from the client

-`$ frame`은`swoole_websocket_frame` 클래스의 객체입니다. 그것은 클라이언트로부터의 정보를 포함합니다.

> For swoole websocket server, it must set the callback function for the event `message`

> swoole websocket 서버의 경우, 이벤트`message`에 대한 콜백 함수를 설정해야합니다

> The `ping` frame from the client will not trigger the event `message` and the swoole websocket server will respond `pong` automatically.

> 클라이언트의`ping` 프레임은`message` 이벤트를 발생시키지 않으며 swoole websocket 서버는`pong`을 자동으로 응답합니다.

#### swoole_websocket_frame

The class `swoole_websocket_frame` has four properties:

`swoole_websocket_frame` 클래스에는 4 개의 프로퍼티가 있습니다 :

- `$frame->fd` the id number of client

- `$frame->data` the data from the client. It can be text or binary data which can be distinguished by the value of `$frame->opcode`.

- `$frame->opcode` the opcode type of websocket

- `$frame->finish` if the data frame is complete.

-`$ frame-> fd` 클라이언트의 ID 번호

-`$ frame-> data`는 클라이언트의 데이터입니다. `$ frame-> opcode`의 값으로 구별 할 수있는 텍스트 또는 바이너리 데이터가 될 수 있습니다.

-`$ frame-> opcode`는 웹 소켓의 opcode 타입입니다.

- 데이터 프레임이 완료되면`$ frame-> finish '.

#### OpCode and Data type

- WEBSOCKET_OPCODE_TEXT = 0x1, text

- WEBSOCKET_OPCODE_BINARY = 0x2, binary data
