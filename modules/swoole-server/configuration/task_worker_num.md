### task_worker_num

the number of task worker process.

To enable this parameter, it needs to register the callback function of `task` event and `finish` event.

The task worker process is synchronous and blocking.

According to the speed of sending task and handling task, set a reasonable value of `task_worker_num`.

작업 작업자 프로세스의 수.

이 매개 변수를 사용하려면`task` 이벤트와`finish` 이벤트의 콜백 함수를 등록해야합니다.

작업 작업자 프로세스는 동기식이며 블로킹입니다.

태스크 및 핸들링 태스크 전송 속도에 따라 'task_worker_num'값을 적당히 설정하십시오.