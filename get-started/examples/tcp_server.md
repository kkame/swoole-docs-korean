## Create TCP Server

### Code example

`server.php`

``` php
// Create the server object and listen 127.0.0.1:9501
$server = new swoole_server("127.0.0.1", 9501);

// Register the function for the event `connect`
$server->on('connect', function($server, $fd){
    echo "Client : Connect.\n";
});

// Register the function for the event `receive`
$server->on('receive', function($server, $fd, $from_id, $data){
    $server->send($fd, "Server: " . $data);
});

// Register the function for the event `close`
$server->on('close', function($server, $fd){
    echo "Client: {$fd} close.\n";
});

// Start the server
$server->start();
```
The code above creates a TCP server, and listens the 127.0.0.1:9501. It implements a simple echo tcp server. When the client connects to this server and sends a string 'hello', the server will respond with a string 'Server: hello'.

위의 코드는 TCP 서버를 만들고 127.0.0.1:9501을 수신합니다. 그것은 간단한 echo tcp 서버를 구현합니다. 클라이언트가이 서버에 연결하고 'hello'문자열을 보내면 서버는 'Server : hello'문자열로 응답합니다.

The class `swoole_server` creates an async server by registering the events listening functions. When an event happens, the internal of swoole will call the corresponding function which is registered for this event. 

`swoole_server` 클래스는 이벤트 청취 함수를 등록함으로써 비동기 서버를 생성합니다. 이벤트가 발생하면 내부 이벤트가이 이벤트에 등록 된 해당 기능을 호출합니다.

For example, if a tcp connection comes and connects to the tcp server, the swoole will call the function which is registered for event `connect`. If a tcp client sends data to the tcp server, the swoole will recevice the data and call the corresponding function to handle this event. 

예를 들어, tcp 연결이 tcp 서버에 연결되면 swoole은 이벤트`connect`에 대해 등록 된 함수를 호출합니다. tcp 클라이언트가 tcp 서버에 데이터를 보내면 swoole은 데이터를 수신하고 해당 기능을 호출하여이 이벤트를 처리합니다.

- The server can be connected by thousands of client at the same time and `$fd` is the unique identifier of client.

- 서버는 동시에 수천 개의 클라이언트로 연결될 수 있으며 `$fd`는 클라이언트의 고유 한 식별자입니다.

- When calling `$server->send($fd, $data)` to send data to client, `$fd` stands for the client.

- `$server->send ($fd, $ data)`를 호출하여 클라이언트에게 데이터를 보낼 때, `$fd`는 클라이언트를 나타낸다.

- When calling `$server->close($fd)`, the connection between the client `$fd` and the server will be closed and the server will call the function registered for event `close`.

- `$server->close ($fd)`를 호출하면 클라이언트 `$fd`와 서버 사이의 연결이 닫히고 서버는 이벤트`close`에 대해 등록 된 함수를 호출합니다.

- When the client closes the connection proactively, the server will call the function registered for event `close`.

- 클라이언트가 연결을 사전에 닫으면 서버는 이벤트`close`에 대해 등록 된 함수를 호출합니다.

### Run program

``` bash
php server.php
```

Run the server file in command line. You can use the `netstat` to check which process is listening the 9501 port. 

명령 줄에서 서버 파일을 실행하십시오. `netstat`를 사용하여 어떤 프로세스가 9501 포트를 듣고 있는지 확인할 수 있습니다.

`sudo netstat -nlp |awk '/9501/'`

Use the `telnet` or `netcat` tool to connect the server.

`telnet` 또는`netcat` 도구를 사용하여 서버에 연결하십시오.

``` bash
telnet 127.0.0.1 9501
hello
Server: hello
```

### Q&A

#### Fail to connect the server

There are some ways to check this problem:

이 문제를 확인하는 몇 가지 방법이 있습니다.

- Run `sudo netstat -nlp | grep 9501` to check if the 9501 has been listened

-`sudo netstat -nlp | 9501이 들었는지 확인하는 grep 9501`

- If there is no problem after the above check, check the firewall of operating system.

- 위의 사항을 확인한 후에 문제가 없으면 운영체제의 방화벽을 확인하십시오.

- Pay attention to the ip address the server listens. The client should connect the same ip address

- 서버가 수신하는 IP 주소에주의하십시오. 클라이언트는 동일한 IP 주소를 연결해야합니다.
