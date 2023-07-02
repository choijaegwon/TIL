# Compactmap(_:)
- nil이 시퀀스의 각 요소로 지정된 변환을 호출한 비결과를 포함하는 배열을 반환한다.  

~~~
func compactMap<ElementOfResult>(_ transform: (Self.Element) throws -> ElementOfResult?) rethrows -> [ElementOfResult]
~~~

- transform: 이 시퀀스의 요소를 인수로 받아들이고 선택적 값을 반환하는 클로저.
- return: 시퀀스의 각 요소를 nil호출한 결과 가 아닌 배열(nil을 제거한 배열)

## 예시코드
- 배열에 nil이 포함되어 있을때, nil을 제거할때 사용하는 함수  

~~~
let possibleNumbers = ["1", "2", "three", "///4///", "5"]

let mapped: [Int?] = possibleNumbers.map { str in Int(str) }
// [1, 2, nil, nil, 5]

let compactMapped: [Int] = possibleNumbers.compactMap { str in Int(str) }
// [1, 2, 5]
~~~

# Reference
https://developer.apple.com/documentation/swift/sequence/compactmap(_:)  