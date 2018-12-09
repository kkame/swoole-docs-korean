### open_length_check

Open the check of package length.

패키지 길이 점검을 엽니 다.

If this configuration has enabled, the swoole will open the analysis of package which has fixed header and body. And the worker process will receive a whole package in the callback function `onReceive`.

이 구성을 사용하면 스풀이 머리글과 본문이 고정 된 패키지 분석을 엽니 다. 그리고 작업자 프로세스는 콜백 함수`onReceive`에서 전체 패키지를받습니다.

This configuration should work with three other configurations.

이 구성은 세 가지 다른 구성에서도 작동합니다.

#### package_length_type

Use some field in the header of package to stand for the length the package. The swoole supports 10 types of length. Check the full list in [the configuration of package_length_type](/modules/swoole-server/configuration/package_length_type.md)

패키지 헤더의 일부 필드를 사용하여 패키지 길이를 표시하십시오. 스톨은 10 종류의 길이를 지원합니다. [package_length_type 구성] (/ modules / swoole-server / configuration / package_length_type.md)에서 전체 목록을 확인하십시오.

#### package_body_offset

The offset of the package to calculate the length of package.

패키지의 길이를 계산하기위한 패키지 오프셋.

- `0`, the length stands for the length of header and body

- `N`, this value stands for that the length of header is N and the length of package only contains the length of body.

- `0`, 길이는 헤더와 본문의 길이를 나타냅니다.

- `N`,이 값은 헤더의 길이가 N이고 패키지의 길이가 본문의 길이 만 포함한다는 것을 나타냅니다.

#### package_length_offset

The offset of value of length in the header

헤더의 길이 값의 오프셋

##### Example

```c
struct
{
    uint32_t type;
    uint32_t uid;
    uint32_t length;
    uint32_t serid;
    char body[0];
}
```
The configuration designed from the above protocal design

위의 protocal 디자인에서 설계된 구성

```php
$server->set(array(
    'open_length_check' => true,
    'package_max_length' => 81920,
    'package_length_type' => 'N',
    'package_length_offset' => 8,
    'package_body_offset' => 16,
));
```
