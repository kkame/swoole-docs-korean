# Swoole Async HTTP2 client

Http2.0 client support stream and multiplexing. Multiple GET or POST request can be sent over the same TCP connection.

Http2.0 클라이언트 지원 스트림 및 멀티플렉싱. 여러 개의 GET 또는 POST 요청은 동일한 TCP 연결을 통해 이루어질 수 있습니다.

Swoole HTTP2 client is based on *nghttp2*, enable this feature when compiling with *--enable-nghttp2*, *--enable-openssl* or *--with-openssl-dir*.

Swoole HTTP2 클라이언트는 * nghttp2 *를 기반으로 * - enable-nghttp2 *, * - enable-openssl * 또는 * - with openssl-dir *을 사용하여 컴파일 할 때이 기능을 활성화합니다.

## Example

```php
<?php
$array = array(
    "host" => "www.google.com",
    "accept-encoding" => "gzip, deflate",
    'accept' => 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8',
    'accept-language' => 'zh-CN,zh;q=0.8,en;q=0.6,zh-TW;q=0.4,ja;q=0.2',
    'user-agent' => 'Mozilla/5.0 (X11; Linux x86_64) Chrome/58.0.3026.3 Safari/537.36',
);

$client = new Swoole\Http2\Client("www.google.com", 443, true);

$client->setHeaders($array);
$client->setCookies(array("a" => "1", "b" => "2"));

$client->get("/", function ($o) use($client) {
    echo "#{$client->sock} hello world 1\n";
    echo $o->body;
});

$client->post("/", $array, function ($o) use($client) {
    echo "{$client->sock} hello world 3\n";
    echo $o->body;
    $client->close();
});
Swoole\Event::wait();
```

### Events

### Methods

#### function swoole_http2_client->__construct($host, $port, $ssl = false)

Construct HTTP2 client.

HTTP2 클라이언트를 구성합니다.

#### function swoole_http_client->get(string $path, callable $callback);

Send *GET* request, example callback function:

* GET * 요청, 예제 콜백 함수 보내기 :

```php
<?php
function callback(Swoole\Http2\Response $resp)
{
    var_dump($resp->cookie);
    var_dump($resp->header);
    var_dump($resp->server);
    var_dump($resp->body);
    var_dump($resp->statusCode);
}
```

#### function swoole_http2_client->post(string $path, mixed $data, callable $callback);

Send *POST* request, example:

* POST * 요청 보내기, 예 :

```php
<?php
$cli = new swoole_http2_client('127.0.0.1', 80); 
$cli->post('/post.php', array("a" => '1234', 'b' => '456'), function ($response) {
    echo "Length: " . strlen($cli->body) . "\n";
    echo $cli->body;
});
```

#### function swoole_http2_client->setHeaders(array $headers);

Setup the http request headers.

http 요청 헤더를 설정합니다.

#### function swoole_http2_client->setCookies(array $cookies);

Setup the http request cookies.

http 요청 쿠키를 설정하십시오.





