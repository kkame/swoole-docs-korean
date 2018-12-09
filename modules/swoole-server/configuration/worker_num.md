## Configuration 

### worker_num 

the number of the worker process

작업자 프로세스의 수

If the code of logic is asynchronous and non-blocking, set the `worker_num` to the value from one times to four times of cpu cores.
If the code of logic is synchronous and blocking, set the `worker_num` according to the consuming time of request and load of os.

논리 코드가 비동기식이고 비 차단 형인 경우 'worker_num'을 한 번에서 네 번까지의 값으로 설정합니다.
논리 코드가 동기식이고 블로킹 (blocking)이라면 요청과 소비 시간의 소비 시간에 따라 'worker_num'을 설정하십시오.