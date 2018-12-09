### swoole_server->task

#### Prototype

```php
int swoole_server->task(mixed $data, int $dst_worker_id = -1, callable $callback = NULL)
```

#### Illustration

Send data to the task worker processes.

작업 작업자 프로세스에 데이터를 보냅니다.

> To call this method, it needs to set [the configuration of task_worker_num](/modules/swoole-server/configuration/task_worker_num.md) and the callback function of [onTask](/modules/swoole-server/callback-functions/ontask.md) and [onFinish](/modules/swoole-server/callback-functions/onfinish.md)
> This method is non-blocking and return immediately after sending the task data to the pool of task worker.

>이 메소드를 호출하려면 [task_worker_num의 구성] (/ modules / swoole-server / configuration / task_worker_num.md)과 [onTask]의 콜백 함수 (/ modules / swoole-server / callback-functions / ontask.md) 및 [onFinish] (/ modules / swoole-server / callback-functions / onfinish.md)
>이 메서드는 비 블로킹이며 작업 데이터를 작업 작업자 풀로 보낸 직후 반환됩니다.

#### Parameter

* `$data`	the data which is to send to the task worker, its type could any type except fot resource
* `$dst_worker_id` the id number of task worker. If this parameter hasn't been passed, the swoole server would select a random and unoccupied task worker process.
* `$callback` the callback function be called when the task has been finished. If this parameter has been passed, there is no need to register the callback function of the event of `onFinish`

*`$ data`는 작업 작업자에게 보낼 데이터이며, 그 유형은 fot 리소스를 제외한 모든 유형이 될 수 있습니다
*`$ dst_worker_id`는 작업 작업자의 ID 번호입니다. 이 매개 변수가 전달되지 않은 경우 스풀 서버는 임의의 비어있는 작업 작업자 프로세스를 선택합니다.
*`$ callback` 콜백 함수는 작업이 끝나면 호출됩니다. 이 매개 변수가 전달되면 onFinish 이벤트의 콜백 함수를 등록 할 필요가 없습니다.

#### Return

If the call of this method succeeds, the return is the task id which identifies the task
If the call of this method fails, the return is false

이 메서드의 호출이 성공하면, 반환 값은 태스크를 식별하는 태스크 ID입니다.
이 메서드 호출이 실패하면 반환 값은 false입니다.

#### Example

```php
<?php
$task_id = $server->task("some data");

$server->task("taskcallback", -1, function (swoole_server $serv, $task_id, $data) {
    echo "Task Callback: ";
    var_dump($task_id, $data);
});
```
