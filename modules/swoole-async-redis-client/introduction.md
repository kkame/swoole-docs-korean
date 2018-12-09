# Swoole Async Redis client

Swoole async redis client is based on *hiredis*.

Swoole async redis 클라이언트는 * hiredis *를 기반으로합니다.

### Install *hiredis* library

```bash
wget https://github.com/redis/hiredis/archive/v0.13.3.tar.gz
tar zxvf v0.13.3.tar.gz
cd hiredis-0.13.3/
make -j
sudo make install
sudo ldconfig
```

#### Compile hiredis library into Swoole extension

```bash
./configure --enable-async-redis
make clean
make -j
sudo make install
```

### Events

* message
* close

### Methods:

#### swoole_redis->connect(string $host, int $port, callable $callback);

Connect to the Redis server.

Redis 서버에 연결하십시오.

Example:

예제 :

```php
<?php
$client = new swoole_redis;
$client->connect('127.0.0.1', 6379, function (swoole_redis $client, $result) {
    if ($result === false) {
        echo "connect to redis server failed.\n"
        return;
    }
    $client->set('key', 'swoole', function (swoole_redis $client, $result) {
        var_dump($result);
    });
});
```

#### function swoole_redis->on(string $event_name, callable $callback);

Register callback function based on event name: *Close* and *Message*, *Receive*.

이벤트 이름에 기반한 콜백 함수 등록 : * Close * 및 * Message *, * Receive *.

Example:

예제 :

```php
<?php
$client = new swoole_redis;
$client->on('message', function (swoole_redis $client, $result) {
    var_dump($result);
    static $more = false;
    if (!$more and $result[0] == 'message')
    {
        echo "subscribe new channel\n";
        $client->subscribe('msg_1', 'msg_2');
        $client->unsubscribe('msg_0');
        $more = true;
    }
});
$client->connect('127.0.0.1', 6379, function (swoole_redis $client, $result) {
    echo "connect\n";
    $client->subscribe('msg_0');
});
```

#### function swoole_redis->__call(string $command, array $params);

Execute redis client commands: [http://redis.io/commands](http://redis.io/commands)

redis 클라이언트 명령을 실행합니다 : [http://redis.io/commands](http://redis.io/commands)

Commands:

명령 :

* subscribe
* psubscribe
* unsubscribe
* punsubscribe

#### function swoole_redis->close();

Close the redis connection.

다시 연결을 닫습니다.