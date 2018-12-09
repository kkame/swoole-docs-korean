### swoole_process->exec

#### Prototype

```php
bool swoole_process->exec(string $execfile, array $args)
```

#### Illustration

Execute system commands:

시스템 명령 실행 :

The process will be replaced to be the system command process, but the pipe between the parent process will be kept.

프로세스가 시스템 명령 프로세스로 바뀌지 만 상위 프로세스 사이의 파이프가 유지됩니다.

If it needs to communication between the main process and child process, it must enable the redirection of stdin and stdout of child process.

주 프로세스와 하위 프로세스 간 통신이 필요한 경우 하위 프로세스의 stdin 및 stdout을 리디렉션 할 수 있어야합니다.

#### Parameter

- `$execfile` the absolute path of the command

-`$ execfile` 명령의 절대 경로

- `$args` the array of arguments for the command

-`$ args`는 명령 인수의 배열입니다.

#### Return

bool

#### Example
```php
<?php
// main process
$process = new swoole_process(function($process){
    //execute the external program
    $process->exec("/usr/bin/php", array('/code/swoole/process/testexec.php'));
}, true); // enable the redirection of stdin and stdout

$process->start();

//Inter-Process Communication Of main process and child process by stdin and stdout

$process->write("hello child process from main process");

$res = $process->read();

var_dump($res);

```
```php
<?php
// /code/swoole/process/testexec.php 
$fd = fopen('php://stdin', 'r');
$res = fread($fd, 123);
echo "the message from main process" . $res;
```
