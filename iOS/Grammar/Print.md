# Print
- 출력해주는 함수

~~~
func print(
    _ items: Any...,
    separator: String = " ",
    terminator: String = "\n"
)
~~~
- item: 출력해주고싶은 것
- separator: 각 항목 사이에 넣어줄 문자열(기본값: " ")
- terminator: 출력 후 표시주는 문자열(기본값: 줄바꿈)

## item
---

- 출력해주고싶은 것
~~~
print(1...5)
~~~
출력
~~~
"1...5"
~~~

## separator
---

- 각 항목 사이에 넣어줄 문자열(기본값: " ")
~~~
print(1, 2, 3, 4, 5, separator: "...")
~~~
출력
~~~
1...2...3...4...5
~~~

## terminator
---

- 출력 후 표시주는 문자열(기본값: 줄바꿈)
~~~
for i in 1...5 {
    print(i, terminator: "")
}
~~~
출력
~~~
"12345"
~~~


# Reference
https://developer.apple.com/documentation/swift/print(_:separator:terminator:)