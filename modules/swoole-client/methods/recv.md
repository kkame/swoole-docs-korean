# Swoole TCP/UDP client

## Methods 

### swoole_client->recv

#### Prototype

```php
string swoole_client->recv(int $size = 65535, int $flags = 0);
```

#### Illustration

Receive data from the remote socket.

원격 소켓에서 데이터를 수신합니다.

#### Parameter

- `$size` the buffer size of receiving data

-`$ size`는 데이터 수신의 버퍼 크기

- `$flags` the configuration of receiving data(Check the predefined constants of class swoole_client)

-`$ flags` 데이터 수신 설정 (swoole_client 클래스의 미리 정의 된 상수 확인)

> If the swoole client has setted the configuration about check of `EOF/Length`, it doesn't need to set the parameter `$size` and `$flags` and the swoole client will return the whole package.

> swoole 클라이언트가`EOF / Length` 검사에 관한 설정을했다면`$ size`와`$ flags` 매개 변수를 설정할 필요가 없으며 swoole 클라이언트는 전체 패키지를 반환합니다.

#### Return

If the client receives data successfully, it returns the length of data received. Or it returns `false` and sets `$swoole_client->errCode`.

클라이언트가 데이터를 성공적으로 수신하면 수신 된 데이터의 길이를 반환합니다. 아니면`false`를 반환하고`$ swoole_client-> errCode`를 설정합니다.

#### Example
```php
$client->recv(8192, swoole_client::MSG_PEEK | swoole_client::MSG_WAITALL);
```
