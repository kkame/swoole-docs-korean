## Create Websocket Server

### Code example

`websocket_server.php`

``` php
//Create the websocket server object 
$websocket_server = new swoole_websocket_server("0.0.0.0", 9502);

// Register function of the opening connection event
$websocket_server->on('open', function($websocket_server, $request){
    var_dump($request->fd, $request->get, $request->server);
    $websocket_server->push($request->fd, "Hello welcome\n");
});

// Register function of the receiving message event
$websocket_server->on('message', function($websocket_server, $frame){
    echo "Message : {$frame->data}\n";
    $websocket_server->push($frame->fd, "Server : {$frame->data}");
});

// Register function of the close event
$websocket_server->on('close', function($websocket_server, $fd){
    echo "client_{$fd} is closed\n";
});

// Start the server
$websocket_server->start();
```

Websocket server is based on the http server. The client will first send a handshake request to start the WebSockrt handshake process. If the process of handshake successed, the swoole would call the function registered for event `open` and get the `$request` object. The `$request` object contains the information of GET, Cookie and Http headers. 

Websocket 서버는 http 서버를 기반으로합니다. 클라이언트는 먼저 WebSockrt 핸드 셰이크 프로세스를 시작하기 위해 핸드 셰이크 요청을 보냅니다. 핸드 쉐이크가 성공하면, swoole은 이벤트`open`을 위해 등록 된 함수를 호출하고 `$request` 객체를 얻습니다.  `$request` 객체는 GET, Cookie 및 Http 헤더 정보를 포함합니다.

Once the connection has been setted, the client and the server can make the interactive communication.

일단 연결이 설정되면, 클라이언트와 서버는 대화식 통신을 할 수 있습니다.

- The onMessage function will be called when the client send data to the server

- 클라이언트가 서버에 데이터를 보낼 때 onMessage 함수가 호출됩니다.

- The server uses `$websocket_server->push($fd, $data)` to send data to the client

- 서버는 `$websocket_server->push ($fd, $ data)`를 사용하여 클라이언트에게 데이터를 보낸다.

- The server is able to register the function for event `handshake` to handle the handshake

- 서버는 핸드 셰이크를 처리하기 위해 이벤트`handshake '에 대한 함수를 등록 할 수 있습니다.

### Run program

``` bash
php websocket_server.php
```

In the browser, js code is below:

브라우저에서 js 코드는 다음과 같습니다.

``` javascript
var wsServer = 'ws://127.0.0.1:9502';
var websocket = new WebSocket(wsServer);
websocket.onopen = function (evt) {
    console.log("Connected to WebSocket server.");
};

websocket.onclose = function (evt) {
    console.log("Disconnected");
};

websocket.onmessage = function (evt) {
    console.log('Retrieved data from server: ' + evt.data);
};

websocket.onerror = function (evt, e) {
    console.log('Error occured: ' + evt.data);
};

```
