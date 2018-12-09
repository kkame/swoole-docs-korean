### task_max_request

the max number of task the task worker process could handle. 

After handling the number of `task_max_request` tasks, the task worker process will exit and release all the memory amd resouce occupied by this process. And then, the manager will respawn a new task worker process.

The dafault value of `task_max_request` is 0 which means there is no limit of the max task request.

작업 작업자 프로세스가 처리 할 수있는 최대 작업 수.

`task_max_request` 태스크의 수를 처리 한 후, 태스크 작업자 프로세스는이 프로세스에 의해 점유 된 모든 메모리 및 리소스를 종료하고 해제합니다. 그런 다음 관리자가 새 작업 작업자 프로세스를 다시 생성합니다.

`task_max_request`의 dafault 값은 0이며 이는 최대 작업 요청의 한계가 없음을 의미합니다.
