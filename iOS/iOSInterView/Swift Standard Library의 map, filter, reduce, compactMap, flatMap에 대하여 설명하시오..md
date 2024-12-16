# Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.

## Map 함수
- 기존 배열 등의 각 아이템을 새롭게 매핑해서 새로운 배열을 리턴하는 함수
- 각 아이템을 매핑해서, 새로운 배열을 만들때 주로 사용한다.

~~~
let numbers = [1, 2, 3, 4, 5]

// 이렇게 클로져로 사용할 수있다(여기서는 numbers의 타입이 Int여서 클로져에서 Int로 나온다)
numbers.map(transform: (Int) throws -> T)

// int값을 받아서 이렇게 String 값으로 바꿀수 있다.
numbers.map { num in
	return "숫자: \(num)"
} 

// 클로져형태라서 이렇게 줄여서 사용할 수도 있다. 위 코드랑 같은 코드다.
// nubmers.map { "숫자: \($0)" }

print(numbers)
["숫자: 1", "숫자: 2", "숫자: 3", "숫자: 4", "숫자: 5"]
~~~

## filter 함수

- 기존 배열 등의 각 아이템을 조건을 확인한 후, Bool값으로 판단한후, 새로운 배열을 리턴해주는 함수

~~~
let names = ["Apple", "Black", "Circle", "Dream", "Blue"]

// 이렇게 클로져로 사용할 수있다(여기서는 names의 타입이 String여서 클로져에서 String으로 나온다)
names.filter(isIncluded: (String) throws -> Bool)

// names 배열에서 "B"가 포함되어 있으면(true면) return해준다.
var aaa = names.filter { str in
	return str.contains("B")
}

// 출력
print(aaa)
["Black", "Blue"]

//여기서 contains는 값이 포함되어 있는지, 이미 String에 구현되어있는 기능이다. 결과값으로 true or false를 return 해준다.
// ex) "Black".contains("B") // true가 return된다.
~~~

## reduce 함수

- 기존 배열 등의 각 아이템을 클로져가 제공하는 방식으로 결합해서 마지막 결과값을 리턴해준다.
- 누적적으로 계속 반복하기 때문에 초기값이 필요하다.

~~~
var numbersArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

numbersArray.reduce(initialResult: Result, nextPartialResult: (Result, Int) throws -> Result)

// 여기서 초기값은 0이다. (0 + 1)더한값이 그다음 초기값으로 사용된다.(1 + 2)...반복한다.
var aaa = numbersArray.reduce(0) { a, b in
	return a + b
}

//클로져 형태라서 압축할수 있다.
var aaa = numbersArray.reduce(0) { $0 + $1 } //위에랑 같은 코드이다.

//출력
print(aaa)
55
~~~

## compactMap 함수
- 기존 배열 등의 각 아이템을 새롭게 매핑해서 변형하되, 옵셔널 요소는 제거하고, 새로운 배열을 리턴해준다.
- 옵셔널 바인딩의 기능까지 내장되어 있다.

~~~
let stringArray: [String?] = ["A", nil, "B", nil, "C"]

var newStringArray = stringArray.compactMap { $0 }

//출력
print(newStringArray)
["A", "B", "C"] // 여기서 newStringArray의 타입을 보면 [String]타입으로 바뀌어있다.
~~~

## flatMap 함수
- 중첩된 배열의 각 배열을 새롭게 매핑해서 내부 중첩된 배열을 제거하고 리턴해준다.