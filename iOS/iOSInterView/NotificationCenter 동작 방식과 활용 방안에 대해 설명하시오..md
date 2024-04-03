# NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.

## 동작 방식
- 특정 객체가 NotificationCenter에 등록된 Event를 발생시키면, NotificationCennter에 등록된 Observer들 중 해당 Event를 담당 중인 Observer가 그 Event에 대한 행동을 취하는 것(#selector)이 NotificationCenter가 동작하는 방식이다

## 활용 방안
- 동작방식에서 알 수 있듯이 특정 Event의 실행을 감지할 수 있기 때문에, 특정 Event의 실행에 따라 동작해야하는 것 또는 동시적으로 여러 View에서 동작해야하는 것 등을 처리할 때에 활용할 수 있다.