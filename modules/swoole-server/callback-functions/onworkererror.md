### onWorkerError

When there is error or exception in the worker process or task worker process, the event `workererror` happens in the manager process.

작업자 프로세스 또는 작업 작업자 프로세스에 오류 또는 예외가 발생하면 관리자 프로세스에서 'workererror'이벤트가 발생합니다.

The callback function registered for event `workererror` is called in manager process.

`workererror` 이벤트에 등록 된 콜백 함수는 manager 프로세스에서 호출됩니다.

#### Example

```php
void onWorkerError(swoole_server $serv, int $worker_id, int $worker_pid, int $exit_code, int $signal);
```

- `$worker_id` the id number of worker

- `$worker_pid` the pid of worker process

- `$exit_code` the exit code of worker process

- `$signal` the exit signal of worker process

-`$ worker_id` 작업자의 id 번호

-`$ worker_pid` 작업자 프로세스의 PID

-`$ exit_code` 작업자 프로세스의 종료 코드

-`$ signal` 작업자 프로세스의 종료 신호