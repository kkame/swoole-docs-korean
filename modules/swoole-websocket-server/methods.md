
## Method

The `swoole_websocket_server` class inherits from the class `swoole_server`. It has also its own method.

`swoole_websocket_server` 클래스는`swoole_server` 클래스를 상속받습니다. 또한 자체적 인 방법이 있습니다.

### swoole_websocket_server->push

#### Illustration

This method is to push the message to the client. The max length of message is 2M.

이 방법은 메시지를 클라이언트로 푸시하는 것입니다. 메시지의 최대 길이는 2M입니다.

#### Prototype

```php
bool swoole_websocket_server->push(int $fd, string $data, int $opcode = 1, bool $finish = true);
```
- `$fd` the id number of client. If the client isn't websocket client, the push will fail.

- `$data` the message to send

- `$opcode` the format of message to send. The default is text. If you want to send binary data, the value of this parameter should be `WEBSOCKET_OPCODE_BINARY`

- If the push of message succeeds, the return is `true` otherwise `false`

-`$ fd`는 클라이언트의 ID 번호입니다. 클라이언트가 websocket 클라이언트가 아닌 경우 푸시가 실패합니다.

-`$ data`는 보낼 메시지입니다.

-`$ opcode`는 보낼 메시지의 형식입니다. 기본값은 텍스트입니다. 바이너리 데이터를 보내려면이 매개 변수의 값은`WEBSOCKET_OPCODE_BINARY`이어야합니다.

- 메시지의 push가 성공하면 반환 값은 true이고, 그렇지 않으면 false이다.