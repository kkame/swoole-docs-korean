# Swoole TCP/UDP client

## Methods 

### swoole_client->enableSSL

#### Prototype

```php
bool swoole_client->enableSSL(mixed $var);
```

#### Illustration

If the client hasn't enabled the SSL in the construction and has connnected to the server, you can enable the SSL for the TCP client by this method.

클라이언트가 구성 중에 SSL을 활성화하지 않았고 서버에 연결되어 있으면이 방법으로 TCP 클라이언트에 대해 SSL을 활성화 할 수 있습니다.

#### Parameter

For sync TCP client, it should not pass parameter to this method and this method wouldn't return until the process of enabling SSL finished.

Sync TCP 클라이언트의 경우,이 메소드에 매개 변수를 전달해서는 안되며이 메소드는 SSL 사용 프로세스가 완료 될 때까지 리턴하지 않습니다.

For async TCP client, it should pass the callback function which is called after the process of enabling SSL finished. 

비동기 TCP 클라이언트의 경우, SSL 종료 프로세스가 완료된 후에 호출되는 콜백 함수를 전달해야합니다.

#### Return

bool

#### Example

Sync TCP client with SSL:

TCP 클라이언트와 SSL 동기화 :

```php
<?php
$client = new swoole_client(SWOOLE_SOCK_TCP);
if (!$client->connect('127.0.0.1', 9501, -1))
{
    exit("connect failed. Error: {$client->errCode}\n");
}
$client->send("hello world\n");
echo $client->recv();

if ($client->enableSSL())
{
    $client->send("hello world\n");
    echo $client->recv();
}
$client->close();
```

Async TCP client with SSL:

SSL을 사용하는 비동기 TCP 클라이언트 :

```php
<?php
$client = new swoole_client(SWOOLE_SOCK_TCP, SWOOLE_SOCK_ASYNC);
$client->on("connect", function(swoole_client $cli) {
    $cli->send("hello world\n");
});
$client->on("receive", function(swoole_client $cli, $data) {
    echo "Receive: $data";
    $cli->send(str_repeat('A', 10)."\n");

    $cli->enableSSL(function($client) { 
        $client->send("hello");
    })
});
$client->on("error", function(swoole_client $cli){
    echo "error\n";
});
$client->on("close", function(swoole_client $cli){
    echo "Connection close\n";
});
$client->connect('127.0.0.1', 9501);
```
