# Swoole TCP/UDP client

## Methods 

### swoole_client->isConnected

#### Prototype

```php
bool swoole_client->isConnected()
```

#### Illustration

Check if the connection is established.

연결이 설정되어 있는지 확인하십시오.

> The method returns the connection status of application layer. Perhaps the return means that the client is connected to the server, but the connection is unusable.

>이 메소드는 응용 프로그램 계층의 연결 상태를 반환합니다. 아마도 반환은 클라이언트가 서버에 연결되어 있지만 연결을 사용할 수 없음을 의미합니다.

#### Parameter

void

#### Return

bool

#### Example
