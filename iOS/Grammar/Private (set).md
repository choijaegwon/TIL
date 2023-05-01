# Private (set)
- 내부에서만 값이 변경되도록 하기위한 문법  

## 예시코드
--- 
~~~
struct MyProfile {
    private (set) var name: String = "Jae Gwon"
    var phone: String = "010-1111-2222"
}
~~~ 

외부에서 접근시

~~~
var myProfile = MyProfile()
print(myProfile.name) // Jae Gwon
myProfile.name = "Choi Jae Gwon" // error 발생
myProfile.phone = "010-3333-4444"
~~~