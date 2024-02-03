# defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.

## defer가 호출되는 경우

~~~
swift
func test() {
    defer {
        print("3")
    }
 
    print("2")
}
 
print("1")
test()
// 출력결과
1
2
3
~~~
1,2,3 호출

## defer가 호출되지 않는 경우

~~~
swift
var a = "Hello"

func b() -> String {
	defer { a.append(" World") }
	retrun a
}

a = "Hello"
print(b())

// 출력결과
Hello

~~~
출력한 후 a에다가 World를 더해줌 따라서 출력 결과는 Hello