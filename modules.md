# Swoole Modules

## [Swoole Server](/modules/swoole-server/introduction.md)

Swoole server provides the API to write TCP / UDP / UnixSocket servers.

Swoole 서버는 TCP / UDP / UnixSocket 서버를 작성하는 API를 제공합니다.

### [Quick Start](/modules/swoole-server/quick-start.md)

### [Methods List](/modules/swoole-server/methods.md)

### [Properties List](/modules/swoole-server/properties.md)

### [Configuration](/modules/swoole-server/configuration.md)

### [Predefined Constants](/modules/swoole-server/predefined-constants.md)

### [Callback functions](/modules/swoole-server/callback-functions.md)

### [Performance testing](/modules/swoole-server/performance-testing.md)

### [Common problems](/modules/swoole-server/common-problems.md)

## [Swoole HTTP Server](/modules/swoole-http-server/introduction.md)

Swoole HTTP server provides the API to write HTTP servers.

Swoole HTTP 서버는 HTTP 서버를 작성하기위한 API를 제공합니다.

### [Methods And Properties List](/modules/swoole-http-server/methods_properties.md)

### [Configurations List](/modules/swoole-http-server/configuration.md)

### [Common Problems](/modules/swoole-http-server/common-problems.md)

## [Swoole WebSocket Server](/modules/swoole-websocket-server/introduction.md)

Swoole WebSocket server provides the API to write WebSocket servers.

Swoole WebSocket 서버는 WebSocket 서버를 작성하기위한 API를 제공합니다.

### [Events And Callback Functions](/modules/swoole-websocket-server/events-callbacks.md)

### [Methods List](/modules/swoole-websocket-server/methods.md)

### [Predefined Contants](/modules/swoole-websocket-server/constants.md)

### [Common Problems](/modules/swoole-websocket-server/common-problems.md)

## [Swoole Redis Server](/modules/swoole-redis-server/introduction.md)

Swoole Redis server provides the API to write TCP servers with Redis protocol.

Swoole Redis 서버는 Redis 프로토콜을 사용하여 TCP 서버를 작성하는 API를 제공합니다.

### [Methods List](/modules/swoole-redis-server/methods.md)

### [Predefineds Contants](/modules/swoole-redis-server/constants.md)

## [Swoole TCP/UDP Client](/modules/swoole-client/introduction.md)

Swoole client provide the API to write TCP/UDP/UnixSocket/HTTP clients, supports IPv4/IPv6 protocol. Developers can write sync or async client side features with swoole client API.

Swoole 클라이언트는 TCP / UDP / UnixSocket / HTTP 클라이언트를 작성하고 IPv4 / IPv6 프로토콜을 지원하는 API를 제공합니다. 개발자는 Swoole 클라이언트 API를 사용하여 동기화 또는 비동기 클라이언트 측 기능을 작성할 수 있습니다.

### [Methods List](/modules/swoole-client/methods.md)

### [Callback functions](/modules/swoole-client/callback-functions.md)

### [Properties List](/modules/swoole-client/properties.md)

### [Predefined Constants](/modules/swoole-client/predefined-constants.md)

### [Configurations List](/modules/swoole-client/configuration.md)

### [Common Problems](/modules/swoole-client/common-problems.md)

## [Swoole Process Manager](/modules/swoole-process/introduction.md)

Linux process management module can be used to create new Linux process, manage the processes, and the communication between different processes.

리눅스 프로세스 관리 모듈은 새로운 리눅스 프로세스를 생성하고, 프로세스를 관리하며, 서로 다른 프로세스 들간의 통신을 가능하게합니다.

### [Methods List](/modules/swoole-process/methods.md)

## [Swoole Async File I/O](/modules/swoole-async-io/introduction.md)

Async API includes the async File IO API, Timer, async HTTP client API, async MySQL client API,  async Redis client API and async DNS client API.

비동기 API에는 비동기 파일 IO API, 타이머, 비동기 HTTP 클라이언트 API, 비동기 MySQL 클라이언트 API, 비동기 Redis 클라이언트 API 및 비동기 DNS 클라이언트 API가 포함됩니다.

## [Swoole MySQL Client](/modules/swoole-async-mysql-client/introduction.md)

The swoole async MySQL client is a replacement of the other sync MySQL clients: libmysqlclient, mysqlnd, mysqli.

swoole async MySQL 클라이언트는 다른 동기화 MySQL 클라이언트 인 libmysqlclient, mysqlnd, mysqli를 대신합니다.

## [Swoole Redis Client](/modules/swoole-async-redis-client/introduction.md)

Swoole async redis client is based on *hiredis*.

Swoole async redis 클라이언트는 * hiredis *를 기반으로합니다.

## [Swoole Async Http/WebSocket Client](/modules/swoole-async-http-client/introduction.md)

Swoole Async HTTP client is a high performance and aync HTTP client supports Http-Chun, Keep-Alive, form-data.

Swoole Async HTTP 클라이언트는 고성능이며 aync HTTP 클라이언트는 Http-Chun, Keep-Alive, form-data를 지원합니다.

## [Swoole Async Http2 Client](/modules/swoole-async-http2-client/introduction.md)

Http2.0 client support stream and multiplexing. Multiple GET or POST request can be sent over the same TCP connection.

Http2.0 클라이언트 지원 스트림 및 멀티플렉싱. 동일한 TCP 연결을 통해 여러 GET 또는 POST 요청을 보낼 수 있습니다.

## [Swoole EventLoop](/modules/swoole-event-loop/introduction.md)

Developers can use swoole EventLoop API to use the system EventLoop.

개발자는 EventLoop 시스템을 사용하기 위해 Swoole EventLoop API를 사용할 수 있습니다.

## [Swoole Scheduler](/modules/swoole-scheduler/introduction.md)

Schedule functions to run at set intervals, accurate to milliseconds.

일정 간격으로 밀리 초 단위로 기능을 실행하도록 예약합니다.

## [Swoole Serialize](/modules/swoole-serialize/introduction.md)

Fast serialization for PHP.

PHP를위한 빠른 직렬화.

## [Swoole Memory](/modules/swoole-memory/introduction.md)

### [Swoole Atomic](/modules/swoole-atomic/introduction.md)

Integer variable allows any processor to atomically test and modify. Implemented based on CPU atomic instructions.

정수 변수를 사용하면 모든 프로세서가 원자 적으로 테스트하고 수정할 수 있습니다. CPU 원자 명령어를 기반으로 구현되었습니다.

### [Swoole Buffer](/modules/swoole-buffer/introduction.md)

Memory management module enable developers managing memory like C language without worrying about memory allocation, release.

메모리 관리 모듈은 개발자가 메모리 할당, 릴리스에 대한 걱정없이 C 언어와 같은 메모리를 관리 할 수있게합니다.

### [Swoole Table](/modules/swoole-table/introduction.md)

Swoole table is a high performance memory management module, implemented based on shared memory and spin lock.

Swoole 테이블은 공유 메모리 및 스핀 잠금을 기반으로 구현 된 고성능 메모리 관리 모듈입니다.

### [Swoole MMap](/modules/swoole-mmap/introduction.md)

Swoole provides the api to use mmap for files access.

Swoole은 api가 파일 액세스에 mmap을 사용할 수있게합니다.

### [Swoole Channel](/modules/swoole-channel/introduction.md)

Memory data structure likes Chan in Golang, implemented based on shared memory and Mutex locks. It can be used as high performance message queue in memory. 

메모리 데이터 구조는 공유 메모리 및 뮤텍스 잠금을 기반으로 구현 된 Golang의 Chan을 좋아합니다. 메모리의 고성능 메시지 대기열로 사용될 수 있습니다.

### [Swoole Lock](/modules/swoole-lock/introduction.md)

Swoole locks enable PHP developers use locks for data synchronization between multiple theads or processes.

Swoole locks은 PHP 개발자가 여러 스레드 또는 프로세스 간의 데이터 동기화를 위해 잠금을 사용할 수있게합니다.