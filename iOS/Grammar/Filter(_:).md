# Filter(_:)
- 주어진 조건자를 만족하는 시퀀스의 요소를 순서대로 포함하는 배열을 반환한다.  

~~~
func filter(_ isIncluded: (Self.Element) throws -> Bool) rethrows -> [Self.Element]
~~~

- isIncluded: 시퀀스의 요소를 인수로 취하고 요소가 반환된 배열에 포함되어야 하는지 여부를 나타내는 부울 값을 반환하는 클로저
- return: 통과한 결과의 배열

## 예시코드
- 이름의 String이 5글자 미만인 이름들   

~~~
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let shortNames = cast.filter { $0.count < 5 }
print(shortNames)
// Prints "["Kim", "Karl"]"
~~~

# Reference
https://developer.apple.com/documentation/swift/sequence/filter(_:)  