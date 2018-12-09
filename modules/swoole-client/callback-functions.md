# Swoole TCP/UDP client

## Events and Callback-functions List

There is no connect and close connection event for UDP. If you have setted the callback function for event `connect`, it will be called immediately after the UDP client is created.

UDP에 대한 연결 및 닫기 연결 이벤트는 없습니다. 이벤트`connect`에 대한 콜백 함수를 설정했다면, UDP 클라이언트가 생성 된 직후에 호출됩니다.

If you have setted the callback function for event `close`, it will be called immediately after the UDP client is closed.

이벤트`close`에 대한 콜백 함수를 설정했다면, UDP 클라이언트가 닫힌 직후 호출됩니다.

### Table of Contents

- onConnect
- onError
- onReceive
- onClose
- onBufferFull
- onBufferEmpty

#### onConnect

`connect` event happens when the client connect to the server successfully.

`connect` 이벤트는 클라이언트가 서버에 성공적으로 연결할 때 발생합니다.

```php
function onConnect(swoole_client $client)
```

> For TCP client, it must set the callback function for event `connect`. 

> TCP 클라이언트의 경우, 이벤트`connect`에 대한 콜백 함수를 설정해야합니다.

> For UDP client, it is optional to set the callback function for event `connect`.

> UDP 클라이언트의 경우 이벤트`connect`에 대한 콜백 함수를 설정하는 것은 선택 사항입니다.

#### onError

`error` event happens when the client fails to connect to the server.

`error` 이벤트는 클라이언트가 서버에 연결하지 못할 때 발생합니다.

```php
function onError(swoole_client $client)
```

> For UDP client, there is no event `error`.

> UDP 클라이언트의 경우 `error` 이벤트가 없습니다.

#### onReceive

The `receive` event happens when the client receive the data from the server.

`receive` 이벤트는 클라이언트가 서버로부터 데이터를받을 때 발생합니다.

```php
function onReceive(swoole_client $client, string $data)
```
- `$data` data received from the server.

- 서버로부터받은`$ data` 데이터.

> If the client has setted the configuration about `eof/length` check, the data received would be a whole packet.

> 클라이언트가`eof / length` 체크에 관한 설정을하면, 수신 된 데이터는 전체 패킷이됩니다.

#### onClose

The `close` event happens when the connection between the client and server is closed. 

`close` 이벤트는 클라이언트와 서버 사이의 연결이 닫힐 때 발생합니다.

```php
function onClose(swoole_client $client)
```

> The `close` event is triggered when the connection is closed by either the server or the client.

>`close` 이벤트는 서버 또는 클라이언트에 의해 연결이 닫힐 때 트리거됩니다.

#### onBufferFull

The `bufferfull` event happens when the buffer reaches the `buffer_high_watermark` which is setted by `$client->buffer_high_watermark`. If the buffer is full, it can't send data to the server anymore.

`bufferfull` 이벤트는 버퍼가`$ client-> buffer_high_watermark`에 의해 설정된`buffer_high_watermark`에 도달 할 때 발생합니다. 버퍼가 가득 차면 더 이상 서버에 데이터를 보낼 수 없습니다.

```php
function onBufferFull(Swoole\Client $cli);
```
#### onBufferEmpty

The `bufferempty` event happens when the buffer reaches the `buffer_low_watermark` which is setted by `$client->buffer_low_watermark`. If the buffer is empty, it can continue to send data to the server.

`bufferempty` 이벤트는 버퍼가`$ client-> buffer_low_watermark`에 의해 설정된`buffer_low_watermark`에 도달 할 때 발생합니다. 버퍼가 비어 있으면 서버로 데이터를 계속 보낼 수 있습니다.

```php
function onBufferEmpty(Swoole\Client $cli);
```
