# abs(_:)
- 숫자의 절대값을 반환해 주는 함수
- 메서드 형식

~~~
func abs<T>(_ x: T) -> T where T : Comparable, T : SignedNumeric
~~~

- x: 숫자 값
- return: |입력된 숫자 값|, Int 형으로 반환해준다.

## 예시코드

~~~
let x = Int8.min
// x == -128
let y = abs(x)
// Overflow error
~~~

# Reference
https://developer.apple.com/documentation/swift/abs(_:)  