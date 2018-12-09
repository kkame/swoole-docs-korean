### swoole_process::kill

#### Prototype

```php
bool swoole_process::kill($pid, $signo = SIGTERM);
```

#### Illustration

Send signal to the child process.

자식 프로세스에 신호를 보냅니다.

#### Parameter

- `$pid` the pid of child process

- `$signo` the signal to send, the default is `SIGTERM`

-`$ pid`는 자식 프로세스의 pid입니다.

-`$ signo '보낼 신호, 기본값은`SIGTERM`이다.

#### Return

if sends signal successfully, it returns true, otherwise it returns false.

신호가 성공적으로 전송되면 true를 반환하고, 그렇지 않으면 false를 반환합니다.

#### Example
```php
<?php
$child_num = 3;
$child_processes = [];
for($i = 1; $i <= $child_num; $i++)
{
    $process = new swoole_process(function($worker){
        echo "the pid of child process is " . $worker->pid . "\n";
        
        $worker->name("php child process");
        
        sleep(rand(20, 60));
        
    }, false, false);
    
    $res = $process->useQueue(0, 2);
    
    $pid = $process->start();

    $child_processes[(string)$pid] = $process;
}

sleep(5);

foreach($child_processes as $pid => $child_process)
{
    $ret = swoole_process::kill($pid);
    var_dump($ret);

    $ret = swoole_process::wait();
    var_dump($ret);
}
```
