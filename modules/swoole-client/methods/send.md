# Swoole TCP/UDP client

## Methods 

### swoole_client->send

#### Prototype

```php
int swoole_client->send(string $data);
```

#### Illustration

Send data to the remote TCP socket.

데이터를 원격 TCP 소켓으로 보냅니다.

#### Parameter

- `$data` the data to send which can be text or binary

-`$ data`는 보낼 데이터로, 텍스트 또는 바이너리 일 수 있습니다.

#### Return

If the client sends data successfully, it returns the length of data sent. Or it returns `false` and sets `$swoole_client->errCode`.

클라이언트가 데이터를 성공적으로 보내면 전송 된 데이터의 길이를 반환합니다. 아니면`false`를 반환하고`$ swoole_client-> errCode`를 설정합니다.

> For sync client, there is no limit for the data to send. 

> 동기화 클라이언트의 경우 전송할 데이터에는 제한이 없습니다.

> For async client, The limit for the data to send is `socket_buffer_size`. 

> 비동기 클라이언트의 경우 보낼 데이터의 한계는`socket_buffer_size`입니다.

#### Example
