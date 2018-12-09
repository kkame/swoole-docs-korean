### swoole_process->exit

#### Prototype

```php
int swoole_process->exit(int $status=0);
```

#### Illustration

Stop the child process.

자식 프로세스를 중지하십시오.

#### Parameter

- `$status` the exit status code of process. If this code is `0`, it stands for that the process exits normally and continue to execute the registered shutdown function. If this code isn't `0`, it stands for that the process exits unexpectedly and stops immediately. The father process can use `swoole_process::wait` to get the exit event and code from the child process.

-`$ status` 프로세스의 종료 상태 코드. 이 코드가 '0'이면 프로세스가 정상적으로 종료되고 등록 된 시스템 종료 기능이 계속 실행됩니다. 이 코드가 '0'이 아닌 경우 프로세스가 예기치 않게 종료되고 즉시 중지됨을 의미합니다. 아버지 프로세스는`swoole_process :: wait`를 사용하여 자식 프로세스에서 이탈 이벤트와 코드를 얻을 수 있습니다.

#### Return

int

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

foreach($child_processes as $child_process)
{
    $ret = swoole_process::wait();
    var_dump($ret);
}
```
