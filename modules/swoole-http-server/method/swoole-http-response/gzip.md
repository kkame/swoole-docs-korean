

### swoole_http_response->gzip

#### Prototype

```php
swoole_http_response->gzip(int $level = 1);
```

#### Illustration

Enable the gzip of response content. The header about Content-Encoding will be added automatically.

응답 내용의 gzip을 활성화하십시오. Content-Encoding에 대한 헤더가 자동으로 추가됩니다.

#### Parameter

- `$level` the level of compression

- '$ 수준'압축 수준

> This method must be called before the end method

>이 메서드는 end 메서드보다 먼저 호출해야합니다.

> This method needs `zlib`. Install zlib by `sudo apt-get install libz-dev`

>이 메소드는`zlib`을 필요로합니다. `sudo apt-get install libz-dev`에 의해 zlib을 설치하십시오.