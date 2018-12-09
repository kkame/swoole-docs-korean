### enable_delay_receive

Enable the delay of receiving new connection.

새 연결 수신 지연을 사용합니다.

Once enabled, the client which has been accepted would not be added to the EventLoop automaticlly and only trigger the callback function of the receive event.

일단 활성화되면, 받아 들여진 클라이언트는 EventLoop automaticlly에 추가되지 않고 수신 이벤트의 콜백 기능 만 트리거합니다.

The worker process needs to call `$serv->confirm($fd)` to confirm the connection manually and add the connection to the EventLoop. 

작업자 프로세스는 수동으로 연결을 확인하고 EventLoop에 연결을 추가하기 위해`$ serv-> confirm ($ fd)`을 호출해야합니다.

#### Usage

```php
// enable `enable_delay_receive`
$serv->set(array(
	'enable_delay_receive' => true,
));

$serv->on("Connect", function ($serv, $fd, $reactorId) {
	$serv->after(2000, function() use ($serv, $fd) {
		// confirm connection and start process data
		$serv->confirm($fd);
	});
});
```
