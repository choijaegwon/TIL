# Map(_:)
- 주어진 클로저를 시퀀스 요소에 매핑한 결과를 포함하는 배열을 반환한다.  

~~~
func map<T>(_ transform: (Self.Element) throws -> T) rethrows -> [T] 
~~~

- transform: 매핑 클로저. transform이 시퀀스의 요소를 매개변수로 받아들이고 동일하거나 다른 유형의 변환된 값을 반환
- return: 통과한 결과의 배열

## 예시코드
- map먼저 배열의 이름을 소문자 문자열로 변환한 다음 해당 문자를 계산하는 데 사용

~~~
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let lowercaseNames = cast.map { $0.lowercased() }
// 'lowercaseNames' == ["vivien", "marlon", "kim", "karl"]
let letterCounts = cast.map { $0.count }
// 'letterCounts' == [6, 6, 3, 4]
~~~

# Reference
https://developer.apple.com/documentation/swift/sequence/map(_:)  