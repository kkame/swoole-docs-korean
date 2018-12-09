### package_length_func

Set the function to check the length of package. The swoole supports the PHP function and C++ function.

패키지의 길이를 확인하는 기능을 설정하십시오. swoole은 PHP 함수와 C ++ 함수를 지원합니다.

The function returns an integer.

이 함수는 정수를 반환합니다.

- `0`, lack of data to joint a whole package

- `1`, error data, the swoole will close the connection.

- The length of package.

- `0`, 전체 패키지 조인을위한 데이터 부족

-`1`, 오류 데이터, swoole은 연결을 닫습니다.

- 포장의 길이.

#### PHP function

```php
$serv = new swoole_server("127.0.0.1", 9501);

$serv->set(array(
	'open_length_check' => true,
	'dispatch_mode' => 1,
	'package_length_func' => function ($data) {
		if (strlen($data) < 8) {
			return 0;
		}
		$length = intval(trim(substr($data, 0, 8)));
		if ($length <= 0) {
			return -1;
		}
	
		return $length + 8;
	},
	'package_max_length' => 2000000,
));

$serv->on('receive', function (swoole_server $serv, $fd, $from_id, $data){
	var_dump($data);
	echo "#{$serv->worker_id}>> received length=" . strlen($data) . "\n";
});

$serv->start();
```

#### C++ function
```c++
#include <string>
#include <iostream>
#include "swoole.h"

using namespace std;

int test_get_length(swProtocol *protocol, swConnection *conn, char *data, uint32_t length);

void register_length_function(void)
{
		swoole_add_function((char *) "test_get_length", (void *) test_get_length);
		return SW_OK;
}

int test_get_length(swProtocol *protocol, swConnection *conn, char *data, uint32_t length)
{
		printf("cpp, size=%d\n", length);
		return 100;
}
```
