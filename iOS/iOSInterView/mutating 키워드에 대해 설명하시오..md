# mutating 키워드에 대해 설명하시오.

- 값 타입의 속성은 기본적으로 인스턴스 메서드 내에서 수정할 수 없습니다.
- mutating을 선언한 메서드는 메서드 내에서 프로퍼티를 변경할 수 있고, 메서드가 종료될 때 변경한 모든 내용을 원래 struct에 다시 기록합니다. 또한 메서드는 self property에 새 인스턴스를 할당할 수도 있습니다.