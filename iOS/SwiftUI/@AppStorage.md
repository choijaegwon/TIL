# @AppStorage
- UserDefault의 SwfitUI버전
- App의 전역범위에 데이터 공유 가능
- Binding으로 서브뷰로 전달하여 데이터를 바로 업데이트 가능

## 코드

### 저장하기
~~~
@AppStorage("KEY") var Name: Type = Value
~~~

### 사용하기
~~~
struct ContentView: View {
    @AppStorage("onboarding") var isOnboarindViewActive: Bool = true
    var body: some View {
        ZStack {
            if isOnboarindViewActive {
                OnboardingView()
            }
            else {
                HomeView()
            }
        }
    }
}
~~~

# Reference
https://velog.io/@kipsong/Today-I-learned-SwiftUI-AppStorage   