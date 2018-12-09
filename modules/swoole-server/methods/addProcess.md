### swoole_server->addProcess

#### Prototype

```php
bool swoole_server->addProcess(swoole_process $process)
```

#### Illustration

Add a user defined child process to the server. The process can be used as monitoring or other tasks.

사용자 정의 하위 프로세스를 서버에 추가하십시오. 이 프로세스는 모니터링 또는 다른 작업으로 사용할 수 있습니다.

#### Parameter

* `$process` the swoole_process object defined by user
    - Check [the document of swoole_proccess](/modules/swoole-process/introduction.md)

*`$ process`는 사용자가 정의한 swoole_process 객체입니다.
     - [swoole_process의 문서] (/ modules / swoole-process / introduction.md)를 확인하십시오.

##### Return

The return value indicates the result of add proccess to swoole server.

반환 값은 swoole 서버에 추가 프로세스의 결과를 나타냅니다.

##### Example:

```php
<?php
$server = new swoole_server('127.0.0.1', 9501);

$process = new swoole_process(function($process) use ($server) {
    while (true) {
        $msg = $process->read();
        foreach($server->connections as $conn) {
            $server->send($conn, $msg);
        }
    }
});

$server->addProcess($process);

$server->on('receive', function ($serv, $fd, $from_id, $data) use ($process) {
    // send the data received to all the child processes
    $process->write($data);
});

$server->start();
```
