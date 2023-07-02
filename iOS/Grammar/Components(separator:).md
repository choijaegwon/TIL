# Components(separator:)
- 기준점을 잡고 그 기준 중심으로 나눈다.

~~~
func components(separatedBy separator: String) -> [String]
~~~

- separator: 구분할 문자열
- return: 나눈 문자열 배열

## 예시코드
- 기준을 정해서 문자열을 분할할 때 사용  
- " "를 기준으로 String을 나누기

~~~
var my_string: String = "i love you"
var strArr = my_string.components(separatedBy: " ")
// Prints "["i", "love", "you"]"
~~~

# Reference
https://developer.apple.com/documentation/foundation/nsstring/1413214-components   