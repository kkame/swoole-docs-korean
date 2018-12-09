### swoole_process->start

#### Prototype

```php
int swoole_process->start();
```

#### Illustration

Fork the swoole child process constructed and return the *PID* of the child process, or return false if the fork is failed. 

fork 된 swoole 자식 프로세스가 생성되고 자식 프로세스의 * PID *를 반환하거나 fork가 실패하면 false를 반환합니다.

Attributes of the child process:

하위 프로세스의 속성 :

```php
<?php
$process->pid;  // the pid of child process
$process->pipe; // the file descriptor of pipe
```

#### Parameter

void

#### Return

the pid of child process, or return false if the fork is failed. You can use `swoole_errno` and `swoole_strerror` to get the code and information of error.

아이 프로세스의 PID. fork가 실패했을 경우는 false를 돌려 준다 `swoole_errno`와`swoole_strerror`를 사용하면 오류의 코드와 정보를 얻을 수 있습니다.

#### Example
```
<?php
$workers = [];
$worker_num = 3;

for($i=0;$i<$worker_num ; $i++){
    
    $process = new swoole_process('process');
    $pid = $process->start();
    $workers[$pid] = $process;

    echo "create a child process\n";
}

foreach($workers as $process)
{
    swoole_event_add($process->pipe, function ($pipe) use($process){
        $data = $process->read();
        echo "RECV: " . $data . "\n";
    });
}

function process(swoole_process $process){
    sleep(rand(5, 10)); 
    $process->write($process->pid);
    echo $process->pid . "\n";
}
```
