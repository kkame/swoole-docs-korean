

#### swoole_http_request->$get

The `swoole_http_request->$get` is an array which amounts to the `$_GET` of PHP.

`swoole_http_request -> $ get`은 PHP의`$ _GET`에 해당하는 배열입니다.

##### Example

```php
echo $request->get['hello'];
var_dump($request->get);
```

> The max number of GET parameters is 128

> GET 매개 변수의 최대 수는 128입니다.