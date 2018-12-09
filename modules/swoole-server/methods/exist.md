### swoole_server->exist

#### Prototype

```php
bool swoole_server->exist(int $fd)
```

#### Illustration

Check whether the `$fd` which indicates a TCP client is existed.

TCP 클라이언트를 나타내는`$ fd `가 있는지 확인하십시오.

#### Parameter

* `$fd`	the id number of client

*`$ fd`는 클라이언트의 ID 번호입니다.

#### Return

the existence of `$fd` client

`$ fd` 클라이언트의 존재

#### Example
