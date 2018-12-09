### swoole_process->write

#### Prototype

```php
int swoole_process->write(string $data);
```

#### Illustration

Write data into the pipe and communicate with the parent process or child processes.

파이프에 데이터를 쓰고 상위 프로세스 또는 하위 프로세스와 통신하십시오.

#### Parameter

- `$data` the string of data to communicate

-`$ data`는 통신 할 문자열입니다.

#### Return

int the length of data sent

int 전송 된 데이터의 길이

#### Example
```php
<?php
$process = new swoole_process(function($worker){
    echo "the pid of child process is " . $worker->pid . "\n";
    echo "the file descriptor of pipe is " . $worker->pipe . "\n";
    
    $res = $worker->write("Hello main process\n");
    var_dump(strlen("Hello main process\n"));
    var_dump($res);
    
    $worker->name("php child process");
}, false, 2);

$process->start();

usleep(100);

echo $process->read();
```
