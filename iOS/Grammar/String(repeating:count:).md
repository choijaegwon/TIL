# String(repeating:count:)
- 지정된 횟수만큼 반복하여 나타낸다.

~~~
init(
    repeating repeatedValue: String,
    count: Int
)
~~~
- repeating: 반복해줄 문자열
- count: 반복할 횟수

## 예시코드

~~~
let s = String(repeating: "ab", count: 10)
print(s)
// Prints "abababababababababab"
~~~


# Reference
https://developer.apple.com/documentation/swift/string/init(repeating:count:)-23xjt  