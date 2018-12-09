### swoole_redis_server::format

#### Prototype

```php
function swoole_redis_server::format(int $type, mixed $value = null);
```

#### Illustration

Format the data to the format of redis

데이터를 redis 형식으로 포맷합니다.

#### Parameter

- `$format` the type of data. `NIL`, `ERROR`, `STATUS`, `INT`, `STRING`, `SET`, `MAP` 

-`$ format`은 데이터의 타입입니다. `NIL`,`ERROR`,`STATUS`,`INT`,`STRING`,`SET`,`MAP`