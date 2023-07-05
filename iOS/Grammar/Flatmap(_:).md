# Flatmap(_:)
- 이 시퀀스의 각 요소로 지정된 변환을 호출한 연결된 결과를 포함하는 배열을 반환한다.

~~~
func flatMap<SegmentOfResult>(_ transform: (Self.Element) throws -> SegmentOfResult) rethrows -> [SegmentOfResult.Element] where SegmentOfResult : Sequence
~~~

- transform: 이 시퀀스의 요소를 인수로 받아들이고 시퀀스 또는 컬렉션을 반환하는 클로저.
- return: 평면화 된 배열 (1차 배열)

## 예시코드
- 이중 배열을 1차원 배열로 바꿔준다.  

~~~
let numbers = [1, 2, 3, 4]

let mapped = numbers.map { Array(repeating: $0, count: $0) }
// [[1], [2, 2], [3, 3, 3], [4, 4, 4, 4]]

let flatMapped = numbers.flatMap { Array(repeating: $0, count: $0) }
// [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
~~~

# Reference
https://developer.apple.com/documentation/swift/sequence/flatmap(_:)-jo2y  