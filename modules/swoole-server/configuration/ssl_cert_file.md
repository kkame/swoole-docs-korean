## Configuration 

### ssl_cert_file

> It must add `--enable-openssl` to the support for ssl when you compile the swoole

> swoole을 컴파일 할 때 ssl 지원에`--enable-openssl`을 추가해야합니다

To enable ssl, it should set the file path of the cert file and the key file.

ssl을 사용하려면 cert 파일과 키 파일의 파일 경로를 설정해야합니다.

```php
$server = new swoole_server("0.0.0.0", 9501, SWOOLE_PROCESS, SWOOLE_SOCK_TCP | SWOOLE_SSL);
$server->set(array(
    'ssl_cert_file' => __DIR__ . '/config/ssl.cert',
    'ssl_key_file' => __DIR__ . '/config/ssl.key',
));
```

 - The web browser must believes in the credential before browsing the webpage
 - In the websock application, the part starting the connection of websocket must use https
 - The certificate extensions must be PEM and not DER
 
 - 웹 브라우저는 웹 페이지를 탐색하기 전에 자격 증명을 믿어야합니다.
 - websock 응용 프로그램에서 websocket 연결을 시작하는 부분은 https를 사용해야합니다.
 - 인증서 확장은 DEM이 아닌 PEM이어야합니다.
Convert PEM to DER
```
openssl x509 -in cert.crt -outform der -out cert.der
```
Convert DER to PEM
```
openssl x509 -in cert.crt -inform der -outform pem -out cert.pem
```
