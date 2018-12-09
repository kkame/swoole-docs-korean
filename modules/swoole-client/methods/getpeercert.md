# Swoole TCP/UDP client

## Methods 

### swoole_client->getPeerCert

#### Prototype

```php
string swoole_client->getPeerCert();
```

#### Illustration

Get the Cert of the remote server.

원격 서버의 인증서를 가져옵니다.

> It needs the support of openssl. You should compile swoole with `--enable-openssl`.

> openssl의 지원이 필요합니다. `--enable-openssl`로 swoole을 컴파일해야합니다.

#### Parameter

void

#### Return

The Cert of the remote server. You can use the function `openssl_x509_parse` of extension openssl to parse the cert information.

원격 서버의 인증서. 확장 openssl의 openssl_x509_parse 함수를 사용하여 인증서 정보를 파싱 할 수 있습니다.
