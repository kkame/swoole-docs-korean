### onFinish

When the task finished, the task result would be sent to worker process and trigger the event `finish`.

작업이 끝나면 작업 결과가 작업자 프로세스로 전송되어 'finish'이벤트가 트리거됩니다.

#### Example

```php
void onFinish(swoole_server $serv, int $task_id, string $data)
```

- `$serv` the swoole server object

- `$task_id` the id number of task

- `$data` the result of task

-`$ serv`는 스풀 서버 객체입니다.

-`$ task_id`는 작업의 id 번호입니다.

-`$ data`는 작업의 결과입니다.