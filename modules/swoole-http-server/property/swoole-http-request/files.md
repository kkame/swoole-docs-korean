

#### swoole_http_request->$files

The `swoole_http_request->$files` is an array which amounts to the `$_FILES` of PHP.

`swoole_http_request -> $ files`는 PHP의`$ _FILES`에 해당하는 배열입니다.

##### Example

```php
var_dump($request->cookie);
Array
(
 [name] => facepalm.jpg
 [type] => image/jpeg
 [tmp_name] => /tmp/swoole.upfile.n3FmFr
 [error] => 0
 [size] => 15476
)
```
> The uploaded files will be deleted after the run of `$response->end()`

> 업로드 된 파일은`$ response-> end ()`실행 후 삭제됩니다.