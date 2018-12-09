The class `swoole_redis_server` inherits from the class `swoole_server`.

`swoole_redis_server` 클래스는`swoole_server` 클래스에서 상속받습니다.

It can call the methods of class `swoole_server` and its own methods. 

클래스`swoole_server`의 메소드와 메소드를 호출 할 수 있습니다.

The object of class `swoole_redis_server` doesn't need to register the callback function for event `receive`. It needs to use the method `setHandler` to set the corresponding function fo redis command. If the swoole redis server receives the command that hasn't the corresponding function to handle, it responds the message `ERR unknown command '$command'`.

`swoole_redis_server` 클래스의 객체는`receive` 이벤트에 대한 콜백 함수를 등록 할 필요가 없습니다. `setHandler` 메서드를 사용하여 redis 명령에 해당하는 함수를 설정해야합니다. swoole redis 서버가 처리 할 해당 기능이없는 명령을 받으면`ERR unknown command '$ command'` 메시지에 응답합니다.

### Table of Contents

* [swoole_redis_server->setHandler](/modules/swoole-redis-server/methods/sethandler.md)

* [swoole_redis_server::format](/modules/swoole-redis-server/methods/format.md)
