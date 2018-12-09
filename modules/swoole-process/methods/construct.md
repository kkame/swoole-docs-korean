### swoole_process->__construct

#### Prototype

```php
swoole_process swoole_process->__construct(mixed $function, bool $redirect_stdin_stdout = false, int $create_pipe = 2);
```

#### Illustration

Construct a child process with the callback function executed in the child process, optionally redirect the standard I/O to pipes between the parent process and the child processes.

자식 프로세스에서 실행되는 콜백 함수를 사용하여 자식 프로세스를 생성하고 선택적으로 표준 I / O를 부모 프로세스와 자식 프로세스 사이의 파이프로 리디렉션합니다.

> When the parent process is stopped, the child processes will receive *CLOSE* event from the pipe.

> 상위 프로세스가 중지되면 하위 프로세스는 파이프에서 * CLOSE * 이벤트를 수신합니다.

#### Parameter

- `$function` the callback function executed in the child process. If the execution of this function in the child process finished, the child process would exit.

-`$ function`은 자식 프로세스에서 실행 된 콜백 함수입니다. 자식 프로세스에서이 함수의 실행이 끝나면 자식 프로세스는 종료됩니다.

- `$redirect_stdin_stdout` if enable the redirection of stdin and stdout of child process. If `$redirect_stdin_stdout` is `true`, the output of child process will be written to the the pipe of main process and the input of child process will come from the pipe. The default of mode is blocking. 

-`$ redirect_stdin_stdout` : 자식 프로세스의 stdin과 stdout의 방향 전환을 가능하게한다. `$ redirect_stdin_stdout`이`true`이면, 자식 프로세스의 출력은 메인 프로세스의 파이프에 쓰여지고 자식 프로세스의 입력은 파이프로부터 온다. 기본 모드가 차단 중입니다.

- `$create_pipe` if create the pipe. `0` don't create the pipe, `1` create the `SOCK_STREAM` pipe, `2` create the `SOCK_DGRAM` pipe. If `$redirect_stdin_stdout` is `true`, this parameter is setted to `1`. 

파이프를 만들려면`$ create_pipe`. `0`은 파이프를 생성하지 않고,`1`은`SOCK_STREAM` 파이프를 생성하고,`2`는`SOCK_DGRAM` 파이프를 생성합니다. `$ redirect_stdin_stdout`가`true`이면이 매개 변수는`1`로 설정됩니다.

#### Return

the object of `swoole_process`

`swoole_process`의 객체

#### Example
```
<?php
$process = new swoole_process(function($process){
    echo "the pid of child process is " . $worker->pid . "\n";
    echo "the file descriptor of pipe is " . $worker->pipe . "\n";
    $process->write("hello");
}, false, true);

$process->start();

usleep(100);

echo $process->read();
```
