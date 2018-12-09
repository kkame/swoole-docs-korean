### onHandShake

This event happens when the websocket connection start the handshake process. The `swoole_websocket_server` has built-in callback function registered for event `handshake`. But you can also choose to custom your callback function for event `handshake`.

이 이벤트는 websocket 연결이 핸드 셰이크 프로세스를 시작할 때 발생합니다. `swoole_websocket_server`는 이벤트`handshake`를 위해 내장 된 콜백 함수를 내장하고 있습니다. 그러나 이벤트`handshake`에 대한 커스텀 콜백 함수를 선택할 수도 있습니다.

#### Example

```php
function onHandShake(swoole_http_request $request, swoole_http_response $response)
```

- If the return of function is `true`, the handshake is successful.

- 함수 반환이 'true'이면 핸드 셰이크가 성공한 것입니다.

> The callback function for event `handshake` is optional.

> 이벤트`handshake '에 대한 콜백 함수는 선택 사항입니다.

> If the callback function for event `handshake` has been customed, the event `open` would not be triggered. 

> 이벤트`핸드 쉐이크 '에 대한 콜백 함수가 커스텀 화 된 경우, 이벤트`open`은 트리거되지 않습니다.

> The built-in protocol of handshake is `Sec-WebSocket-Version: 13`, it needs to implemen t the process of handshake when the browser is in low-version.

> 핸드 셰이크의 내장 프로토콜은`Sec-WebSocket-Version : 13`이며, 브라우저의 버전이 낮을 때 핸드 셰이크 과정을 구현해야합니다.


#### Example Code

```php
$server->on('handshake', function (\swoole_http_request $request, \swoole_http_response $response) {
	$secWebSocketKey = $request->header['sec-websocket-key'];
	$patten = '#^[+/0-9A-Za-z]{21}[AQgw]==$#';
	
	if (0 === preg_match($patten, $secWebSocketKey) || 16 !== strlen(base64_decode($secWebSocketKey))) {
		$response->end();
		return false;
	}
	
	echo $request->header['sec-websocket-key'];
	
	$key = base64_encode(sha1($request->header['sec-websocket-key'] . '258EAFA5-E914-47DA-95CA-C5AB0DC85B11', true));

	$headers = [
		'Upgrade' => 'websocket',
		'Connection' => 'Upgrade',
		'Sec-WebSocket-Accept' => $key,
		'Sec-WebSocket-Version' => '13',
	];

	// WebSocket connection to 'ws://127.0.0.1:9502/'
	// failed: Error during WebSocket handshake:
	// Response must not include 'Sec-WebSocket-Protocol' header if not present in request: websocket
	if (isset($request->header['sec-websocket-protocol'])) {
		$headers['Sec-WebSocket-Protocol'] = $request->header['sec-websocket-protocol'];
	}

	foreach ($headers as $key => $val) {
		$response->header($key, $val);
	}

	$response->status(101);
	$response->end();
	echo "connected!" . PHP_EOL;
	return true;
});

```
