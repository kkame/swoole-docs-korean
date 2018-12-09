### buffer_output_size

Set the output buffer size in the memory.

출력 버퍼 크기를 메모리에 설정하십시오.

The default value is 2M. The data to send can't be larger than `buffer_output_size` every times.

기본값은 2M입니다. 보낼 데이터는 매번`buffer_output_size`보다 클 수 없습니다.

#### Usage
```php
$server->set([
    'buffer_output_size' => 32 * 1024 *1024, // byte in unit
])
```


