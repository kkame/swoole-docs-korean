### pid_file

The file path which the master process id saves in.

마스터 프로세스 ID가 저장하는 파일 경로.

#### Usage

```php
$server->set(array(
    'pid_file' => __DIR__.'/server.pid',
));
```
The pid of master process saves in the `pid_file` after the swoole server starts. And this file is deleted after the swoole server stops normally.

마스터 프로세스의 PID는 스풀 서버가 시작된 후`pid_file`에 저장됩니다. 그리고이 파일은 swoole 서버가 정상적으로 중지 된 후에 삭제됩니다.
