## Create Sync TCP Client

### Code example

`sync_tcp_client.php`

``` php
// Create the tcp client
$client = new swoole_client(SWOOLE_SOCK_TCP);

// Connect to the tcp server
if(!$client->connect('127.0.0.1', 9501, 0.5))
{
    die("connect failed");
}

// Send data to the tcp server
if(!$client->send("Hello World"))
{
    die("send failed");
}

// Receive data from the tcp server
$data = $client->recv();
if(!$data)
{
    die("recv failed");
}
echo $data;

// Close the connection
$client->close();
```

The code above creates a synchronous TCP client. This client can be used to connect the tcp server we have created in the previous example. When the client send a string 'Hello World' to the server, the server would respond with a string 'Server: Hello World'.

위의 코드는 동기 TCP 클라이언트를 만듭니다. 이 클라이언트는 앞의 예제에서 만든 tcp 서버에 연결하는 데 사용할 수 있습니다. 클라이언트가 문자열 'Hello World'를 서버에 보내면 서버는 문자열 'Server : Hello World'로 응답합니다.

This client is synchronous and blocking. The operations, like connect, send and recv, don't return until the IO operation completes. The synchronous and blocking operation doesn't consume CPU resource and switch to `sleep` mode automatically before the IO completes. When the IO operation completes, the system will awake the process and continue to execute.

이 클라이언트는 동기적이고 블로킹입니다. connect, send 및 recv와 같은 작업은 IO 작업이 완료 될 때까지 반환되지 않습니다. 동기 및 차단 작업은 CPU 리소스를 소비하지 않고 IO가 완료되기 전에 자동으로 '절전 모드'로 전환됩니다. 입출력 작업이 완료되면 시스템은 프로세스를 깨우고 계속 실행합니다.

- If the operation of connecting server needs 100ms, `$client->connect` will block and cost 100ms.

- 접속 서버의 동작이 100ms 필요하면 `$client->connect`가 차단되어 100ms가 소요됩니다.

- `$client->send` can return immediately when to send small data. But it could be blocked when to send large data because the data could fill in the socket send buffer.

- `$client->send`는 작은 데이터를 보낼 때 즉시 반환 할 수 있습니다. 그러나 데이터가 소켓 보내기 버퍼를 채울 수 있으므로 대용량 데이터를 보낼 때 차단 될 수 있습니다.

- `$client->recv` blocks to wait the return data of the server. The elapsed time equals to the sum of the time for procees data in server and the time for tranporting data

- `$client->recv` 블록은 서버의 리턴 데이터를 기다린다. 경과 시간은 서버에있는 procees 데이터의 시간과 데이터 전송을위한 시간의 합계와 같습니다

### Run program

``` bash
php sync_tcp_client.php
```
