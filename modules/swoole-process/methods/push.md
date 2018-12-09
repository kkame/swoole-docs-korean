### swoole_process->push

#### Prototype

```php
bool swoole_process->push(string $data);
```

#### Illustration

Write and push data into the message queue.

데이터를 쓰고 메시지 대기열로 밀어 넣습니다.

#### Parameter

- `$data` the data to push to the queue, the default value is 8192 Bytes and the max value is 65536 Bytes.

-`$ data`는 큐에 넣을 데이터이고, 기본값은 8192 바이트이고 최대 값은 65536 바이트입니다.

#### Return

if failed, it returns `false`. Or it returns `true`.

실패하면`false`를 반환합니다. 아니면 true를 반환합니다.

In the blocking mode, if the queue is full, the call of this method will block.

차단 모드에서 큐가 가득 차면이 메서드 호출이 차단됩니다.

In the non-blocking mode, if the queue is full, the call of this method will return `false` immediately.

비 블로킹 모드에서는, 큐가 가득 찬 경우,이 메소드의 호출은 즉시`false`를 리턴합니다.

#### Example
```php
<?php

$workers = [];
$worker_num = 2;

for($i = 0; $i < $worker_num; $i++)
{
    $process = new swoole_process('callback_function', false, false);
    $process->useQueue();
    $pid = $process->start();
    $workers[$pid] = $process;
}

function callback_function(swoole_process $worker)
{
    echo "Child process started, PID=".$worker->pid."\n";
    //recv data from the parent process
    $recv = $worker->pop();
    echo "Data received from the parent process: $recv\n";
    sleep(2);
    $worker->exit(0);
}

foreach($workers as $pid => $process)
{
    $process->push("hello child process [$pid]\n");
}

for($i = 0; $i < $worker_num; $i++)
{
    $ret = swoole_process::wait();
    $pid = $ret['pid'];
    unset($workers[$pid]);
    echo "Child process exit, PID=".$pid.PHP_EOL;
}
```
