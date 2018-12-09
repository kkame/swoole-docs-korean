### onTask

The event `task` happens when the worker process send a task data to task worker processed pool.

'작업'이벤트는 작업자 프로세스가 작업자가 처리 한 풀에 작업 데이터를 보낼 때 발생합니다.

The task worker process which has received the task data will call the callback function registered for the event `task`.

작업 데이터를받은 작업 작업자 프로세스는 이벤트`task`에 등록 된 콜백 함수를 호출합니다.

When the task worker process is processing the task, its status is busy and changes to idle after finishing the task.

작업 작업자 프로세스가 작업을 처리 할 때 작업 상태가 사용 중이며 작업을 마친 후 유휴 상태로 변경됩니다.

#### Example

```php
function onTask(swoole_server $serv, int $task_id, int $src_worker_id, mixed $data);
```

- `$serv` the swoole server object

-`$ serv`는 스풀 서버 객체입니다.

- `$task_id` the id number of task, the combination of `$task_id` and `$src_worker_id` is an unique identification for task

-`$ task_id`는 작업의 id 번호이고,`$ task_id`와`$ src_worker_id`의 조합은 작업을위한 유일한 식별 정보입니다

- `$data` the task data

-`$ data`는 작업 데이터입니다.

#### Return task result to worker process

In the callback function registered for event `task`, the return of this function is the result of task and will be sent to the worker process which sent the task. You can also return the result of task by calling `swoole_server->finish()`.

이벤트`task`에 등록 된 콜백 함수에서이 함수의 리턴은 task의 결과이며 태스크를 보낸 worker 프로세스로 보내질 것이다. `swoole_server-> finish ()`를 호출하여 작업 결과를 반환 할 수도 있습니다.

When the worker process has received the task result, the event `finish` would be triggered and call the function registered for event `finish` in the worker process.

작업자 프로세스가 작업 결과를 수신하면 작업자 프로세스에서 'finish'이벤트가 트리거되고 'finish'이벤트에 대해 등록 된 함수를 호출합니다.