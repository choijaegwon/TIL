# Class와 Struct와 Enum의 차이를 설명하시오.

## class 
- 참조 타입
- 실제 인스턴스(데이터)는 힙에 저장되고, 그 인스턴스를 가리키는 변수에 메모리 주소가 담겨 스택에 저장됨
- 일반적으로 단일 상속이 가능하지만, 프로토콜을 사용하면 다중 상속도 가능

## struct 
- 값 타입
- 실제 인스턴스의 데이터 자체가 스택에 저장됨
- 상속이 불가능

## enum 
- 값 타입
- 상속 불가
- 유사한 종류의 여러 값을 유의미한 이름으로 한 곳에 모아 정의한 것
- 열거형 자체가 하나의 데이터 타입