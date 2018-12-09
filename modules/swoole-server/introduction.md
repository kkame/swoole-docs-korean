Swoole server provides the API for developers to write TCP, UDP, Unix Socket asynchronous servers. It supports IPv4, IPv6, one Way, two Way SSL and TLS Encryption. Developers do not have to know the internal implementations, only have to write the logics of the server in the callback functions.

Swoole 서버는 개발자가 TCP, UDP, Unix Socket 비동기 서버를 작성할 수있는 API를 제공합니다. 그것은 IPv4, IPv6, 편도, 양방향 SSL 및 TLS 암호화를 지원합니다. 개발자는 내부 구현을 알 필요가 없으며 서버의 로직 만 콜백 함수에 작성하면됩니다.

> Swoole server apis only can be used in the php cli mode.

> Swoole 서버 api는 php cli 모드에서만 사용할 수 있습니다.

### Table of Contents

* [Quick Start](/modules/swoole-server/quick-start.md)

* [Methods List](/modules/swoole-server/methods.md)

* [Properties List](/modules/swoole-server/properties.md)

* [Configurations List](/modules/swoole-server/configuration.md)

* [Predefined Constants](/modules/swoole-server/predefined-constants.md)

* [Callback functions](/modules/swoole-server/callback-functions.md)

* [Listening On Multiple Ports](/modules/swoole-server/multiple_ports.md)

* [Performance testing](/modules/swoole-server/performance-testing.md)

### Swoole Working Flow Chart(for SWOOLE_PROCESS mode)
![Swoole Flow](https://github.com/yannsun/swoole-docs/blob/master/static/img/swoole_process.png)

### Swoole Process/Thread Structure Chart(for SWOOLE_PROCESS mode)
![Swoole Structure](https://github.com/yannsun/swoole-docs/blob/master/static/img/swoole_structure.png)
