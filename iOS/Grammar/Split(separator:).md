# Split(separator:)
- 기준점을 잡고 그 기준 중심으로 나눈다.

~~~
func split(
    separator: Self.Element,
    maxSplits: Int = Int.max,
    omittingEmptySubsequences: Bool = true
) -> [Self.SubSequence]
~~~

- separator: 분할해야 할 요소
- maxSplits: 컬렉션을 분할할 최대 횟수
- omittingEmptySubsequences: 공백 부분 반환 여부
- return: 시퀀스의 배열 ex) [String.subequence]

## 예시코드
- 공백에서 문자열을 분할할 때 사용  

~~~
let line = "BLANCHE:   I don't want realism. I want magic!"
print(line.split(separator: " "))
// Prints "["BLANCHE:", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
~~~

- 매개변수 1에 대해 전달 되므로 두개의 문자열로 한번만 분할  

~~~
print(line.split(separator: " ", maxSplits: 1))
// Prints "["BLANCHE:", "  I don\'t want realism. I want magic!"]"
~~~

- 매개변수 false 전달 공백이 반복되는 빈문자열이 포함됨

~~~
print(line.split(separator: " ", omittingEmptySubsequences: false))
// Prints "["BLANCHE:", "", "", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
~~~


# Reference
https://developer.apple.com/documentation/swift/string/split(separator:maxsplits:omittingemptysubsequences:)  