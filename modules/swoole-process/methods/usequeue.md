### swoole_process->useQueue

#### Prototype

```php
bool swoole_process->useQueue(int $msgkey = 0, int $mode = 2);
```

#### Illustration

Create a message queue as the communication method between the parent process and child processes.

상위 프로세스와 하위 프로세스 간의 통신 방법으로 메시지 대기열을 작성하십시오.

> It can't use the pipe and message queue the same time.

> 파이프와 메시지 대기열을 동시에 사용할 수 없습니다.

> Before the start of the swoole process, it can also call the method `push` and `pop`

> 스풀 프로세스가 시작되기 전에`push`와`pop` 메서드를 호출 할 수 있습니다

#### Parameter

- `$msgkey` the ID of the message queue, the default value is *ftok(__FILE__, 1)*

- `$mode` `2` : competitive mode, all the processes created will compete for the message received by the message queue.
                Set the mode to `$mode | swoole_process::IPC_NOWAIT` to make the message queue non-blocking. In the non-blocking mode, it will return immediately when the method `push` is called in the condition of full queue and the method `pop` is called in the condition of empty queue.
                
-`$ msgkey` 메시지 큐의 ID이며, 기본값은 * ftok (__ FILE__, 1)입니다.

-`$ mode``2` : 경쟁 모드, 생성 된 모든 프로세스는 메시지 큐에 의해 수신 된 메시지를 놓고 경쟁합니다.
                 모드를`$ mode | swoole_process :: IPC_NOWAIT`를 사용하여 메시지 대기열을 비 차단으로 만듭니다. non-blocking 모드에서는 full queue의 조건에서`push` 메서드가 호출되고 빈 큐의 조건에서`pop` 메서드가 호출 될 때 즉시 반환됩니다.
                

#### Return

bool

#### Example
```
<?php
$child_num = 3;
$child_processes = [];
for($i = 1; $i <= $child_num; $i++)
{
    $process = new swoole_process(function($worker){
        echo "the pid of child process is " . $worker->pid . "\n";
        
        $worker->name("php child process");
        
        $recv = $worker->pop();
        
        echo "To child process " . $worker->pid .  " : " . $recv;

        echo "the child process " . $worker->pid . " exited\n";
        
        exit(0);
    }, false, false);
    
    $res = $process->useQueue(0, 2);
    
    $pid = $process->start();

    $child_processes[(string)$pid] = $process;
}

foreach($child_processes as $pid => $child_process)
{
    $child_process->push("From main process : Hello child process {$pid}\n");
}
```
