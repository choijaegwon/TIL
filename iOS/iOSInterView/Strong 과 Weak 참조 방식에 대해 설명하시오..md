# Strong 과 Weak 참조 방식에 대해 설명하시오.

## Strong (강한 참조)
- 해당 인스턴스의 소유권을 가진다.
- 자신이 참조하는 인스턴스의 retain count를 증가시킨다.
- 값 지정 시점에 retain이 되고, 참조가 종료되는 시점에 release가 된다.
- 선언할 때 아무것도 적어주지 않으면 default로 strong이 된다.
~~~
var test = Test() // retain count 1 증가
test = nil // retain count가 1 감소 되어 0 이 되면서 메모리 해제됨
~~~

## Weak (약한 참조)
- 해당 인스턴스의 소유권을 가지지 않고, 주소값만을 가지고 있는 포인터 개념이다.
- 자신이 참조하는 인스턴스의 retain count를 증가시키지 않는다. release도 발생하지 - 않는다.
- 자신이 참조는 하지만 weak 메모리를 해제시킬 수 있는 권한은 다른 클래스에 있따.
- 메모리가 해제될 경우 자동으로 레퍼런스가 nil로 초기화를 해준다.
- weak 속성을 사용하는 객체는 항상 optional타입이어야 한다.(해당객체가 nil일 수 있기때문)
~~~
var test = Test() // retain count 1 증가
test = nil // retain count가 1 감소 되어 0 이 되면서 메모리 해제됨
~~~