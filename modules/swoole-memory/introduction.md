# Swoole memory management

Swoole provides 6 different memory operation APIs: Lock, Buffer, Table, Atomic, MMap, Channel which can be used when developing multiple process programs.

Swoole은 여러 프로세스 프로그램을 개발하는 데 사용할 수있는 Lock, Buffer, Table, Atomic, MMap, Channel 등 6 가지 메모리 조작 API를 제공합니다.

All these API are async and non-blocking, multiple-process safe. Don't have to warry about the data sync issues. 

이러한 모든 API는 비동기 및 비 차단, 다중 프로세스 안전합니다. 데이터 동기화 문제에 대해 걱정할 필요가 없습니다.

### [Swoole Lock](/modules/swoole-lock.md) {#entry_h2_1}

Swoole locks enable PHP developers use locks for data synchronization between multiple theads or processes.

Swoole locks은 PHP 개발자가 여러 스레드 또는 프로세스 간의 데이터 동기화를 위해 잠금을 사용할 수있게합니다.

### [Swoole Atomic](/modules/swoole-atomic.md) {#entry_h2_5}

Integer variable allows any processor to atomically test and modify. Implemented based on CPU atomic instructions.

정수 변수를 사용하면 모든 프로세서가 원자 적으로 테스트하고 수정할 수 있습니다. CPU 원자 명령어를 기반으로 구현되었습니다.

### [Swoole Buffer](/modules/swoole-buffer.md) {#entry_h2_6}

Memory management module enable developers managing memory like C language without worrying about memory allocation, release.

메모리 관리 모듈은 개발자가 메모리 할당, 릴리스에 대한 걱정없이 C 언어와 같은 메모리를 관리 할 수있게합니다.

### [Swoole Table](/modules/swoole-table.md) {#entry_h2_7}

Swoole table is a high performance memory management module, implemented based on shared memory and spin lock.

Swoole 테이블은 공유 메모리 및 스핀 잠금을 기반으로 구현 된 고성능 메모리 관리 모듈입니다.

### [Swoole MMap](/modules/swoole-mmap.md) {#entry_h2_8}

Swoole provides the api to use mmap for files access.

Swoole은 api가 파일 액세스에 mmap을 사용할 수있게합니다.

### [Swoole Channel](/modules/swoole-channel.md) {#entry_h2_9}

Memory data structure likes Chan in Golang, implemented based on shared memory and Mutex locks. It can be used as high performance message queue in memory. 

Chan in Golang, 공유 메모리 및 뮤텍스 잠금을 기반으로합니다. 메모리의 고성능 메시지 대기열로 사용될 수 있습니다.


