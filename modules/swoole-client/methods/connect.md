# Swoole TCP/UDP client

## Methods 

### swoole_client->connect

#### Prototype

```php
bool swoole_client->connect(string $host, int $port, float $timeout = 0.1, int $flag = 0)
```

#### Illustration

Connect to the remote TCP/UDP port.

원격 TCP / UDP 포트에 연결하십시오.

#### Parameter

* `$host`	  the ip address the client connects to
* `$port`     the port the client connects to
* `$timeout`  the timeout(second) of connect/send/recv, the dafault value is 0.1s
* `$flag`     if the type of client is UDP, the `$flag` means if to enable the configuration `udp_connect`. If the configuration `udp_connect` is enabled, the client will only receive the data from specified `ip:port`. If the type of client is TCP and the `$flag` is setted to `1`, it must use `swoole_client_select` to check the connection status before `send/recv`.  

* `$host` 클라이언트가 접속하는 IP 주소
* `$port` 클라이언트가 연결하는 포트
* `$timeout`은 connect / send / recv의 타임 아웃 (초)이고, dafault 값은 0.1 초입니다
클라이언트의 타입이 UDP라면`$flag`,`$flag`는`udp_connect` 설정을 가능하게하는 것을 의미합니다. 설정`udp_connect`가 활성화되면, 클라이언트는 지정된`ip : port`에서 데이터를 수신합니다. 클라이언트 유형이 TCP이고`$flag`가`1`로 설정되어 있다면`send / recv '전에 연결 상태를 검사하기 위해`swoole_client_select'를 사용해야합니다.

> `$timeout` is noneffective for asynchronous client.

> `$timeout`은 비동기 클라이언트에서는 유효하지 않습니다.

#### Return

##### Synchronous mode

This method won't return until the client connects to the server successfully or unsuccessfully.

이 메서드는 클라이언트가 서버에 성공적으로 또는 성공적으로 연결할 때까지 반환되지 않습니다.

```php
if ($cli->connect('127.0.0.1', 9501)) {
    $cli->send("data");
} else {
    echo "connect failed.";
}
```

##### Asynchronous mode


#### Example

```php
<?php
if ($cli->connect('127.0.0.1', 9501)) {
      $cli->send("data");
} else {
      echo "connect failed.";
}
```
