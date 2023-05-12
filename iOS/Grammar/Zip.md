# Zip
- 내부에서만 값이 변경되도록 하기위한 문법  
- 만약, 두개의 길이가 같지 않으면 짧은쪽에 맞춰서 결과 값이 나온다.

~~~
func zip<Sequence1, Sequence2>(
    _ sequence1: Sequence1,
    _ sequence2: Sequence2
) -> Zip2Sequence<Sequence1, Sequence2> where Sequence1 : Sequence, Sequence2 : Sequence
~~~
- sequence1: 압축할 첫 번째 시퀸스
- sequence2: 압축할 두 번째 시퀸스
- Zip2Sequence: 각 쌍의 요소를 튜플로 나타내 준다.

## 예시코드

~~~
let words = ["one", "two", "three", "four"]
let numbers = 1...4

for (word, number) in zip(words, numbers) {
    print("\(word): \(number)")
}
// Prints "one: 1"
// Prints "two: 2"
// Prints "three: 3"
// Prints "four: 4"
~~~

# Reference 
https://developer.apple.com/documentation/swift/zip(_:_:)  
