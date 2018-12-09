### package_max_length

The max length of package whose unit is byte.

단위가 바이트 인 패키지의 최대 길이.

Once the configuration `open_length_check/open_eof_check/open_http_protocol` has enabled, the internal of swoole will joint the data received from the client amd the data stores in the memory before recevicing the whole package. So to limit the usage of memory, it should set the `package_max_length`.

설정`open_length_check / open_eof_check / open_http_protocol`이 활성화되면, 전체 패키지를 수신하기 전에 내부 메모리가 클라이언트로부터받은 데이터와 메모리의 데이터 저장소를 연결합니다. 그래서 메모리 사용을 제한하기 위해`package_max_length`를 설정해야합니다.
