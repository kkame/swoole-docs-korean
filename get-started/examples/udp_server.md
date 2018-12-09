## Create UDP Server

### Code example

`udp_server.php`

``` php
// Create the server object which listens at 127.0.0.1:9502. Set the server type to SWOOLE_SOCK_UDP
$server = new swoole_server("127.0.0.1", 9502, SWOOLE_PROCESS, SWOOLE_SOCK_UDP);

// Register callback function for the event `receive data`
$server->on('Packet', function($server, $data, $clientInfo){
    $server->sendto($clientInfo['address'], $clientInfo['port'], "Server : " . $data);
});

// Start the server
$server->start();
```

As UDP server, it is unlike TCP server and hasn't the concept of connection. When the UDP server has started, the client can send directly the data to the ip address and port which the server listens at. Then the UDP server will call the function registered for receiving packet.

UDP 서버로서 TCP 서버와 달리 연결의 개념이 없습니다. UDP 서버가 시작되면 클라이언트는 서버가 수신하는 IP 주소와 포트로 직접 데이터를 보낼 수 있습니다. 그러면 UDP 서버는 패킷 수신을 위해 등록 된 기능을 호출합니다.

- `$clientInfo` is the information of client. It is a array which contains the ip address and port of client.

- `$clientInfo`는 클라이언트의 정보입니다. 그것은 클라이언트의 IP 주소와 포트를 포함하는 배열입니다.

- Calling the `$server->sendto($ip, $port, $data)` to send data to client

- `$server->sendto ($ip, $ port, $ data)`를 호출하여 클라이언트에게 데이터 보내기


### Run program 

``` bash
php udp_server.php
```
You can use `netcat -u` to test.

`netcat -u`를 사용하여 테스트 할 수 있습니다.

``` bash
netcat -u 127.0.0.1 9502 
hello
Server : hello
```
