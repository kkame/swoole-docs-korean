

### swoole_http_response->cookie

#### Prototype

```php
swoole_http_response->cookie(string $key, string $value = '', int $expire = 0 , string $path = '/', string $domain  = '', bool $secure = false , bool $httponly = false);
```

#### Illustration

Amount to `setcookie` of PHP.

PHP의`setcookie '에 대한 금액.

> This method must be called before the end method

>이 메서드는 end 메서드보다 먼저 호출해야합니다.