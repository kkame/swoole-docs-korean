

### swoole_http_response->end

#### Prototype

```php
swoole_http_response->end(string $html)
```

#### Illustration

Send data for the HTTP request and end the response.

HTTP 요청에 대한 데이터를 보내고 응답을 종료합니다.

#### Parameter

- `$html` the data to send to the client

-`$ html`은 클라이언트에게 보낼 데이터입니다.

> The call of `$response->end` can only be once.

>`$ response-> end`의 호출은 한 번만 가능합니다.

> If the client enables the configuration of keepalive, the connection between the server and the client will maintain.

> 클라이언트가 킵 얼라이브 구성을 활성화하면 서버와 클라이언트 간의 연결이 유지됩니다.

> If the client doesn't enable the configuration of keepalive, the connection between the server and the client will be closed.

> 클라이언트가 킵 얼라이브 구성을 활성화하지 않으면 서버와 클라이언트 간의 연결이 닫힙니다.