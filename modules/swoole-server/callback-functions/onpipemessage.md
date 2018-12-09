### onPipeMessage

When the worker process or task worker process receives the message sent by `sendMessage`, the event `pipeMessage` happens. 

작업자 프로세스 나 작업 작업자 프로세스가`sendMessage`가 보낸 메시지를 받으면`pipeMessage` 이벤트가 발생합니다.

The callback function registered for event `pipeMessage` will be called.

이벤트`pipeMessage`에 대해 등록 된 콜백 함수가 호출됩니다.

#### Example

```php
void onPipeMessage(swoole_server $server, int $from_worker_id, string $message);
```

- `$from_worker_id` the id number of worker when the message from

- `$message` the message

-`$ from_worker_id`에서 보낸 메시지의 작업자 ID 번호

-`$ message` 메시지