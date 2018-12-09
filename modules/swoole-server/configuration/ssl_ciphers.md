## Configuration 

#### ssl_ciphers

Set the `ssl_ciphers` to change the default encryption algorithm of openssl. The default encryption algorithm of openssl is `EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH`

`ssl_ciphers`를 설정하여 openssl의 기본 암호화 알고리즘을 변경하십시오. openssl의 기본 암호화 알고리즘은`EECDH + AESGCM : EDH + AESGCM : AES256 + EECDH : AES256 + EDH`입니다.

```php
$server->on(array(
    'ssl_ciphers' => 'ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP', // the swoole use the default algorithm when the `ssl_ciphers` is empty
));
```
