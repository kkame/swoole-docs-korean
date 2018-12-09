# Swoole Process Manager

Swoole process manager can be used to replace PHP *pcntl* extension. Compare with PHP pcntl, Swoole process manager provides more features:

Swoole 프로세스 관리자는 PHP * pcntl * 확장을 대체하는 데 사용할 수 있습니다. Swoole 프로세스 관리자는 PHP pcntl과 비교하여 더 많은 기능을 제공합니다.

* Interprocess communication based on unixsock, with read/write or push/pop API.
* Redirect standard input and output
* The child process can use swoole_event callbacks.
* Exec API enable the child process execute Linux applications and communicate with parent process

*Unixsock 기반의 프로세스 간 통신, 읽기 / 쓰기 또는 푸시 / 팝 API.
* 표준 입력 및 출력 리디렉션
* 자식 프로세스는 swoole_event 콜백을 사용할 수 있습니다.
* Exec API는 자식 프로세스가 Linux 응용 프로그램을 실행하고 부모 프로세스와 통신 할 수있게합니다.

## Table of Contents

* [Methods List](/modules/swoole-process/methods.md)
