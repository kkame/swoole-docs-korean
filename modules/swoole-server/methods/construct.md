### swoole_server::__construct 

#### Prototype

```php
swoole_server::__construct(string $host, int $port = 0, int $mode = SWOOLE_PROCESS, int $sock_type = SWOOLE_SOCK_TCP);
```
#### Illustration

Construct a swoole server object

스풀 서버 객체 생성

#### Parameter

* `$host`: the ip address of the server
* `$port`: the port of the server (it needs root privileges if the port is litte than 1024)
* `$mode`: the running mode of the server:
    * SWOOLE_PROCESS: multiple process mode, the business logic is running in child processes, the default running mode of server
    * SWOOLE_BASE: reactor based mode, the business logic is running in the reactor
* `$sock_type`: the socket type of the server:
    * SWOOLE_SOCK_TCP: TCP
    * SWOOLE_SOCK_TCP6: TCP IPv6
    * SWOOLE_SOCK_UDP: UDP
    * SWOOLE_SOCK_UDP6: UDP IPv6
    * SWOOLE_UNIX_DGRAM: Unix socket dgram
    * SWOOLE_UNIX_STREAM: Unix socket stream
* Enable SSL: `$sock_type | SWOOLE_SSL`. To enable ssl, it must set [the configuration about ssl](/modules/swoole-server/configuration.md).

*`$ host` : 서버의 IP 주소
*`$ port` : 서버의 포트 (포트가 1024보다 작 으면 루트 권한이 필요합니다)
*`$ mode` : 서버의 실행 모드 :
     * SWOOLE_PROCESS : 다중 프로세스 모드, 비즈니스 로직은 하위 프로세스에서 실행 중이며 서버의 기본 실행 모드입니다.
     * SWOOLE_BASE : 원자로 기반 모드, 비즈니스 로직이 원자로에서 실행 중임
*`$ sock_type` : 서버의 소켓 유형 :
     * SWOOLE_SOCK_TCP : TCP
     * SWOOLE_SOCK_TCP6 : TCP IPv6
     * SWOOLE_SOCK_UDP : UDP
     * SWOOLE_SOCK_UDP6 : UDP IPv6
     * SWOOLE_UNIX_DGRAM : 유닉스 소켓 dgram
     * SWOOLE_UNIX_STREAM : 유닉스 소켓 스트림
SSL 사용 :`$ sock_type | SWOOLE_SSL`. ssl을 활성화하려면 [ssl에 대한 구성] (/ modules / swoole-server / configuration.md)을 설정해야합니다.

#### Return

the swoole_server object

swoole_server 객체

#### Example:

##### Listen on a random port:

The swoole supports the feature of listening on a random port. When the argument `$port` isn't seted or is `0`, the swoole will choose a random and available port to listen on. You can use `$server->port` to listen on. 

스풀은 임의의 포트에서 수신하는 기능을 지원합니다. 인수`$ port`가 설정되어 있지 않거나 '0'이면, swoole은 무작위로 사용할 수있는 포트를 선택합니다. `$ server-> port`를 사용하여들을 수 있습니다.

```php
<?php
$http = new swoole_http_server("127.0.0.1");

$http->on('request', function ($request, $response) {
    $response->header("Content-Type", "text/html; charset=utf-8");
    $response->end("<h1>Hello Swoole. #".rand(1000, 9999)."</h1>");
});

$http->start();
```
##### Listen on a port defined in systemd

The swoole-1.9.7 adds the support for `systemd socket`. The port listened on can be setted by the configuration of systemd.

swoole-1.9.7은`systemd socket '에 대한 지원을 추가합니다. 시스템의 구성에 따라 수신 대기 포트를 설정할 수 있습니다.

`swoole.socket`
```bash
[Unit]
Description=Swoole Socket

[Socket]
ListenStream=9501
Accept=false
[Install]
WantedBy = sockets.target
```

`swoole.service`
```bash
[Service]
Type=forking
PIDFile=/var/run/swoole.pid
ExecStart=/usr/bin/php /var/www/swoole/server.php
ExecStop=/bin/kill $MAINPID
ExecReload=/bin/kill -USR1 $MAINPID

[Install]
WantedBy = multi-user.target
```

`server.php`
```php
$http = new swoole_http_server("systemd");

$http->set([
    'daemonize' => true,
    'pid_file' => '/var/run/swoole.pid',
]);

$http->on('request', function ($request, $response) {
    $response->header("Content-Type", "text/html; charset=utf-8");
    $response->end("<h1>Hello Swoole. #".rand(1000, 9999)."</h1>");
});

$http->start();
```

`Start the systemd service`

```bash
sudo systemctl enable swoole.socket
sudo systemctl start swoole.socket
sudo systemctl start swoole.service
```
