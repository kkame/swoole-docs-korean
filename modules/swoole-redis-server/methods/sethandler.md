### swoole_redis_server->setHandler

#### Prototype

```php
function swoole_redis_server->setHandler(string $command, callable $callback)
```

#### Illustration

Set the handling function of redis command. 

redis 명령의 처리 기능을 설정합니다.

#### Parameter

- `$command` the redis command

- `$callback` the function to handle the redis command. The return data of this function must is in form of Redis. You can the method `swoole_redis_server::format` to make the return data.

-`$ command` redis 명령

-`$ callback` redis 명령을 처리하는 함수. 이 함수의 반환 데이터는 Redis 형식이어야합니다. `swoole_redis_server :: format` 메소드를 사용하여 리턴 데이터를 작성할 수 있습니다.

#### Example

```php
$server = new swoole_redis_server('127.0.0.1', 9501);

//synchronous mode
$server->setHandler('Set', function($fd, $data) {
    $server->array($data[0], $data[1]);
    return swoole_redis_server::format(Server::INT, 1);
});

//asynchronous mode
$server->setHandler('Get', function ($fd, $data) use ($server) {
    $db->query($sql, function($db, $result) use ($fd) {
        $server->send($fd, Server::format(Server::LIST, $result));
    });
});

$server->start();
```
