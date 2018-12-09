### swoole_server->set 

#### Prototype

```php
void swoole_server->set(array $setting)
```

#### Illustration

Set the runtime settings of the swoole server. The settings can be accessed by `$server->setting` when the swoole server has started.

스풀 서버의 런타임 설정을 지정합니다. 스풀 서버가 시작되면 설정은`$ server-> setting`에 의해 액세스 될 수 있습니다.

#### Parameter

* `$setting` the array of runtime settings

*`$ setting`은 런타임 설정 배열입니다.

Setting example:

* max_conn => 10000: the max tcp connection number of the server
* daemonize => 1: enable the daemon mode the server process
* reactor_num => 2: set the number of system poll threads, the default setting is the number of CPU cores
* worker_num => 4: set the number of worker processes 
* max_request => 2000: the number of requests processed by the worker process before been recycled
* backlog => 128: TCP backlog number, the max number of connections waiting for acception
* open_cpu_affinity => 1: enable CPU affinity
* open_tcp_nodelay => 1: enable TCP_NoDelay
* tcp_defer_accept => 5: delay a period of time for the new connection before been accepted
* log_file => '/data/log/swoole.log': set the error logs location of the server
* open_eof_check => true: enable buffer for the data receiving
* package_eof => "\r\n\r\n": set EOF of the packages
* heartbeat_check_interval => 30: set the interval of health checking for the TCP connections
* heartbeat_idle_time => 60: set the max idle time before the idel connection been closed
* dispatch_mode = 1: dispatch mode for child processes:
    * 1: round robin assignment
    * 2: assignment by mod
    * 3: preemptive assignment

설정 예 :

* max_conn => 10000 : 서버의 최대 tcp 연결 번호
* daemonize => 1 : 서버 프로세스의 데몬 모드 활성화
* reactor_num => 2 : 시스템 폴링 스레드 수를 설정합니다. 기본 설정은 CPU 코어 수입니다
* worker_num => 4 : 작업자 프로세스 수 설정
* max_request => 2000 : 재활용되기 전에 작업자 프로세스에 의해 처리 된 요청 수
* backlog => 128 : TCP 백 로그 번호, 대기중인 연결의 최대 수
* open_cpu_affinity => 1 : CPU 선호도 사용
* open_tcp_nodelay => 1 : TCP_NoDelay 사용 가능
* tcp_defer_accept => 5 : 새 연결을 수락하기 전에 일정 기간 지연
* log_file => '/data/log/swoole.log': 서버의 오류 로그 위치를 설정하십시오
* open_eof_check => true : 데이터 수신을위한 버퍼 사용
* package_eof => "\ r \ n \ r \ n": 패키지의 EOF 설정
* heartbeat_check_interval => 30 : TCP 연결에 대한 상태 검사 간격 설정
* heartbeat_idle_time => 60 : idel 연결이 닫히기 전의 최대 유휴 시간을 설정합니다.
* dispatch_mode = 1 : 하위 프로세스의 디스패치 모드 :
    * 1 : 라운드 로빈 지정
    * 2 : mod에 의한 지정
    * 3 : 선제 과제


> Check [the full list of settings](/modules/swoole-server/configuratio.md)

> [전체 설정 목록] (/ modules / swoole-server / configuratio.md)을 확인하십시오.

#### Return

void

#### Example

```php
<?php
$server->set(array(
    'reactor_num' => 2, //reactor thread num
    'worker_num' => 4,    //worker process num
    'backlog' => 128,   //listen backlog
    'max_request' => 50,
    'dispatch_mode' => 1,
));
```
