## Create Async TCP Client

### Code example

`async_tcp_client.php`

``` php
// Create the asynchronous tcp client object
$client = new swoole_client(SWOOLE_SOCK_TCP, SWOOLE_SOCK_ASYNC);

// Register the function for the event `connect`
$client->on("connect", function($client){
	$client->send("Hello World");
});

// Register the function for the event `receive`
$client->on("receive", function($client, $data){
	echo "Received :" . $data . "\n";
});

// Register the function for the event `error`
$client->on("error", function($client){
	echo "Connect failed";
});

// Register the function for the event `close`
$client->on("close", function($client){
	echo "Connection close\n";
});

// Start to connect to the server
$client->connect("127.0.0.1", 9501, 0.5);
```

This tcp client is asynchronous and non-blocking and is used for high concurrency program. The `redis-async` and `mysql-async` provided by swoole is based on this tcp client.

이 tcp 클라이언트는 비동기식이며 비 차단 형이며 높은 동시성 프로그램에 사용됩니다. swoole이 제공하는`redis-async`와`mysql-async`는이 tcp 클라이언트를 기반으로합니다.

It needs to register functions for the events. There are four events which must be registered. 

이벤트에 대한 함수를 등록해야합니다. 등록해야하는 네 가지 사건이 있습니다.

- the event of connecting which is triggered when the client connects to the server successfully
- the event of error which is triggered when the client fails to connect the server
- the event of receiving data which is triggered when the client receives data from the server
- the event of close which is triggered when the connection between the client and the server is closed

- 클라이언트가 서버에 성공적으로 연결할 때 트리거되는 연결 이벤트
- 클라이언트가 서버 연결에 실패 할 때 트리거되는 오류 이벤트
- 클라이언트가 서버로부터 데이터를 수신 할 때 트리거되는 데이터 수신 이벤트
- 클라이언트와 서버 간의 연결이 닫힐 때 트리거되는 close 이벤트


`$client->connect` returns immediately. When an event is triggered, the swoole would call the corresponding function registered for the event.

 `$client->connect`는 즉시 리턴합니다. 이벤트가 트리거되면 스풀은 이벤트에 대해 등록 된 해당 기능을 호출합니다.

### Run program

``` bash
php async_tcp_client.php
```
