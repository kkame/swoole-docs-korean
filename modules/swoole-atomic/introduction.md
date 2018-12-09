# Swoole Atomic

Integer variable allows any processor to atomically test and modify. Implemented based on CPU atomic instructions. 

정수 변수를 사용하면 모든 프로세서가 원자 적으로 테스트하고 수정할 수 있습니다. CPU 원자 명령어를 기반으로 구현되었습니다.

> The Swoole atomic variables have to defined before *swoole_server->start*.

> swoole 원자 변수는 * swoole_server->start * 전에 정의되었습니다.

Compare-and-swap (CAS) is an atomic instruction used in multithreading to achieve synchronization. It compares the contents of a memory location with a given value and, only if they are the same, modifies the contents of that memory location to a new given value. 

Compare-and-Swap (CAS)은 동기화를 달성하기 위해 멀티 스레딩에 사용되는 원자 적 명령어입니다. 메모리 위치의 내용을 주어진 값과 비교하여 같으면 해당 메모리 위치의 내용을 새 지정된 값으로 수정합니다.

### Example

```php
<?php
$atomic = new swoole_atomic(123);
echo $atomic->add(12)."\n";
echo $atomic->sub(11)."\n";
echo $atomic->cmpset(122, 999)."\n";
echo $atomic->cmpset(124, 999)."\n";
echo $atomic->get()."\n";
```

### Methods

#### swoole_atomic->__construct();

Construct a swoole atomic object.

Swoole의 원자 오브젝트를 구축합니다.

#### swoole_atomic->add($add_value);

Add a number to the value fo the atomic object.

원자 객체의 값에 숫자를 추가하십시오.

#### swoole_atomic->sub($sub_value);

Subtract a number to the value of the atomic object.

원자 객체의 값으로 숫자를 뺍니다.

#### swoole_atomic->get();

Get the current value of the atomic object.

원자 적 개체의 현재 값을 가져옵니다.

#### swoole_atomic->set($value);

Set the value to the atomic object.

값을 원자 적 개체로 설정하십시오.

#### swoole_atomic->cmpset($value);

Compare and set the value of the atomic object. See more about [Compare and set](https://en.wikipedia.org/wiki/Compare-and-swap).

원자 적 개체의 값을 비교하고 설정합니다. [비교 및 설정](https://en.wikipedia.org/wiki/Compare-and-swap)에 대해 자세히 알아보십시오.

#### swoole_atomic->wait($timeout);

Wait the value to be changed for a duration.

지속 기간 동안 값이 변경 될 때까지 기다립니다.

#### swoole_atomic->wakeup();

Wakeup processes waiting on the lock.

깨우기 프로세스는 잠금 대기 중입니다.
