

### swoole_http_response->write

#### Prototype

```php
bool swoole_http_response->write(string $data);
```

#### Illustration

Enable `chunk` feature of Http to send data to client. Check the [reference material](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Transfer-Encoding) about `chunk` feature of Http.

Http의`청크 (chunk) '기능을 사용하여 클라이언트에 데이터를 보냅니다. Http의`chunk` 기능에 대한 [참고 자료] (https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Transfer-Encoding)를 확인하십시오.

#### Parameter

- `$data` the max length of data is 2M

-`$ data` 데이터의 최대 길이는 2M입니다.

> After this method has been called, the call of `$response->end` can't be passed any parameter. 

>이 메소드가 호출 된 후에,`$ response-> end` 호출은 어떤 파라미터도 넘겨 줄 수 없습니다.

> After the call of `$response->end()`, it would send a chunk of length 0 to end data transmission. 

>`$ response-> end ()`호출 후, 데이터 전송을 끝내기 위해 길이 0의 덩어리를 보냅니다.
