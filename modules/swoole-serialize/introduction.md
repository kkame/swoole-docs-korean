# Swoole Serialize

Swoole provides a fast and high performance serialization module.

Swoole은 빠르고 고성능 직렬화 모듈을 제공합니다.

## Methods

### string swoole_serialize->pack(mixed $data, $is_fast = 0);

#### Illustration

Serialize the data.

데이터를 직렬화하십시오.

#### Parameter

- `$data` the data to serialize

-`$ data`는 직렬화 할 데이터입니다.

- `$is_fast` if enable fast mode

- 고속 모드를 가능하게한다면`$ is_fast`

#### Return

If the process of serialization succeeds, it returns the binary string as the result of serialization. Otherwise, it returns false.

직렬화 프로세스가 성공하면 직렬화의 결과로 2 진 문자열을 리턴합니다. 그렇지 않으면 false를 반환합니다.

### mixed swoole_serialize->unpack($data);

#### Illustration

Unserialize the data.

데이터의 직렬화를 해제하십시오.

#### Parameter

- `$data` the data to unserialize

-`$ data`는 비 직렬화 할 데이터입니다.

#### Return

If the process of unserialization succeeds, it returns the unserialized data. Otherwise, it returns false.

비 직렬화 프로세스가 성공하면 비 직렬화 된 데이터를 리턴합니다. 그렇지 않으면 false를 반환합니다.