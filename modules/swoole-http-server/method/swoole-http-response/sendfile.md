

### swoole_http_response->sendfile

#### Prototype

```php
swoole_http_response->sendfile(string $filename, int $offset = 0, int $length = 0);
```

#### Illustration

Response the file content to the client.

파일 내용을 클라이언트에 응답합니다.

#### Parameter

- `$filename` the file path to send. If there is no this file, the sendfile will fail.

- `$offset` the start offset of file to send.

- `$length` the length of data to send. The default value is the whole length of file.

-`$ filename`은 보낼 파일 경로입니다. 이 파일이 없으면 sendfile이 실패합니다.

-`$ offset`은 보낼 파일의 시작 오프셋입니다.

-`$ length` 보낼 데이터의 길이. 기본값은 파일의 전체 길이입니다.

> Before the call of this method, it has to set content type by `$response->header()`.

>이 메소드를 호출하기 전에`$ response-> header ()`에 의해 컨텐츠 타입을 설정해야한다.

> Before the call of this method, it must not call `$response->write`

>이 메소드를 호출하기 전에`$ response-> write`를 호출하면 안됩니다

> After the call of this method, it will call `$response->end()` automatically.

>이 메소드를 호출하면`$ response-> end ()`가 자동으로 호출됩니다.

> `$response->sendfile` doesn't support gzip compression.

>`$ response-> sendfile`은 gzip 압축을 지원하지 않습니다.

#### Example

```php
$response->header('Content-Type', 'image/jpeg');
$response->sendfile(__DIR__.$request->server['request_uri']);
```
