### swoole_process::wait

#### Prototype

```php
array swoole_process->wait(bool $blocking = true);
```

#### Illustration

Wait for the events of child processes.

하위 프로세스의 이벤트를 기다립니다.

#### Parameter

- `$blocking` if block the execution of this method when called

- 호출 될 때이 메소드의 실행을 차단하는 경우 '$ blocking'

#### Return

array, it contains the exit code, pid and signal of child process.

배열에는 자식 프로세스의 종료 코드, pid 및 신호가 포함됩니다.

```php
array('code' => 0, 'pid' => 15001, 'signal' => 15);
```

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
        
        sleep(rand(2, 6));

        $worker->exit(rand(1, 255));
        
    }, false, false);
    
    $res = $process->useQueue(0, 2);
    
    $pid = $process->start();

    $child_processes[(string)$pid] = $process;
}

$i = 1;

swoole_process::signal(SIGCHLD, function($sig) use (&$i){
        // there may be multi processes which exit at the same time
        while($ret = swoole_process::wait(false)){
            var_dump($ret);
        }
        
        var_dump($i);
        
        if($i >= 3)
        {
            exit(0);
        }
        
        $i++;
    }
);

echo "Wait for exit of child process\n";
```
