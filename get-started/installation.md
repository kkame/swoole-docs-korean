## Installation

### Installation

#### Install by binary releases

##### Linux users

> Swoole is available as a PECL compatible package

> Swoole은 PECL 호환 패키지로 제공됩니다.

```bash
pecl install swoole
```
##### MacOS X \(macOS\) users

> It is highly recommended to install Swoole on Mac OS X or macOS systems via homebrew

> Swoole을 Mac OS X 또는 macOS 시스템에 homebrew를 통해 설치하는 것이 좋습니다

```bash
brew install swoole
```

#### Building swoole from sources

##### Download link

You are recommended to download the latest stable version of swoole. You can download the source code from one of the following the links.

최신 안정 버전의 swoole을 다운로드하는 것이 좋습니다. 다음 링크 중 하나에서 소스 코드를 다운로드 할 수 있습니다.

- [https://github.com/swoole/swoole-src/releases](https://github.com/swoole/swoole-src/releases)
- [http://pecl.php.net/package/swoole](http://pecl.php.net/package/swoole)
- [http://git.oschina.net/swoole/swoole/releases](http://git.oschina.net/swoole/swoole/releases)

##### Steps of Compilation 

The process of compile and install the swoole extension for PHP

PHP 용 swoole 확장을 컴파일하고 설치하는 프로세스

```bash
cd swoole          #  enter the directory of swoole source code   
phpize       	   #  prepare the build environment for a PHP extension
./configure        #  add configuration paramaters as needed
make 			   #  a successful result of make is swoole/module/swoole.so
sudo make install  #  install the swoole into the PHP extensions directory
```

### Enable swoole

After installing the swoole extension to the PHP extensions directory, you will need to edit php.ini and add an extension=swoole.so line before you can use the swoole extension.

swoole 확장을 PHP 확장 디렉토리에 설치 한 후 swoole 확장을 사용하기 전에 php.ini를 편집하고 extension = swoole.so 행을 추가해야합니다.

```bash
php -i | grep php.ini                      # check the php.ini file location
sudo echo "extension=swoole.so" > php.ini  # add the extension=swoole.so to the end of php.ini
php -m | grep swoole                       # check if the swoole extension has been enabled
```

### Configuration paramaters

These configurations are used for enabling some features.

이러한 구성은 일부 기능을 사용하는 데 사용됩니다.

`--enable-swoole-debug` 

Enable the debug logs of swoole. Don't enable this configuration in production environment.

swoole의 디버그 로그를 활성화합니다. 프로덕션 환경에서는이 구성을 사용하지 마십시오.

`--enable-sockets` 

Enable sockets support. It depends on the PHP sockets extension. If this configuration has been enabled, the function swoole_event_add() could add the connection created by the sockets extension to the event loop of swoole. And the function getSocket() depends on this configuration.  

소켓 지원을 활성화하십시오. PHP 소켓 확장에 따라 다릅니다. 이 구성이 활성화 된 경우 swoole_event_add () 함수는 소켓 확장에 의해 생성 된 연결을 swoole의 이벤트 루프에 추가 할 수 있습니다. 그리고 getSocket () 함수는이 설정에 의존한다.

`--enable-openssl` 

Enable openssl support. It depends on the libssl.so library given by operating system.

openssl 지원을 사용합니다. 운영 체제에서 제공하는 libssl.so 라이브러리에 따라 다릅니다.

`--with-openssl-dir`

Set the path of openssl library, for example:`--with-openssl-dir=/opt/openssl/.`

openssl 라이브러리의 경로를 설정합니다 (예 :`--with-openssl-dir = / opt / openssl / .`).

`--enable-http2`

Enable the support of HTTP2. It depends on nghttp2 library.

HTTP2의 지원을 활성화하십시오. 그것은 nghttp2 라이브러리에 달려 있습니다.

`--enable-async-redis`

Enable the support of async redis client. It depends on hiredis library.

비동기 적발 클라이언트의 지원을 활성화하십시오. hiredis 라이브러리에 따라 다릅니다.

`--enable-timewheel`

Enable the support of timewheel and optimize the heartbeat algorithm.

타임 휠을 지원하고 하트 비트 알고리즘을 최적화하십시오.

> This is an experimental feature. Don't use this feature in production environment.

`--enable-mysqlnd`

Enable the support of mysqlnd, for example `swoole_mysql::escapse`.

'swoole mysql :: escape'와 같이 mysqlnd의 지원을 활성화하십시오.

`--enable-ringbuffer`

Enable the support of ringbuffer memory pool.

링 버퍼 메모리 풀의 지원을 가능하게합니다.

> This is an experimental feature. Don't use this feature in production environment

> 실험적인 기능입니다. 프로덕션 환경에서이 기능을 사용하지 마십시오.

**After the installation of swoole,  try the [examples](/get-started/examples.md) written by swoole.**

** swoole을 설치 한 후 swoole로 작성된 [examples](/get-started/examples.md)를 시도하십시오. **