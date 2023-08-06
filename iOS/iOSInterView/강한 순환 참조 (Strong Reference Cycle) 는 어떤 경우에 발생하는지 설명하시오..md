# 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.

~~~
class ClassA {
	var objB: ClassB!
	deinit { print("A 객체 해제") }
}

class ClassB {
	var objA: ClassA!
	deinit { print("B 객체 해제") }
}
~~~
~~~
var a: ClassA! = ClassA()    // -> A 객체 R.C = 1
var b: ClassB! = ClassB()    // -> B 객체 R.C = 1
~~~
만약 여기서 끝난다고 해도 강한 순환 참조가 됩니다. 왜냐하면 ClassA와 ClassB 객체가 해제되지 않아 Reference Count가 1로 남아있기 때문입니다.

~~~
// 서로 객체 소유
**a.objB = b**    // -> B 객체 R.C = 2
**b.objA = a**    // -> A 객체 R.C = 2
~~~
여기서 ClassA 객체의 인스턴스인 a가 objB라는 프로퍼티를 통해서 ClassB 객체를 참조하고 있어 ClassB 객체의 R.C가 1 증가하고 ClassB 객체의 인스턴스인 b가 objA라는 프로퍼티를 통해서 ClassA 객체를 참조해 ClassA 객체의 R.C가 1씩 증가합니다.

~~~
a = nil    // -> A 객체 R.C = 1
b = nil    // -> B 객체 R.C = 1
~~~
nil을 대입해 해제하려고 해도 두 객체 모두 현재 R.C가 1씩 남아있기 때문에 객체가 해제되지 않는데 이 상황을 강한 순한 참조 라고 합니다.