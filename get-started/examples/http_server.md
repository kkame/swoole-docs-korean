## Create Web Server

### Code example 

`http_server.php`

``` php
// Create the http server object 
$http_server = new swoole_http_server("127.0.0.1", 9503);

// Register the event of request
$http_server->on('request', function($request, $response){
    var_dump($request->get, $request->post);
    $response->header("Content-Type", "text/html;charset=utf-8");
    $response->end("<h1>Hello Swoole " . rand(1000, 9999) . "</h1>");
});

// Start the server
$http_server->start();
```

For http server, the most important task is to handle the request and send the response. You can just register the function for event `request`. 

http 서버의 경우 가장 중요한 작업은 요청을 처리하고 응답을 보내는 것입니다. `request` 이벤트에 대해서만 함수를 등록 할 수 있습니다.

When the new http request comes, the server will call the function registered for request to handle. The swoole will pass two parameters, `$request` and `$response`, in the registered function. 

새 http 요청이 오면 서버는 처리 요청에 등록 된 함수를 호출합니다. swoole은 등록 된 함수에서 두 개의 매개 변수 인 `$request`와 `$response`를 전달합니다.

The parameter `$request` contains the information about the http request, for example GET/POST data.

'$ request` 매개 변수는 http 요청에 대한 정보를 포함합니다 (예 : GET / POST 데이터).

The parameter `$response` is handled by swoole to send the data to client. `$response->end($data)` will output the `$data` to the client in the form of html and  close the connection. 

 `$response` 매개 변수는 swoole에 의해 처리되어 클라이언트에 데이터를 보냅니다.  `$response->end ($data)`는 `$data`를 html 형식으로 클라이언트에 출력하고 연결을 닫습니다.

- '0.0.0.0' represents that the server listens all ip addresses.
- '9501' represents the port that the server listens at. If the port has already been used, the swoole would throw a fatal error and stop execution.

- '0.0.0.0'은 서버가 모든 IP 주소를 청취 함을 나타냅니다.
- '9501'은 서버가 청취하는 포트를 나타냅니다. 포트가 이미 사용 중이면 swoole이 치명적인 오류를 발생시키고 실행을 중지합니다.

### Run program

``` bash
php http_server.php
```

- Use the browser or run `curl http://127.0.0.1:9501` in command line to check the result of program

- 브라우저를 사용하거나 명령 줄에서`curl http : //127.0.0.1 : 9501`을 실행하여 프로그램의 결과를 확인하십시오.

- Use the tool `ab` of apache to test the performance of this http server

- 아파치의 도구`ab`를 사용하여이 http 서버의 성능을 테스트하십시오.