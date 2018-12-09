### swoole_server->sendto

#### Prototype

```php
bool swoole_server->sendto(string $ip, int $port, string $data, int $server_socket = -1)
```

#### Illustration

Send data to the remote UDP address.

원격 UDP 주소로 데이터를 보냅니다.

> To use `swoole_server->sendto`, the swoole server has to listen the port of UDP
> To use `swoole_server->sendto` to send data to IPV6, the swoole server has to listen the port of UDP6

>`swoole_server-> sendto`를 사용하려면, swoole 서버는 UDP 포트를 청취해야합니다
>`swoole_server-> sendto`를 사용하여 IPV6에 데이터를 보내려면 스풀 서버가 UDP6의 포트를 청취해야합니다

#### Parameter

* `$ip`	the string of ip address
* `$port` the integer of port
* `$data` the data to send
* `$server_socket` the swoole server may listen multiple port at the same time, use `$server_socket` to assign the port to use

*`$ ip`는 IP 주소 문자열입니다.
*`$ port`는 포트의 정수입니다.
*`$ data`는 보낼 데이터입니다.
*`$ server_socket` 스풀 서버는 동시에 여러 개의 포트를들을 수 있습니다.`$ server_socket`을 사용하여 사용할 포트를 지정하십시오

#### Return

the result of send data

데이터 전송 결과

#### Example

```php
<?php
$server->sendto('220.181.57.216', 9502, "hello world");

$server->sendto('2600:3c00::f03c:91ff:fe73:e98f', 9501, "hello world");
```
