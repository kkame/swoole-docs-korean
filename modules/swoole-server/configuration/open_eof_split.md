### open_eof_split

Enable the split of data to package.

데이터 분할을 사용 가능하게 설정하십시오.

Once the configuration `open_eof_check` has been setted, the worker process will receive the data ending with the specified string. This data may contain one or serval whole package. In this situation, you can enable the `open_eof_split` to split the data to package automatically. And then the callback function `onReceive` will receive a whole package.

설정`open_eof_check`가 설정되면 작업자 프로세스는 지정된 문자열로 끝나는 데이터를 수신합니다. 이 데이터에는 하나 또는 전체 serval 패키지가 포함될 수 있습니다. 이 상황에서,`open_eof_split`을 활성화하여 데이터를 패키지로 자동 분리 할 수 있습니다. 그리고 콜백 함수`onReceive`는 전체 패키지를받습니다.
