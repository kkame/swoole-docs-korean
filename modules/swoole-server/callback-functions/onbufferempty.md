### onBufferEmpty

The event `bufferempty` happens when the buffer watermark is lowest.

`bufferempty` 이벤트는 버퍼 워터 마크가 가장 낮을 때 발생합니다.

#### Example

```php
function onBufferEmpty(Swoole\Server $serv, int $fd)
```
-  Set the configuration `server->buffer_low_watermark` to control the buffer low watermark
- When the event `bufferempty` is triggered, it could send data to client.

- 버퍼 low watermark를 제어하기 위해`server-> buffer_low_watermark` 설정을합니다.
-`bufferempty` 이벤트가 발생하면 클라이언트에게 데이터를 보낼 수 있습니다.
