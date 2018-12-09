# Swoole TCP/UDP client

## Methods 

### swoole_client->sendto

#### Prototype

```php
bool swoole_client->sendto(string $ip, int $port, string $data);
```

#### Illustration

Send data to the remote UDP address. The swoole client should be type of SWOOLE_SOCK_UDP or SWOOLE_SOCK_UDP6.

원격 UDP 주소로 데이터를 보냅니다. swoole 클라이언트는 SWOOLE_SOCK_UDP 또는 SWOOLE_SOCK_UDP6 유형이어야합니다.

#### Parameter

- `$ip` the ip address of remote host, ipv4 or ipv6

-`$ ip` 원격 호스트의 ip 주소, ipv4 또는 ipv6

- `$port` the port number of remote host

-`$ port` 원격 호스트의 포트 번호

- `$data` the data to send which should be less-than 64K.

-`$ data`는 보낼 데이터가 64K보다 작아야합니다.

#### Return

bool
