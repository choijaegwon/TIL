# Generic
- 타입에 의존하지 않는 벙용 코드를 작성할 때 사용

## 장점
---

- 코드의 중복을 피할수 있다.
- 코드를 유연하게 작성할 수 있다.  

## 예시 코드
---
만약 Int타입의 숫자 2개의 값을 교환해야해서 함수를 작성하였다.  

~~~
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}
~~~
근데 요구사항이 추가되어, 숫자 2개가 아닌 문자 2개도 교환해야한다면?  

~~~
func swapTwoStrings(_ a: inout String, _ b: inout String) {
    let temporaryA = a
    a = b
    b = temporaryA
}
~~~
같은 교환이니까, Int형을 받는 대신, String형을 받게 작성해주었다.  
하지만 이번엔 Double형을 요구한다면?  

~~~
func swapTwoDoubles(_ a: inout Double, _ b: inout Double) {
    let temporaryA = a
    a = b
    b = temporaryA
}
~~~
작성을 해보니, 함수의 로직은 같고 매개변수의 타입만 다르다.  
이때 사용하면 좋은 것이 Generic이다.  

~~~
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let temporaryA = a
    a = b
    b = temporaryA
}
~~~
여기서 T는 이름 변경이 가능하고, 제약을 걸어 줄 수도있다.   

~~~
class Bird { }
class Human { }
class Teacher: Human { }
 
func printName<T: Human>(_ a: T) { }
~~~
printName함수는 Human이라는 class를 상속받아야만 사용이 가능하다.  
따라서,  

~~~
let bird = Bird.init()
let human = Human.init()
let teacher = Teacher.init()
 
printName(bird)  // error
printName(human)
printName(teacher)
~~~
이런 식으로 사용을 못하고 에러가 뜬다.  



# Reference
https://docs.swift.org/swift-book/documentation/the-swift-programming-language/generics/    
https://babbab2.tistory.com/136  
