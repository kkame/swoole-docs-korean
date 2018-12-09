### swoole_server->protect

#### Prototype

```php
swoole_server->protect(int $fd, bool $value = true)
```

#### Illustration

Protect the `$fd` from being closed by the thread of checking heart beat

`$ fd`가 심장 박동 검사의 실에 의해 닫히지 않도록 보호하십시오

#### Parameter

* `$fd`	the id number of client
* `$value` if true, protect the `$fd`. If false, remove the protect from `$fd`

*`$ fd`는 클라이언트의 ID 번호입니다.
*`$ value`가 참이면,`$ fd`를 보호하십시오. 거짓이면`$ fd`에서 protect를 제거하십시오.

#### Return


#### Example
