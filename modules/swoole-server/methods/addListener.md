### swoole_server->addListener

#### Prototype

```php
mixed swoole_server->addListener(string $host, int $port, $type = SWOOLE_SOCK_TCP);
```

#### Illustration

Add more listening IP or port for the server. The connection information can be acccessed by `$server->connection_info()` when the server has started. By the connection information, you can distinguish the source port of the connection. 

서버에 청취 IP 또는 포트를 추가하십시오. 연결 정보는 서버가 시작될 때`$ server-> connection_info ()`에 의해 접근 될 수있다. 연결 정보를 통해 연결의 소스 포트를 구별 할 수 있습니다.

#### Parameter

* `$host`: the ip address of the server
* `$port`: the port of the server 
    - it needs root privileges if the port is litte than 1024
    - the parameter `$port` will be ignored when the parameter `$sock_type` is setted to `SWOOLE_UNIX_DGRAM` or `SWOOLE_UNIX_STREAM`
    - if the parameter `$port` is setted to `0`, the swoole server would use a random and available port

*`$ host` : 서버의 IP 주소
*`$ port` : 서버의 포트
     - 포트가 1024보다 작 으면 루트 권한이 필요합니다.
     -`$ sock_type` 매개 변수가`SWOOLE_UNIX_DGRAM` 또는`SWOOLE_UNIX_STREAM`으로 설정되면 매개 변수`$ port`는 무시됩니다
     - 매개 변수 '$ port'가 '0'으로 설정되면, 스풀 서버는 임의의 사용 가능한 포트를 사용합니다

* `$sock_type`: the socket type of the server:
    * SWOOLE_SOCK_TCP: TCP
    * SWOOLE_SOCK_TCP6: TCP IPv6
    * SWOOLE_SOCK_UDP: UDP
    * SWOOLE_SOCK_UDP6: UDP IPv6
    * SWOOLE_UNIX_DGRAM: Unix socket dgram
    * SWOOLE_UNIX_STREAM: Unix socket stream
* Enable SSL: `$sock_type | SWOOLE_SSL`. To enable ssl, it must set [the configuration about ssl](/modules/swoole-server/configuration.md).

*`$ sock_type` : 서버의 소켓 유형 :
     * SWOOLE_SOCK_TCP : TCP
     * SWOOLE_SOCK_TCP6 : TCP IPv6
     * SWOOLE_SOCK_UDP : UDP
     * SWOOLE_SOCK_UDP6 : UDP IPv6
     * SWOOLE_UNIX_DGRAM : 유닉스 소켓 dgram
     * SWOOLE_UNIX_STREAM : 유닉스 소켓 스트림
SSL 사용 :`$ sock_type | SWOOLE_SSL`. ssl을 활성화하려면 [ssl에 대한 구성] (/ modules / swoole-server / configuration.md)을 설정해야합니다.

#### Return

The swoole_server_port object

swoole_server_port 객체

#### Example

```php
<?php
$server->addlistener("127.0.0.1", 9502, SWOOLE_SOCK_TCP);
$server->addlistener("192.168.1.100", 9503, SWOOLE_SOCK_TCP);
$server->addlistener("0.0.0.0", 9504, SWOOLE_SOCK_UDP);
//UnixSocket Stream
$server->addlistener("/var/run/myserv.sock", 0, SWOOLE_UNIX_STREAM);
//TCP + SSL
$server->addlistener("127.0.0.1", 9502, SWOOLE_SOCK_TCP | SWOOLE_SSL); 
//Listen on a random port
$port = $server->addListener("0.0.0.0", 0, SWOOLE_SOCK_TCP);
echo $port->port;
```
