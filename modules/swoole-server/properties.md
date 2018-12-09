### Properties List

#### Table of Contents

- swoole_server::$setting
- swoole_server::$master_pid
- swoole_server::$manager_pid
- swoole_server::$worker_id
- swoole_server::$worker_pid
- swoole_server::$taskworker
- swoole_server::$connections

#### Properties

##### swoole_server::$setting

the setting seted for the swoole server object

스풀 서버 객체에 대해 설정된 설정

```php
$serv = new swoole_server('127.0.0.1', 9501);
$serv->set(array('worker_num' => 4));

echo $serv->setting['worker_num'];
```

##### swoole_server::$master_pid

the pid of master process

마스터 프로세스의 PID

##### swoole_server::$manager_pid

the pid of manager process

관리자 프로세스의 PID

##### swoole_server::$worker_id

the id number of current worker process or task worker process

현재 작업자 프로세스 또는 작업 작업자 프로세스의 ID 번호

##### swoole_server::$worker_pid

the pid of current worker process or task worker process

현재 작업자 프로세스 또는 작업 작업자 프로세스의 PID

##### swoole_server::$taskworker

true: current process is task worker process
false: current process isn worker process

true : 현재 프로세스는 작업 작업자 프로세스입니다.
false : 현재 프로세스가 작업자 프로세스가 아닙니다.


##### swoole_server::$connections

the list of all the connections

모든 연결 목록

```php
foreach($server->connections as $fd)
{
    $server->send($fd, "hello");
}

echo "The server has ".count($server->connections). " connections\n";
```
