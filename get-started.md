# Get started

The swoole is released as a PHP extension \(PECL\) and run as a PHP CLI application.

swoole은 PHP 확장자 \(PECL\)로 배포되고 PHP CLI 어플리케이션으로 실행됩니다.

### Installation

Please check the [preparation](/get-started/preparation.md) and [installation guide](/get-started/installation.md).

[사전준비](/get-started/preparation.md) 및 [설치 안내서](/get-started/installation.md)를 확인하십시오.

### Hello world

An example of a web server written with Swoole which responds 'Hello World':

Swoole로 작성된 'Hello World'로 응답하는 웹 서버의 예 :

```php
<?php
$http = new swoole_http_server("127.0.0.1", 9501);

$http->on('start', function ($server) {
    echo "Swoole http server is started at http://127.0.0.1:9501\n";
});

$http->on('request', function ($request, $response) {
    $response->header("Content-Type", "text/plain");
    $response->end("Hello World\n");
});

$http->start();
```

To run the server, put the code into a file named server.php and execute it in the cli mode of php:

서버를 실행하려면 코드를 `server.php`라는 파일에 넣고 PHP의 cli 모드로 실행합니다:

```bash
$ php server.php
$ curl http://127.0.0.1:9501/
```



