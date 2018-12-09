# Swoole TCP/UDP client

## Methods 

### swoole_client->sendfile

#### Prototype

```php
bool swoole_client->sendfile(string $filename, int $offset = 0, int $length = 0)
```

#### Illustration

Send file to the remote TCP socket.

파일을 원격 TCP 소켓으로 보냅니다.

> This is a wrapper of the Linux *sendfile* system call.

> 이것은 Linux * sendfile * 시스템 호출의 랩퍼입니다.

#### Parameter

- `$filename` the path of file to send

-`$ filename`은 보낼 파일의 경로입니다.

- `$offset` the offset of file to start send

-`$ offset`은 보낼 파일의 오프셋을 보낸다.

- `$length` the length of file to send. The default value is the whole length of file.

-`$ length` 보낼 파일의 길이. 기본값은 파일의 전체 길이입니다.

#### Return

bool

If the file doesn't exist, the return is false. 

파일이 존재하지 않으면 반환 값은 false입니다.