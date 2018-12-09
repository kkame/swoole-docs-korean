### swoole_server->taskwait

#### Prototype

```php
string/bool swoole_server->taskwait(mixed $task_data, float $timeout = 0.5, int $dst_worker_id = -1)
```

#### Illustration

The `swoole_server->taskwait` is similar to `swoole_server->task`. The two methods both send task data to the task worker pool to execute, but the former is blocking.

`swoole_server-> taskwait`는`swoole_server-> task`와 유사합니다. 두 가지 방법은 모두 작업 데이터를 작업 작업자 풀에 보내 실행하지만 전자는 실행을 차단합니다.

#### Parameter

* `$task_data`	the data which is to send to the task worker, its type could any type except fot resource
* `$timeout`    the time of timeout 
* `$dst_worker_id` the id number of task worker. If this parameter hasn't been passed, the swoole server would select a random and unoccupied task worker process.

*`$ task_data`는 작업 작업자에게 보낼 데이터이며, 그 유형은 fot 리소스를 제외한 모든 유형이 될 수 있습니다
*`$ timeout`은 타임 아웃 시간입니다.
*`$ dst_worker_id`는 작업 작업자의 ID 번호입니다. 이 매개 변수가 전달되지 않은 경우 스풀 서버는 임의의 비어있는 작업 작업자 프로세스를 선택합니다.

#### Return

If the call of this method succeeds, the return is the result of task
If the execution of this method exceeds the time of timeout, the return is false

이 메서드의 호출이 성공하면 반환은 작업의 결과입니다.
이 메서드의 실행이 타임 아웃 시간을 넘으면 반환 값은 false입니다.

#### Example
