

### swoole_http_response->status

#### Prototype

```php
swoole_http_response->status(int $http_status_code);
```

#### Illustration

Set the http response status.

http 응답 상태를 설정하십시오.

> This method must be called before the end method

>이 메서드는 end 메서드보다 먼저 호출해야합니다.