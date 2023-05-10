# Stride<T>(from:to:by)
- 지정된 횟수만큼 단계별로 시작 값에서 종료값 까지(종료값은 포함되지않는다.) 시퀀스를 반환한다.

~~~
func stride<T>(
    from start: T,
    to end: T,
    by stride: T.Stride
) -> StrideTo<T> where T : Strideable
~~~
- start: 시퀀스에 사용할 시작 값
- end: 시퀀스에 제한하는 결과값
- stride: 반복할 때마다 건너뛸 값
- return: start부터 end까지 stride뛴 값(마지막 불포함)

## 예시코드
- 마지막 값은 포함되지 않는다.  

~~~
for radians in stride(from: 0.0, to: .pi * 2, by: .pi / 2) {
    let degrees = Int(radians * 180 / .pi)
    print("Degrees: \(degrees), radians: \(radians)")
}
// Degrees: 0, radians: 0.0
// Degrees: 90, radians: 1.5707963267949
// Degrees: 180, radians: 3.14159265358979
// Degrees: 270, radians: 4.71238898038469
~~~

- 높은 시작 값에서 낮은 값으로 갈 수도 있다.  

~~~
for countdown in stride(from: 3, to: 0, by: -1) {
    print("\(countdown)...")
}
// 3...
// 2...
// 1...
~~~

# stride(from:through:by:)
- 지정된 횟수만큼 단계별로 시작 값에서 종료값 까지(종료값이 포함된다.) 시퀀스를 반환한다.  

~~~
func stride<T>(
    from start: T,
    through end: T,
    by stride: T.Stride
) -> StrideThrough<T> where T : Strideable
~~~
- start: 시퀀스에 사용할 시작 값
- end: 시퀀스에 제한하는 결과값
- stride: 반복할 때마다 건너뛸 값
- return: start부터 end까지 stride뛴 값(마지막 포함)

## 예시코드 
- 마지막 값도 포함된다.  

~~~
for radians in stride(from: 0.0, through: .pi * 2, by: .pi / 2) {
    let degrees = Int(radians * 180 / .pi)
    print("Degrees: \(degrees), radians: \(radians)")
}
// Degrees: 0, radians: 0.0
// Degrees: 90, radians: 1.5707963267949
// Degrees: 180, radians: 3.14159265358979
// Degrees: 270, radians: 4.71238898038469
// Degrees: 360, radians: 6.28318530717959
~~~  
  
- 높은 시작 값에서 낮은 값으로 갈 수도 있다.  

~~~
for countdown in stride(from: 3, through: 1, by: -1) {
    print("\(countdown)...")
}
// 3...
// 2...
// 1...
~~~

- 마지막에 포함되지 않으면 맨 마지막 값을 반환해준다.  

~~~
for multipleOfThree in stride(from: 3, through: 10, by: 3) {
    print(multipleOfThree)
}
// 3
// 6
// 9
~~~  

# Reference
https://developer.apple.com/documentation/swift/stride(from:to:by:)   
https://developer.apple.com/documentation/swift/stride(from:through:by:)  