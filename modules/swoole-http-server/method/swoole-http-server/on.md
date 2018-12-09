

### swoole_http_server->on

#### Prototype

```php
swoole_http_server->on(string $event, $callback)
```

#### Illustration

Register the callback function for the event.

이벤트에 대한 콜백 함수를 등록하십시오.

The `swoole_http_server` class inherits from the class `swoole_server`. The `on` method has something different from the `on` method of class `swoole_server`.

`swoole_http_server` 클래스는`swoole_server` 클래스에서 상속받습니다. `on` 메소드는`swoole_server` 클래스의`on` 메소드와 다른 점이 있습니다.

- Don't support the event `connect` and `receive`

- Add new event `request`. This event happens when the process receives a complete http request.

-`connect`와`receive` 이벤트를 지원하지 않습니다.

- 새로운 이벤트`request`를 추가하십시오. 이 이벤트는 프로세스가 완전한 http 요청을 수신 할 때 발생합니다.

#### Example

```php
$http_server->on('request', function(swoole_http_request $request, swoole_http_response $response) {
     $response->end("<h1>hello swoole</h1>");
})
```
When the process receives a complete http request, it will call the callback function registered for this event.

프로세스가 완전한 http 요청을 받으면이 이벤트에 대해 등록 된 콜백 함수를 호출합니다.

- `$request` the object of class `swoole_http_request`

- `$response` the object of class `swoole_http_response`

- If the callback function hasn't called the `$response->end` function, the swoole will add the call of `$response->end("")` at the end automatically.

-`$ request` 클래스의 객체`swoole_http_request`

-`$ 응답`클래스의 객체`swoole_http_response`

- 콜백 함수가`$ response-> end` 함수를 호출하지 않으면, swoole은 자동적으로`$ response-> end ( "")`호출을 끝에 추가 할 것이다.