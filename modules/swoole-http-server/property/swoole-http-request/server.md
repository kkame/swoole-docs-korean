

#### swoole_http_request->$server

The `swoole_http_request->$server` is an array which contains the information of server and amounts to the `$_SERVER` of PHP.

`swoole_http_request -> $ server`는 서버의 정보를 포함하고 PHP의`$ _SERVER`에 해당하는 배열입니다.

All the keys of this array is lowercase.

이 배열의 모든 키는 소문자입니다.

##### Example

```php
echo $request->server['request_time'];
```
