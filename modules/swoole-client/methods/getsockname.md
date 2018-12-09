# Swoole TCP/UDP client

## Methods 

### swoole_client->getSockName

#### Prototype

```php
array swoole_client->getSockName();
```

#### Illustration

Get the local socket name of the connection.

접속의 로컬 소켓 명을 가져옵니다.

#### Parameter

void

#### Return

The array of local socket host and port

로컬 소켓 호스트와 포트의 배열

```php
array('host' => '127.0.0.1', 'port' => 53652)
```
