# A comprensive guide on Lazy variables

## Cache mechanism
Implementing a caching mechanism is a use case for lazy types in Swift.  
A lazy var can be used to cache the result of a computation the first time it is performed and then return the cached value for subsequent calls.   
This can be useful for expensive computations that are called frequently because it improves performance significantly:

## 핵심 내용만 번역 
지연 변수는 계산이 처음 수행될 때 계산 결과를 캐시한 다음 후속 호출에 대해 캐시된 값을 반환하는 데 사용할 수 있습니다.   
이는 성능을 크게 향상시키기 때문에 자주 호출되는 고비용 계산에 유용할 수 있습니다:

## 예시 코드
~~~
class ExpensiveComputation {
    lazy var cachedResult: Int = {
        let result = performExpensiveComputation()
        return result
    }()

    func getResult() -> Int {
        return cachedResult
    }

    private func performExpensiveComputation() -> Int {
        // 비용이 많이 드는 계산을 수행하는 코드
        return 100
    }
}

let computation = ExpensiveComputation()
print(computation.getResult()) // 비용이 많이 드는 계산을 수행하고 결과를 캐시한다.
print(computation.getResult()) // 계산을 다시 수행하지않고 캐시된 결과를 반환한다.
~~~

## 장점
- 실제로 필요할 때까지 값의 계산을 연기함으로써 지연 초기화는 불필요한 계산을 줄여 성능을 향상시킬 수 있다.
- 필요할 때까지 값 초기화를 연기함으로써 특히 계산 비용이 많이 들거나 많은 양의 메모리가 필요한 값의 경우 메모리 사용량을 줄일 수 있다.
- 실제로 필요할 때까지 종속 속성의 초기화를 연기하여 복잡한 종속성을 가진 개체의 초기화를 단순화하는 데 사용할 수 있다.

## 단점
- 클로저를 사용해야 하므로 속성과 메서드 간에 새로운 종속성을 도입할 수 있다.
- 여러 스레드가 동시에 동일한 지연 속성 에 액세스를 시도할 수 있기 때문에 문제가 될 수 있다. 속성이 제대로 보호되지 않으면 경쟁 조건 및 기타 동기화 문제가 발생할 수 있다.
- 경우에 따라 메모리 사용량을 줄일 수 있지만 클로저를 사용하여 초기화를 연기해야 ​​하므로 메모리 사용량을 증가시킬 수도 있다.

# Reference
https://levelup.gitconnected.com/mastering-swift-a-comprensive-guide-on-lazy-variables-23c0a6bbbe4d