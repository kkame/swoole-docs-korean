# Swoole Docs

Swoole is an high-performance network framework using an event-driven, asynchronous, non-blocking I/O model which makes it scalable and efficient. It is written in C language without 3rd party libraries as PHP extension.

Swoole은 이벤트 중심의 비동기식 비 차단 I / O 모델을 사용하는 고성능 네트워크 프레임 워크로서 확장 성과 효율성을 높여줍니다. 이것은 PHP 확장으로서 타사 라이브러리가없는 C 언어로 작성되었습니다.


It enables PHP developers to write high-performance, scalable, concurrent TCP, UDP, Unix Socket, HTTP, WebSocket services in PHP programming language without too much knowledge about non-blocking I/O programming and low-level Linux kernel.

그것은 PHP 개발자가 논 블로킹 I / O 프로그래밍과 로우 레벨 리눅스 커널에 대한 지식없이 PHP 프로그래밍 언어로 고성능, 확장 성, 동시 TCP, UDP, Unix Socket, HTTP, WebSocket 서비스를 작성할 수있게합니다.

Compared with other async programming frameworks or softwares such as Nginx, Tornado, Node.js, Swoole has the built-in async, multiple threads I/O modules. Developers can use sync or async API to write the applications.

다른 비동기 프로그래밍 프레임 워크 또는 Nginx, Tornado, Node.js와 같은 소프트웨어와 비교하여 Swoole에는 비동기식 다중 스레드 I / O 모듈이 내장되어 있습니다. 개발자는 동기화 또는 비동기 API를 사용하여 응용 프로그램을 작성할 수 있습니다.

Swoole PHP network framework enhances the efficiency of R&D team, enable them to focus on the development of innovative products.

Swoole PHP 네트워크 프레임 워크는 R & D 팀의 효율성을 높이고 혁신적인 제품 개발에 집중할 수 있도록합니다.

Swoole follows the same principle as [Node.js](https://nodejs.org/en/) and [Netty](https://netty.io/), but for PHP.

Swoole은 [Node.js] (https://nodejs.org/en/) 및 [Netty] (https://netty.io/)와 동일한 원칙을 따르지 만 PHP에서는 사용하지 않습니다.

The Swoole framework is released as a [PHP extension (PECL)](https://pecl.php.net/package/swoole) and runs as a PHP CLI application.

Swoole 프레임 워크는 [PHP 확장 (PECL)] (https://pecl.php.net/package/swoole)로 출시되며 PHP CLI 응용 프로그램으로 실행됩니다.

### Hello world

``` php
<?php
$http = new swoole_http_server("127.0.0.1", 9501);

$http->on("start", function ($server) {
    echo "Swoole http server is started at http://127.0.0.1:9501\n";
});

$http->on("request", function ($request, $response) {
    $response->header("Content-Type", "text/plain");
    $response->end("Hello World\n");
});

$http->start();
```

### Features

* Rapid development of high performance protocol servers & clients with PHP language
* Event-driven, asynchronous programming for PHP
* Event loop API
* Processes management API
* Memory management API
* Async TCP/UDP/HTTP/WebSocket/HTTP2 client/server side API
* Async TCP/UDP client side API
* Async MySQL client side API and connection pool
* Async Redis client/server side API
* Async DNS client side API
* Message Queue API
* Async Task API
* Milliseconds scheduler
* Async File I/O API
* [Golang style channels](https://en.wikipedia.org/wiki/Channel_\(programming\)) for inter-processes communication
* System locks API: Filelock, Readwrite lock, semaphore, Mutex, spinlock
* IPv4/IPv6/UnixSocket/TCP/UDP and SSL/TLS support
* Fast serializer/unserializer

* PHP 언어로 고성능 프로토콜 서버 및 클라이언트의 신속한 개발
* PHP를위한 이벤트 중심의 비동기 프로그래밍
* 이벤트 루프 API
* 프로세스 관리 API
* 메모리 관리 API
* 비동기 TCP / UDP / HTTP / WebSocket / HTTP2 클라이언트 / 서버 측 API
* 비동기 TCP / UDP 클라이언트 측 API
* 비동기 MySQL 클라이언트 측 API 및 연결 풀
* Async Redis 클라이언트 / 서버 측 API
* 비동기 DNS 클라이언트 측 API
* Message Queue API
* 비동기 작업 API
* 밀리 초 스케쥴러
* 비동기 파일 I / O API
* 프로세스 간 통신을위한 [Golang 스타일 채널] (https : //en.wikipedia.org/wiki/Channel_ \ (프로그래밍 \))
* 시스템 잠금 API : 파일 잠금, 읽기 쓰기 잠금, 세마포, 뮤텍스, 스핀 록
* IPv4 / IPv6 / UnixSocket / TCP / UDP 및 SSL / TLS 지원
* 고속 시리얼 라이저 / 언 시리얼 라이저


### Use cases

* Web applications and systems
* Mobile communication systems
* Online game systems
* Internet of things
* Car networking 
* Smart home systems

Swoole framework is open source and free. Released under the license of Apache 2.0.

* 웹 응용 프로그램 및 시스템
* 이동 통신 시스템
* 온라인 게임 시스템
* 사물의 인터넷
* 자동차 네트워킹
* 스마트 홈 시스템

Swoole 프레임 워크는 오픈 소스이며 무료입니다. Apache 2.0의 라이센스하에 출시되었습니다.

### [Get started](get-started.md)

Environment preparation for swoole.

땀을 흘릴 수있는 환경 준비.

#### [Preparation](/get-started/preparation.md)

The installation guide of swoole.

설치 안내서 swoole.

#### [Installation Guide](/get-started/installation.md)

Try the examples of swoole.

봇의 예를보십시오.

#### [Code Examples](/get-started/examples.md)

### [Swoole Modules](/modules.md)

#### [Swoole Server](/modules/swoole-server/introduction.md)

Swoole server provides the API to write TCP / UDP / UnixSocket servers.

Swoole 서버는 TCP / UDP / UnixSocket 서버를 작성하는 API를 제공합니다.

#### [Swoole HTTP Server](/modules/swoole-http-server/introduction.md)

Swoole HTTP server provides the API to write HTTP servers.

Swoole HTTP 서버는 HTTP 서버를 작성하기위한 API를 제공합니다.

#### [Swoole WebSocket Server](/modules/swoole-websocket-server/introduction.md)

Swoole WebSocket server provides the API to write WebSocket servers.

Swoole WebSocket 서버는 WebSocket 서버를 작성하기위한 API를 제공합니다.

#### [Swoole Redis Server](/modules/swoole-redis-server/introduction.md)

Swoole Redis server provides the API to write TCP servers with Redis protocol.

Swoole Redis 서버는 Redis 프로토콜을 사용하여 TCP 서버를 작성하는 API를 제공합니다.

#### [Swoole TCP/UDP Client](/modules/swoole-client/introduction.md)

Swoole client provides the API to write TCP/UDP/UnixSocket/HTTP clients, supports IPv4/IPv6 protocol. Developers can write sync or async client side features with swoole client API.

Swoole 클라이언트는 TCP / UDP / UnixSocket / HTTP 클라이언트를 작성하고 IPv4 / IPv6 프로토콜을 지원하는 API를 제공합니다. 개발자는 Swoole 클라이언트 API를 사용하여 동기화 또는 비동기 클라이언트 측 기능을 작성할 수 있습니다.

#### [Swoole Process Manager](/modules/swoole-process/introduction.md)

Linux process management module can be used to create new Linux process, manage the processes, and the communication between different processes.

리눅스 프로세스 관리 모듈은 새로운 리눅스 프로세스를 생성하고, 프로세스를 관리하며, 서로 다른 프로세스 들간의 통신을 가능하게합니다.

#### [Swoole Async File I/O](/modules/swoole-async-io/introduction.md)

Async API includes the async File IO API, Timer, async HTTP client API, async MySQL client API,  async Redis client API and async DNS client API.

비동기 API에는 비동기 파일 IO API, 타이머, 비동기 HTTP 클라이언트 API, 비동기 MySQL 클라이언트 API, 비동기 Redis 클라이언트 API 및 비동기 DNS 클라이언트 API가 포함됩니다.

#### [Swoole MySQL Client](/modules/swoole-async-mysql-client/introduction.md)

The swoole async MySQL client is a replacement of the other sync MySQL clients: libmysqlclient, mysqlnd, mysqli.

swoole async MySQL 클라이언트는 다른 동기화 MySQL 클라이언트 인 libmysqlclient, mysqlnd, mysqli를 대신합니다.

#### [Swoole Redis Client](/modules/swoole-async-redis-client/introduction.md)

Swoole async Redis client is based on *hiredis*.

Swoole async Redis 클라이언트는 * hiredis *를 기반으로합니다.

#### [Swoole Async Http/WebSocket Client](/modules/swoole-async-http-client/introduction.md)

Swoole Async HTTP client is a high performance and async HTTP client supports Http-Chun, Keep-Alive, form-data.

Swoole Async HTTP 클라이언트는 고성능이며 비동기 HTTP 클라이언트는 Http-Chun, Keep-Alive, form-data를 지원합니다.

#### [Swoole Async Http2 Client](/modules/swoole-async-http2-client/introduction.md)

Http2.0 client support stream and multiplexing. Multiple GET or POST request can be sent over the same TCP connection.

Http2.0 클라이언트 지원 스트림 및 멀티플렉싱. 동일한 TCP 연결을 통해 여러 GET 또는 POST 요청을 보낼 수 있습니다.

#### [Swoole EventLoop](/modules/swoole-event-loop/introduction.md)

Developers can use Swoole EventLoop API to use the system EventLoop.

개발자는 Swoole EventLoop API를 사용하여 EventLoop 시스템을 사용할 수 있습니다.

#### [Swoole Scheduler](/modules/swoole-scheduler/introduction.md)

Schedule functions to run at set intervals, accurate to milliseconds.

일정 간격으로 밀리 초 단위로 기능을 실행하도록 예약합니다.

#### [Swoole Memory Management](/modules/swoole-memory/introduction.md)

#### [Swoole Atomic](/modules/swoole-atomic/introduction.md)

Integer variable allows any processor to atomically test and modify. Implemented based on CPU atomic instructions.

정수 변수를 사용하면 모든 프로세서가 원자 적으로 테스트하고 수정할 수 있습니다. CPU 원자 명령어를 기반으로 구현되었습니다.

#### [Swoole Buffer](/modules/swoole-buffer/introduction.md)

The memory management module enables developers managing memory like C language without worrying about memory allocation, release.

메모리 관리 모듈을 사용하면 개발자가 메모리 할당, 릴리스에 대한 걱정없이 C 언어와 같은 메모리를 관리 할 수 있습니다.

#### [Swoole Table](/modules/swoole-table/introduction.md)

Swoole table is a high performance memory management module, implemented based on shared memory and spin lock.

Swoole 테이블은 공유 메모리 및 스핀 잠금을 기반으로 구현 된 고성능 메모리 관리 모듈입니다.

#### [Swoole MMap](/modules/swoole-mmap/introduction.md)

Swoole provides the API to use mmap for files access.

Swoole은 파일 액세스에 mmap을 사용하는 API를 제공합니다.

#### [Swoole Serialize](/modules/swoole-serialize/introduction.md)

Fast serialization for PHP.

PHP를위한 빠른 직렬화.


#### [Swoole Channel](/modules/swoole-channel/introduction.md)

Memory data structure likes Chan in Golang, implemented based on shared memory and Mutex locks. It can be used as high-performance message queue in memory. 

메모리 데이터 구조는 공유 메모리 및 뮤텍스 잠금을 기반으로 구현 된 Golang의 Chan을 좋아합니다. 메모리의 고성능 메시지 대기열로 사용할 수 있습니다.

#### [Swoole Lock](/modules/swoole-lock/introduction.md)

Swoole locks enable PHP developers to use locks for data synchronisation between multiple threads or processes.

Swoole 잠금은 PHP 개발자가 여러 스레드 또는 프로세스 간의 데이터 동기화를 위해 잠금을 사용할 수있게합니다.

*Copyright © 2017 [BAOKUN DOU](https://blog.eood.cn) & [Swoole Development Group](https://github.com/swoole/swoole-src), all rights reserved.*