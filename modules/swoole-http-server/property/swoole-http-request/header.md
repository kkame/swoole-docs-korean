

#### swoole_http_request->$header

The `swoole_http_request->$header` is an array which contains the information of http request.

`swoole_http_request -> $ header`는 http 요청의 정보를 담고있는 배열입니다.

All the keys of this array is lowercase.

이 배열의 모든 키는 소문자입니다.

##### Example

```php
echo $request->header['host'];
echo $request->header['accept-language'];
```
