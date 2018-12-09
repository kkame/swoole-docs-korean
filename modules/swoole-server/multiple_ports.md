### Listening On Multiple Ports

The swoole supports listening on multiple ports and analyzing multiple protocols.

swoole은 여러 포트에서 수신 대기하고 여러 프로토콜을 분석 할 수 있습니다.

You can set different protocols and callback functions on different ports. SSL/TLS can also enabled on certain port.

다른 포트에서 다른 프로토콜과 콜백 기능을 설정할 수 있습니다. 특정 포트에서 SSL / TLS를 활성화 할 수도 있습니다.

- If the listening on new port hasn't setted the protocal, it will be in the no protocal mode.

- If the listening on new port hasn't setted the callback functions, it will use the callback functions of `$server`.

- The return of `$server->listen` is object of `swoole_server_port`

- The callback functions setted for different ports still run in same worker process.


- 새 포트에서 청취가 프로토 콜을 설정하지 않으면 프로토콜 없음 모드가됩니다.

- 새로운 포트에서 듣기가 콜백 함수를 설정하지 않았다면, 그것은`$ server`의 콜백 함수를 사용할 것입니다.

-`$ server-> listen`의 반환 값은`swoole_server_port`의 객체입니다.

- 다른 포트에 대해 설정된 콜백 기능은 여전히 동일한 작업자 프로세스에서 실행됩니다.

#### Listen on new port

```php
$port1 = $server->listen("127.0.0.1", 9501, SWOOLE_SOCK_TCP);
$port2 = $server->listen("127.0.0.1", 9502, SWOOLE_SOCK_UDP);
$port3 = $server->listen("127.0.0.1", 9503, SWOOLE_SOCK_TCP | SWOOLE_SSL);
```

#### Set protocol
```php
$port1->set([
    'open_length_check' => true,
    'package_length_type' => 'N',
    'package_length_offset' => 0,
    'package_max_length' => 800000,
]);

$port3->set([
    'open_eof_split' => true,
    'package_eof' => "\r\n",
    'ssl_cert_file' => 'ssl.cert',
    'ssl_key_file' => 'ssl.key',
]);
```

#### Set callback functions of events
```php
$port1->on('connect', function ($serv, $fd){
    echo "Client:Connect.\n";
});

$port1->on('receive', function ($serv, $fd, $from_id, $data) {
    $serv->send($fd, 'Swoole: '.$data);
    $serv->close($fd);
});

$port1->on('close', function ($serv, $fd) {
    echo "Client: Close.\n";
});

$port2->on('packet', function ($serv, $data, $addr) {
    var_dump($data, $addr);
})
```

#### Optional configurations for swoole_server_port object

The swoole_server_port object can only set part of [the configurations list of swoole_server](/modules/swoole-server/configuration.md)

swoole_server_port 객체는 [swoole_server의 구성 목록] (/ modules / swoole-server / configuration.md)의 일부만 설정할 수 있습니다.

- If the swoole_server_port object hasn't set any configuration, it will use the configurations of the main swoole server object.

- swoole_server_port 객체가 구성을 설정하지 않으면 주 swoole 서버 객체의 구성을 사용합니다.

- If the main server object is instance of `swoole_http_server` or `swoole_websocket_server` and the swoole_server_port object hasn't setted the configuration about protocal, the swoole_server_port is setted to analyze `http` or `websocket` protocol automatically and can't be setted the custom callback funtion of event `receive`.

- 주 서버 객체가`swoole_http_server` 또는`swoole_websocket_server`의 인스턴스이고 swoole_server_port 객체가 protocal에 대한 구성을 설정하지 않은 경우 swoole_server_port는 자동으로`http` 또는`websocket` 프로토콜을 분석하도록 설정되며 설정할 수 없습니다 이벤트의 커스텀 콜백 함수`receive`.

- If the main server object is instance of `swoole_http_server` or `swoole_websocket_server` and the swoole_server_port object has setted some custom configurations, the swoole_server_port object would change to analyze TCP protocol. If you still want to set the swoole_server_port object to analyze the `Http/WebSocket` protocol, it needs to add `open_http_protocol => true` or `open_websocket_protocol => true`

- 주 서버 객체가`swoole_http_server` 또는`swoole_websocket_server` 인스턴스이고 swoole_server_port 객체가 일부 사용자 정의 구성을 설정 한 경우 swoole_server_port 객체가 TCP 프로토콜을 분석하도록 변경됩니다. `Http / WebSocket` 프로토콜을 분석하도록 swoole_server_port 객체를 설정하려면`open_http_protocol => true` 또는`open_websocket_protocol => true`를 추가해야합니다

Available Configurations for swoole_server_port object:


swoole_server_port 객체에 대해 사용 가능한 구성 :

- socket configurations, for example, backlog, TCP_KEEPALIVE, open_tcp_nodelay, tcp_defer_accept, etc

- protocol configurations, for example, open_length_check, open_eof_check, package_length_type, etc

- ssl configurations, for example, ssl_cert_file、ssl_key_file, etc

- 소켓 구성 (예 : 백 로그, TCP_KEEPALIVE, open_tcp_nodelay, tcp_defer_accept 등)

- 프로토콜 구성 (예 : open_length_check, open_eof_check, package_length_type 등)

- ssl 구성 (예 : ssl_cert_file, ssl_key_file 등)

Unavailable Configurations for swoole_server_port object:

swoole_server_port 객체에 사용할 수없는 구성 :

- worker_num, task_worker_num, reactor_num

- dispatch_mode, task_ipc_num

- heartbeart_check

- log_file

- user, group, chroot

- open_cpu_affinity

- max_request, task_max_request

#### Optional callback functions for swoole_server_port object

The swoole_server_port object can only set part of [the callback functions of swoole_server](/modules/swoole-server/callback-functions.md)

swoole_server_port 객체는 [swoole_server의 콜백 함수] (/ modules / swoole-server / callback-functions.md)의 일부만 설정할 수 있습니다.

For TCP server:

TCP 서버의 경우 :

- onConnect

- onClose

- onReceive

For UDP server:

UDP 서버의 경우 :

- onPacket

- onReceive

The below callback functions can only be setted by swoole_server object.

아래의 콜백 함수는 swoole_server 객체로만 설정할 수 있습니다.

- onStart

- onShutdown

- onWorkerStart

- onWorkerStop

- onManagerStart

- onManagerStop

- onTask

- onFinish

- onPipeMessage

- onWorkerError

#### Q&A

The `swoole_http_server` class and `swoole_websocket_server` class inherit the `swoole_server` class. The swoole_server object can't call `listen` method to create swoole_server_port object of Http or Websocket server. 

`swoole_http_server` 클래스와`swoole_websocket_server` 클래스는`swoole_server` 클래스를 상속합니다. swoole_server 객체는 Http 또는 Websocket 서버의 swoole_server_port 객체를 만들기 위해`listen` 메소드를 호출 할 수 없습니다.

In this situation, you can create the swoole_http_server object and then call `listen` method to create tcp server.

이 경우 swoole_http_server 객체를 만든 다음`listen` 메소드를 호출하여 tcp 서버를 만들 수 있습니다.

```php
$http_server=new swoole_http_server('0.0.0.0',9998); 
$http_server->set(array('xxx'=>'yyy'));
$http_server->on('request','request');
$tcp_server=$http_server->addListener('0.0.0.0',9999,SWOOLE_SOCK_TCP);
```
