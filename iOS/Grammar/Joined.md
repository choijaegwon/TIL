# Joined
- 배열에 들어있는 여러 원소들을 하나로 묶을때 사용하는 메소드

~~~
func joined() -> FlattenSequence<Self>
~~~
- FlattenSequence<Self>: 배열의 원소들을 하나로 나열한 값

## 예시코드

~~~
let ranges = [0..<3, 8..<10, 15..<17]

// A for-in loop over 'ranges' accesses each range:
for range in ranges {
  print(range)
}
// Prints "0..<3"
// Prints "8..<10"
// Prints "15..<17"

// Use 'joined()' to access each element of each range:
for index in ranges.joined() {
    print(index, terminator: " ")
}
// Prints: "0 1 2 8 9 15 16"
~~~

# Joined(separator:)
- 배열에 들어있는 여러 원소들을 하나로 묶을때 사이에 지정된 문자열을 삽입 가능  

~~~
func joined(separator: String = "") -> String
~~~
- separator: 사이사이에 삽입할 문자열
- String: 연결된 단일 문자열

## 예시코드

~~~
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let list = cast.joined(separator: ", ")
print(list)
// Prints "Vivien, Marlon, Kim, Karl"
~~~


# Reference 
https://developer.apple.com/documentation/swift/array/joined()   
https://developer.apple.com/documentation/swift/array/joined(separator:)-5do1g