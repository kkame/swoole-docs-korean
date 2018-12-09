# Swoole Async HTTP/Websocket client

Swoole Async HTTP client is a high performance and aync HTTP client supports Http-Chun, Keep-Alive, form-data.

Swoole Async HTTP 클라이언트는 고성능이며 aync HTTP 클라이언트는 Http-Chun, Keep-Alive, form-data를 지원합니다.

### Events

* connect
* message
* close
* error

### Methods

#### swoole_http_client::__construct(string $host, int port, bool $ssl = false);

Example:

예제:

```php
<?php
Swoole\Async::dnsLookup("www.google.com", function ($domainName, $ip) {
    $cli = new swoole_http_client($ip, 80);
    $cli->setHeaders([
        'Host' => $domainName,
        "User-Agent" => 'Chrome/49.0.2587.3',
        'Accept' => 'text/html,application/xhtml+xml,application/xml',
        'Accept-Encoding' => 'gzip',
    ]);
    $cli->get('/index.html', function ($cli) {
        echo "Length: " . strlen($cli->body) . "\n";
        echo $cli->body;
    });
});
```

#### swoole_http_client->set(array $setting);

Set the parameters for the http client.

http 클라이언트의 매개 변수를 설정하십시오.

Example:

예제:

```php
<?php
// Set the connect timeout
$http->set(['timeout' => 3.0]);
// Set the keep alive option
$http->set(['keep_alive' => false]);
// Set websocket mask
$http->set(['websocket_mask' => true]);
```

#### swoole_http_client->setMethod(string $method);

Set the http request method.

http 요청 메소드를 설정하십시오.

Example:

예제:

```php
<?php
$client->setMethod("PUT");
```

#### swoole_http_client->setHeaders(array $headers);

Set the http request headers.

http 요청 헤더를 설정하십시오.

#### swoole_http_client->setCookies(array $cookies);

Set the http request cookies.

http 요청 쿠키를 설정하십시오.

#### swoole_http_client->setData(string $data);

Set the http request body data. The http method will be changed to be *POST*.

http 요청 본문 데이터를 설정하십시오. http 메소드는 * POST *로 변경됩니다.

#### swoole_http_client->addFile(string $path, string $name, string $filename = null, string $mimeType = null, int $offset = 0, int $length)

Add files to the post form.

게시물 양식에 파일을 추가하십시오.

Example:

예제:

```php
<?php

<?php
$cli = new swoole_http_client('127.0.0.1', 80);
//post request
$cli->setHeaders(['User-Agent' => "swoole"]);
$cli->addFile(__DIR__.'/post.data', 'post');
$cli->addFile(dirname(__DIR__).'/test.jpg', 'debug');
$cli->post('/dump2.php', array("xxx" => 'abc', 'x2' => 'rango'), function ($cli) {
    echo $cli->body;
});
```

#### swoole_http_client->on(string $event, $callback);

Register callback function by event name.

이벤트 이름으로 콜백 함수를 등록하십시오.

#### swoole_http_client->get(string $path, callable $callback);

Send *GET* http request to the remote server.

원격 서버에 * GET * http 요청을 보냅니다.

Example:

예제:

```php
<?php

$cli = new swoole_http_client('127.0.0.1', 80);

$cli->setHeaders([
    'Host' => "localhost",
    "User-Agent" => 'Chrome/49.0.2587.3',
    'Accept' => 'text/html,application/xhtml+xml,application/xml',
    'Accept-Encoding' => 'gzip',
]);

$cli->get('/index.php', function ($cli) {
    echo "Length: " . strlen($cli->body) . "\n";
    echo $cli->body;
});
```

#### swoole_http_client->post(string $path, mixed $data, callable $callback);

Send *POST* http request to the remote server.

원격 서버에 * POST * http 요청을 보냅니다.

Example:

예제:
```php
<?php

$cli = new swoole_http_client('127.0.0.1', 80); 
$cli->post('/post.php', array("a" => '1234', 'b' => '456'), function ($cli) {
    echo "Length: " . strlen($cli->body) . "\n";
    echo $cli->body;
});
```

#### swoole_http_client->upgrade(string $path, callable $callback);

Upgrade to websocket protocol.

웹 소켓 프로토콜로 업그레이드하십시오.

```php
<?php
$cli = new swoole_http_client('127.0.0.1', 9501);

$cli->on('message', function ($_cli, $frame) {
    var_dump($frame);
});

$cli->upgrade('/', function ($cli) {
    echo $cli->body;
    $cli->push("hello world");
});
// Websocket callback function
function onMessage(swoole_http_client $client, swoole_websocket_frame $frame);
```

#### swoole_http_client->execute(string $path, callable $callback);

Send the http request after setup the parameters.

매개 변수를 설정 한 후 http 요청을 보냅니다.

#### swoole_http_client->download(string $path, string $filename, callable $callback, int $offset = 0);

Download file from the remote server.

원격 서버에서 파일을 다운로드하십시오.

Example:

예제:
```php
<?php

$cli = new swoole_http_client('127.0.0.1', 80);

$cli->setHeaders([
    'Host' => "localhost",
    "User-Agent" => 'Chrome/49.0.2587.3',
    'Accept' => '*',
    'Accept-Encoding' => 'gzip',
]);

$cli->download('/video.avi', __DIR__.'/video.avi', function ($cli) {
    var_dump($cli->downloadFile);
});

// download by range
$cli = new swoole_http_client('127.0.0.1', 80);
$file = __DIR__.'/video.avi';
$offset = filesize($file);
$cli->setHeaders([
    'Host' => "localhost",
    "User-Agent" => 'Chrome/49.0.2587.3',
    'Accept' => '*',
    'Accept-Encoding' => 'gzip',
    'Range' => "bytes=$offset-",
]);

$cli->download('/video.avi', $file, function ($cli) {
    var_dump($cli->downloadFile);
}, $offset);
```

#### swoole_http_client->push($data, $opcode, $fin);

Push data to websocket client.

웹 소켓 클라이언트에 데이터를 푸시합니다.

#### swoole_http_client->isConnected();

Check if the http connection is connected.

http 연결이 연결되어 있는지 확인하십시오.

#### swoole_http_client->close();

Close the http connection.

http 연결을 닫으십시오.
