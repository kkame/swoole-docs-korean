### heartbeat_check_interval

This configuration `heartbeat_check_interval` is the interval of polling every TCP connection. 

이 설정`heartbeat_check_interval`은 모든 TCP 연결을 폴링하는 간격입니다.

If the connection hasn't sent any data to the server in the last interval of `heartbeat_check_interval`, the connection will be closed.

`heartbeat_check_interval`의 마지막 간격으로 연결이 서버에 데이터를 보내지 않으면 연결이 닫힙니다.

The swoole server would not send the heartbeat packet to the client but only wait for the heartbeat packet from the client. The heartbeat check of swoole server only check the last time of sending data from the client. If the time exceeds `heartbeat_check_interval`, the connection between the server and the client will be closed.

스풀 서버는 하트 비트 패킷을 클라이언트로 보내지 않지만 클라이언트의 하트 비트 패킷 만 기다립니다. 스풀 서버의 하트 비트 검사는 마지막으로 클라이언트에서 데이터를 보내는 시간 만 확인합니다. `heartbeat_check_interval`을 초과하면 서버와 클라이언트 사이의 연결이 닫힙니다.
