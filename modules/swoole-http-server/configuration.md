

### Configurations List

The object of swoole_http_server class can set some other configurations except for the configurations of `swoole_server` class.

swoole_http_server 클래스의 객체는`swoole_server` 클래스의 설정을 제외하고 다른 설정을 할 수 있습니다.

- `upload_tmp_dir`

Set the temporary path of upload files.

업로드 파일의 임시 경로를 설정하십시오.

```php
$serv->set(array(
    'upload_tmp_dir' => '/data/uploadfiles/',
));
```
> The max length of `upload_tmp_dir` is 220 bytes.

>`upload_tmp_dir`의 최대 길이는 220 바이트입니다.

- `http_parse_post`

Enable the analysis of POST data. If you set this configuration to false, the swoole will close the analysis of POST data. And if you set this configuration to true, the swoole will analyze the POST data whose `Content-Type` is `x-www-form-urlencoded`. 

POST 데이터의 분석을 활성화합니다. 이 구성을 false로 설정하면 swoole이 POST 데이터의 분석을 닫습니다. 그리고이 설정을 true로 설정하면, swoole은`Content-Type`이`x-www-form-urlencoded` 인 POST 데이터를 분석 할 것입니다.

```php
$serv->set(array(
    'http_parse_post' => false,
));
```

- `document_root`

Set the root path of static files. This configuration needs to work with `enable_static_handler`.

정적 파일의 루트 경로를 설정하십시오. 이 설정은`enable_static_handler`와 함께 작동 할 필요가 있습니다.

If the `document_root` is setted and the value of `enable_static_handler` is `true`, the swoole will judge if the request file exists. If the file requested exists, the swoole will send the file to client directly and don't call the callback function of `request`.

`document_root`가 설정되고`enable_static_handler`의 값이`true`라면, swoole은 요청 파일이 존재하는지 판단 할 것입니다. 요청 된 파일이 있으면 swoole은 파일을 클라이언트에 직접 보내고`request` 콜백 함수를 호출하지 않습니다.

```php
$server->set([
    'document_root' => '/data/webroot/example.com',
    'enable_static_handler' => true,
]);
```
