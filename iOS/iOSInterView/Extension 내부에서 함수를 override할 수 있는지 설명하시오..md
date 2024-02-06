# Extension 내부에서 함수를 override할 수 있는지 설명하시오.

- 새로운 기능을 정의하는 것은 가능하지만 override할수는 없습니다.
- override는 부모클래스의 메서드를 자식클래스가 재정의하여 사용하는 것을 의미하지만, extension은 수평적인 확장이기 때문에 override라는 개념이 어울리지 않습니다.