### swoole_server->sendMessage

#### Prototype

```php
bool swoole_server->sendMessage(string $message, int $dst_worker_id)
```

#### Illustration

Send message to worker processes by ID. This message will trigger the event of `pipe message` and the process which has received this message would call the callback function registered for `pipe message`.

ID로 작업자 프로세스에 메시지 보내기 이 메시지는`pipe message` 이벤트를 발생시키고이 메시지를받은 프로세스는`pipe message`에 등록 된 콜백 함수를 호출합니다.

> There is no length limit for the message, but the server will use the temporary file in the memory if the length of file is bigger than 8K
> In the task worker process, `sendMessage` is blocking
> In the worker process, `sendMessage` is async.

> 메시지의 길이 제한은 없지만 파일 길이가 8K보다 큰 경우 서버는 메모리의 임시 파일을 사용합니다
> 작업 작업자 프로세스에서`sendMessage`가 블로킹 중입니다.
> 작업자 프로세스에서`sendMessage`는 비동기입니다.

#### Parameter

* `$message`	the string of message to send
* `$dst_worker_id` the integer of worker process which is between 0 and (worker_num + task_worker_num - 1)

*`$ message` 보낼 문자열
*`$ dst_worker_id`는 0과 (worker_num + task_worker_num - 1) 사이의 작업자 프로세스의 정수입니다.

#### Return

the result of send message to worker

작업자에게 메시지를 보낸 결과

#### Example

```php
<?php
$serv = new swoole_server("0.0.0.0", 9501);
$serv->set(array(
    'worker_num' => 2,
    'task_worker_num' => 2,
));
$serv->on('pipeMessage', function($serv, $src_worker_id, $data) {
    echo "#{$serv->worker_id} message from #$src_worker_id: $data\n";
});
$serv->on('task', function ($serv, $task_id, $from_id, $data){
    var_dump($task_id, $from_id, $data);
});
$serv->on('finish', function ($serv, $fd, $from_id){

});
$serv->on('receive', function (swoole_server $serv, $fd, $from_id, $data) {
    if (trim($data) == 'task')
    {
        $serv->task("async task coming");
    }
    else
    {
        $worker_id = 1 - $serv->worker_id;
        $serv->sendMessage("hello task process", $worker_id);
    }
});

$serv->start();
```
