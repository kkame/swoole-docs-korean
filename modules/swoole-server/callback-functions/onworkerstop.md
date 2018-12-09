### onWorkerStop

This event `workerstop` happens when the worker process stops.

이 이벤트 'workerstop'은 작업자 프로세스가 멈 추면 발생합니다.

In the callback function registered for the event `workerstop`, you can retrieve or release the resource for the worker process which stops.

`workerstop` 이벤트에 등록 된 콜백 함수에서 멈추는 작업자 프로세스의 리소스를 검색하거나 해제 할 수 있습니다.

> The abnormal stop of worker process will not trigger the event `workerstop`, for example, fatal error, core dump

> 작업자 프로세스의 비정상 종료로 인해 'workerstop'이벤트가 트리거되지 않습니다 (예 : 치명적인 오류, 코어 덤프).

#### Example

```php
function onWorkerStop(swoole_server $server, int $worker_id);
```
