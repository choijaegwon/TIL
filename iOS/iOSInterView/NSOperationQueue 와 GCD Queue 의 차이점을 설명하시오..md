# NSOperationQueue 와 GCD Queue 의 차이점을 설명하시오.

## NSOperationQueuePermalink
- Objective-C 기반 고수준 API
- GCD보다 약간의 오버헤드가 더 발생되고 느리다. But KVO 지원 및 작업취소등을 지원
- 다양한 작업들 중에서 의존성을 추가할 수 있다
- 재사용, 취소, 중지 가능하다
- NSOperation을 만들어서 병렬 or 직렬로 스레드 풀을 사용가능하다.

## GCD QueuePermalink
- C기반 로우레벨의 API
- Global Queue에서 QOS 우선순위를 줄 수 있다.
- Main Queue: 메인 스레드에서 사용될 것 들을 처리, UI코드