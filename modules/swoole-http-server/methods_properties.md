

### Methods And Properties List

#### swoole_http_server

The `swoole_http_server` class inherits from the class `swoole_server`. It is a complete implementation of http server. It supports asynchronous and synchronous mode.

`swoole_http_server` 클래스는`swoole_server` 클래스에서 상속받습니다. 이것은 http 서버의 완전한 구현입니다. 비동기 및 동기 모드를 지원합니다.

The swoole http server can hold a mass of connections in asynchronous or synchronous mode. 

스풀 http 서 v는 비동기 또는 동기 모드로 대량의 연결을 보유 할 수 있습니다.

##### Properties

- [swoole_http_server->on(string $event, $callback)](/modules/swoole-http-server/method/swoole-http-server/on.md)

- [swoole_http_server->start()](/modules/swoole-http-server/method/swoole-http-server/start.md)

#### swoole_http_request

The object of `swoole_http_request` class contains the information of request, for example, GET, POST, etc.

`swoole_http_request` 클래스의 객체는 GET, POST 등과 같은 요청 정보를 포함합니다.

##### Properties

- [swoole_http_request->$header](/modules/swoole-http-server/property/swoole-http-request/header.md)

- [swoole_http_request->$server](/modules/swoole-http-server/property/swoole_http_request/server.md)

- [swoole_http_request->$get](/modules/swoole-http-server/property/swoole_http_request/get.md)

- [swoole_http_request->$post](/modules/swoole-http-server/property/swoole_http_request/post.md)

- [swoole_http_request->$cookie](/modules/swoole-http-server/property/swoole_http_request/cookie.md)

- [swoole_http_request->$files](/modules/swoole-http-server/property/swoole_http_request/files.md)

##### Methods

- [swoole_http_request->rawContent()](/modules/swoole-http-server/method/swoole_http_request/rawcontent.md)

#### swoole_http_response

##### Methods

- [swoole_http_response->header()](/modules/swoole-http-server/method/swoole-http-response/header.md)

- [swoole_http_response->cookie()](/modules/swoole-http-server/method/swoole-http-response/cookie.md)

- [swoole_http_response->status()](/modules/swoole-http-server/method/swoole-http-response/status.md)

- [swoole_http_response->gzip()](/modules/swoole-http-server/method/swoole-http-response/gzip.md)

- [swoole_http_response->write()](/modules/swoole-http-server/method/swoole-http-response/write.md)

- [swoole_http_response->sendfile()](/modules/swoole-http-server/method/swoole-http-response/sendfile.md)

- [swoole_http_response->end()](/modules/swoole-http-server/method/swoole-http-response/end.md)
