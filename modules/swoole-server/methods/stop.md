### swoole_server->stop

#### Prototype

```php
void swoole_server->stop($worker_id = -1);
```

#### Illustration

Stop current worker process or worker process by ID, this will emit 'WorkerStop' event and trigger the WorkerStop callback function.

ID를 기준으로 현재 작업자 프로세스 또는 작업자 프로세스를 중지하면 'WorkerStop'이벤트가 발생하고 WorkerStop 콜백 함수가 트리거됩니다.

- Use the method to replace the function `exit/die` to end the worker process

-이 메소드를 사용하여 'exit / die'함수를 대체하여 작업자 프로세스를 끝냅니다.

#### Parameter

* $worker_id : the id of worker process

* $ worker_id : 작업자 프로세스의 ID

#### Return

the result if the swoole server starts successfully 

스풀 서버가 성공적으로 시작된 경우의 결과

#### Example

```php
<?php
$server = new swoole_server("127.0.0.1", 9501);
$server->on('connect', function ($server, $fd){
    echo "New connection established: #{$fd}.\n";
});
$server->on('receive', function ($server, $fd, $from_id, $data) {
    if(trim($data) == "stop")
    {
        $server->stop();
    }
    else
    {
        $server->send($fd, "Echo to #{$fd}: \n".$data);
        $server->close($fd);
    }
});

$server->on('WorkerStop', function($server, $worker_id){
    echo $worker_id . " stop\n";
});

$server->on('close', function ($server, $fd) {
    echo "Connection closed: #{$fd}.\n";
});
$server->start();
```
