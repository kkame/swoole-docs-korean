### swoole_server->start

#### Prototype

```php
bool swoole_server->start()
```

#### Illustration

Start the swoole server, it will create worker_num + 2 processes by default:

스풀 서버를 시작하면 기본적으로 worker_num + 2 프로세스가 생성됩니다.

* main process: running multiple threads reactor, receive new connections and assign connections to worker processes
* manager process: managing the worker processes
* worker_num * child processes: process the data and business logics

* 주요 프로세스 : 다중 스레드 reactor 실행, 새 연결 수신 및 작업자 프로세스 연결 지정
* 관리자 프로세스 : 작업 프로세스 관리
* worker_num * 자식 프로세스 : 데이터 및 비즈니스 로직 처리

#### Parameter

void

#### Return

the result if the swoole server starts successfully 

스풀 서버가 성공적으로 시작된 경우의 결과

#### Example

```php
<?php
$server = new swoole_server("127.0.0.1", 9501);
$server->on('connect', function ($server, $fd){
    echo "New connection established: #{$fd}.\n";
});
$server->on('receive', function ($server, $fd, $from_id, $data) {
    $server->send($fd, "Echo to #{$fd}: \n".$data);
    $server->close($fd);
});
$server->on('close', function ($server, $fd) {
    echo "Connection closed: #{$fd}.\n";
});
$server->start();
```
