# GCD API 동작 방식과 필요성에 대해 설명하시오.

## 동작 방식
- 해야 할 일(코드)을 Operation으로 Wrapping한 다음에, Queue에 넣는다. Queue에서 남는 스레드에 작업을 배분한다.

## 필요성
- 웹에서 이미지를 다운 받아서 사용자에게 보여준다고 했을 때, 비동기로 처리하지 않는다면 이미지를 다운받는 동안 다른 작업을 할 수 없기 때문에 앱이 멈춘다. 이렇게 비용이 많이 들어가는? 작업을 메인 스레드에서 진행하면 사용자가 다른 작업을 할 수 없기 때문에 필요하다고 생각한다.