### swoole_process->read

#### Prototype

```php
string swoole_process->read(int $buffer_size=8192);
```

#### Illustration

Read data from the pipe:

파이프에서 데이터 읽기 :

#### Parameter

- `$buffer_size` the size of buffer

-`$ buffer_size`는 버퍼의 크기입니다.

#### Return

the string of data readed

읽힌 데이터의 캐릭터 라인

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
