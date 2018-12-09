### discard_timeout_request

If the configuration of `dispatch_mode` is 1 or 3, there may be some data that arrive to worker process after closing the connection.

`dispatch_mode`의 설정이 1 또는 3이면, 연결을 닫은 후에 작업자 프로세스에 도착하는 데이터가있을 수 있습니다.

In this situation, if `discard_timeout_request` is true, the worker process will discard these data or still procee these data.

이 상황에서`discard_timeout_request`가 참이면 작업자 프로세스는이 데이터를 버리거나 여전히이 데이터를 처리합니다.