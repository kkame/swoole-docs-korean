### onBufferFull

The event `bufferfull` happens when the buffer watermark is highest.

'bufferfull'이벤트는 버퍼 워터 마크가 가장 높을 때 발생합니다.

#### Example

```php
function onBufferFull(Swoole\Server $serv, int $fd)
```
-  Set the configuration `server->buffer_high_watermark` to control the buffer high watermark
- When the event `bufferfull` is triggered, it should not send data to client any more.

- 버퍼 최상위 워터 마크를 제어하기 위해`server-> buffer_high_watermark` 설정을합니다.
-`bufferfull` 이벤트가 발생하면 클라이언트에게 더 이상 데이터를 보내면 안됩니다.