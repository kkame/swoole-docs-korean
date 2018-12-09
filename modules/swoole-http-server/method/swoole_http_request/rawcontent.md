
### swoole_http_request->rawContent

#### Prototype

```php
string swoole_http_request->rawContent();
```

#### Illustration

Get the raw POST body. This method is used for the POST data which isn't in form of `application/x-www-form-urlencoded`.

원시 POST 본문을 가져옵니다. 이 메소드는`application / x-www-form-urlencoded` 형식이 아닌 POST 데이터에 사용됩니다.

#### Return 

Return the raw post data.

원시 포스트 데이터를 반환합니다.

> You can set the configuration `http_parse_post` to control the analysis of POST data. 

>`http_parse_post` 설정을 통해 POST 데이터의 분석을 제어 할 수 있습니다.