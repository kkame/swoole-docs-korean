# Swoole TCP/UDP client

## Methods 

### swoole_client->getPeerName

#### Prototype

```php
array swoole_client->getPeerName();
```

#### Illustration

Get the remote socket name of the connection.

접속의 리모트 소켓 명을 가져옵니다.

#### Parameter

void

#### Return

The array of remote socket host and port

원격 소켓 호스트와 포트의 배열

```php
array('host' => '127.0.0.1', 'port' => 53652)
```
