# Reduce(_:_:)
- 주어진 클로저를 사용하여 시퀀스의 요소를 결합한 결과를 반환

~~~
func reduce<Result>(
    _ initialResult: Result,
    _ nextPartialResult: (Result, Self.Element) throws -> Result
) rethrows -> Result
~~~

- initialResult: 초기 누적 값으로 사용할 값. 클로저가 처음 실행될 때 전달 됨
- nextPartialResult: 누적 값과 시퀀스의 요소를 새로운 누적 값으로 결합하여 다음 호출에 사용되거나, 반환되는 값
- return: 최종 누적된 값.

## 예시코드
- 전체 시퀀스의 요소에서 단일 값을 생성  

~~~
let numbers = [1, 2, 3, 4]
let numberSum = numbers.reduce(0, { x, y in
    x + y
})
// numberSum == 10
~~~

- 클로저 사용 예시
~~~
let numbers = [1, 2, 3, 4]
let numberSum = numbers.reduce(0) { $0 + $1 }
// numberSum == 10
~~~

- 이외의 사용법
~~~
let numbers = [1, 2, 3, 4]
let numberSum = numbers.reduce(0, +)
// numberSum == 10
~~~

# Reference
https://developer.apple.com/documentation/swift/array/reduce(_:_:)  
