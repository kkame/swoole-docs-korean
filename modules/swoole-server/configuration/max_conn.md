### max_conn

The max number of connection the server could handle at the same time.

서버가 동시에 처리 할 수있는 최대 연결 수입니다.

After exceed this limit, the swoole server will refuse the new coming connection.

이 제한을 초과하면 스풀 서버는 새로운 연결을 거부합니다.

> `max_conn` should be less than `ulimit -n`
> `max_conn` should be more than `(serv->worker_num + SwooleG.task_worker_num) * 2 + 32`
> the default value of `max_conn` is `ulimit -n`
> the value of `max_conn` should not be too large and be setted according to the memory usage of server.

>`max_conn`은`ulimit -n`보다 작아야합니다.
>`max_conn`은`(serv-> worker_num + SwooleG.task_worker_num) * 2 + 32`보다 커야합니다.
>`max_conn`의 기본값은`ulimit -n`입니다.
> max_conn의 값이 너무 커서 서버의 메모리 사용량에 따라 설정되어서는 안됩니다.
