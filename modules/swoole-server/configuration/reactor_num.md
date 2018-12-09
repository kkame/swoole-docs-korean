## Configuration 

### reactor_num 

the number of the reactor thread(for SWOOLE_BASE_MODE)

You can change the number of event processing thread in the master process. 

To make full use of cpu, the default number of `reactor_num` is the number of core in cpu.

In general, the number of the reactor thread is between one and four times of cpu cores.

반응기 스레드의 번호 (SWOOLE_BASE_MODE의 경우)

마스터 프로세스에서 이벤트 처리 스레드 수를 변경할 수 있습니다.

cpu를 최대한 활용하려면`reactor_num`의 기본 숫자는 cpu의 코어 수입니다.

일반적으로 반응기 스레드의 수는 CPU 코어의 1 ~ 4 배입니다.
