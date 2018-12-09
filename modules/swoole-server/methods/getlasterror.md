### swoole_server->getLastError()

#### Prototype

```php
int swoole_server->getLastError()
```

#### Illustration

Get the error code of the most recent error.

가장 최근 오류의 오류 코드를 가져옵니다.

#### Parameter

void

#### Return

the error code

Error codes:
* 1001: The connection has been closed by the server.
* 1002: The connection has been closed by the client side.
* 1003: The connection is closing.
* 1004: The connection is closed.
* 1005: Error $fd.
* 1007: Received data after connection has been closed.
* 1008: The send buffer is full.

오류 코드

오류 코드 :
* 1001 : 연결이 서버에 의해 닫혔습니다.
* 1002 : 연결이 클라이언트 측에 의해 닫혔습니다.
* 1003 : 연결이 닫힙니다.
* 1004 : 연결이 닫혔습니다.
* 1005 : 오류 $ fd.
* 1007 : 연결이 닫힌 후 데이터가 수신되었습니다.
* 1008 : 송신 버퍼가 가득 찼습니다.

#### Example
