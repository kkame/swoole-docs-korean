

### swoole_http_response->header

#### Prototype

```php
swoole_http_response->header(string $key, string $value)
```

#### Illustration

Set the header of http response.

http 응답 헤더를 설정합니다.

#### Parameter

- `$key` the key of header

- `$value` the value of header

-`$ key`는 헤더의 키입니다.

-`$ value`는 헤더의 값입니다.

#### Example

```php
$responser->header('Content-Type', 'image/jpeg');
```

> This method must be called before the end method

>이 메서드는 end 메서드보다 먼저 호출해야합니다.