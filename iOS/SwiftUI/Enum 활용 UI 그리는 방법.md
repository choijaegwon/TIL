# Enum 활용 UI 그리는 방법

~~~
enum ButtonType {
    case primary
    case secondary
    case destructive
}

struct CustomButton: View {
    var buttonType: ButtonType

    var body: some View {
        switch buttonType {
        case .primary:
            return AnyView(Button("Primary Button").foregroundColor(.white).padding().background(Color.blue).cornerRadius(5))
        case .secondary:
            return AnyView(Button("Secondary Button").foregroundColor(.blue).padding().background(Color.white).cornerRadius(5).overlay(RoundedRectangle(cornerRadius: 5).stroke(Color.blue, lineWidth: 2)))
        case .destructive:
            return AnyView(Button("Destructive Button").foregroundColor(.white).padding().background(Color.red).cornerRadius(5))
        }
    }
}

~~~

이제 위에서 만든 `CustomButton`을 다음과 같이 사용할 수 있다.

~~~
struct ContentView: View {
    var body: some View {
        VStack {
            CustomButton(buttonType: .primary)
            CustomButton(buttonType: .secondary)
            CustomButton(buttonType: .destructive)
        }
    }
}

~~~

그러면 primary, secondary, destructive 타입의 버튼이 나타난다.  
이와 같이 Enum을 사용하면 UI를 그리는 것이 더 직관적이고 유연해진다.  
